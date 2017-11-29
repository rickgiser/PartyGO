<template>
  <div id="home" class="m-map" >
    <div class="search" v-if="placeSearch">
      <input type="text" placeholder="搜地点、查公交、找路线" class="search_input" v-model="searchKey"></input>
      <a ><router-link to="./login"><img class="search_img" src="../assets/defavatar.png" alt=""></router-link></a>
      <span class="search_button" @click="handleSearch"><i class="fa fa-search fa-lg" aria-hidden="true"></i></span>
      <div id="js-result" class="search_result" v-show="searchKey"></div>
    </div>
    <div id="js-container" class="map"></div>
  </div>
</template>


<script>
import remoteLoad from '@/utils/remoteLoad.js'
import { MapKey, MapCityName } from '@/config/config'
export default {
  props: ['lat', 'lng'],
  data () {
    return {
      searchKey: '',
      placeSearch: null,
      dragStatus: false,
      AMapUI: null,
      AMap: null
    }
  },
  watch: {
    searchKey () {
      if (this.searchKey === '') {
        this.placeSearch.clear()
      }
    }
  },
  methods: {
    // 搜索
    handleSearch () {
      if (this.searchKey) {
        this.placeSearch.search(this.searchKey)    //placeSearch.search  调用查询方法
      }
    },
    // 实例化地图
    initMap () {
      // 加载PositionPicker，loadUI的路径参数为模块名中 'ui/' 之后的部分
      let AMapUI = this.AMapUI = window.AMapUI
      let AMap = this.AMap = window.AMap
      AMapUI.loadUI(['misc/PositionPicker'], PositionPicker => {
        let mapConfig = {
          zoom: 16,
          cityName: MapCityName
        }
        if (this.lat && this.lng) {
          mapConfig.center = [this.lng, this.lat]
        }
        let map = new AMap.Map('js-container', mapConfig)
        // 加载地图搜索插件
        AMap.service('AMap.PlaceSearch', () => {
          this.placeSearch = new AMap.PlaceSearch({
            pageSize: 5,
            pageIndex: 1,
            citylimit: false,
            // city: MapCityName,
            map: map,
            panel: 'js-result'
          })
        })
        // 添加地图控件
        AMap.plugin(['AMap.ToolBar','AMap.Scale','AMap.OverView','AMap.Geolocation','AMap.MapType'],
        function(){
          map.addControl(new AMap.ToolBar());

          map.addControl(new AMap.Scale());

          map.addControl(new AMap.Geolocation());

          map.addControl(new AMap.MapType());

          map.addControl(new AMap.OverView({isOpen:false}));

          document.getElementsByClassName("amap-geolocation-con")[0].style.bottom = "40px";
          document.getElementsByClassName("amap-zoomcontrol")[0].style.bottom = "80px";
          
        });
        // 创建地图拖拽
        let positionPicker = new PositionPicker({
          mode: 'dragMap', // 设定为拖拽地图模式，可选'dragMap'、'dragMarker'，默认为'dragMap'
          map: map // 依赖地图对象
        })
        // 拖拽完成发送自定义 drag 事件
        positionPicker.on('success', positionResult => {
          // 过滤掉初始化地图后的第一次默认拖放
          if (!this.dragStatus) {
            this.dragStatus = true
          } else {
            this.$emit('drag', positionResult)
          }
        })
        // 启动拖放
        positionPicker.start()
      })
    }
  },
  async created () {
    // 已载入高德地图API，则直接初始化地图
    if (window.AMap && window.AMapUI) {
      this.initMap()
    // 未载入高德地图API，则先载入API再初始化
    } else {
      await remoteLoad('http://webapi.amap.com/maps?v=1.3&key=39a902a2bc6a0bb933de87db7d588a4e')
      await remoteLoad('http://webapi.amap.com/ui/1.0/main.js')
      this.initMap()
    }
  }
}
</script>


<style lang="less">
  #home{
    height: 100%;
    width: 100%;
    #home_map{
      height: 100%;
      .amap-maptypecontrol{
        position: absolute;
        top:90px;
        z-index: 999;
      }
    }
    .search{
      position: absolute;
      top: 15px;
      left: 15px;
      z-index:999;
      width:330px;
      .search_input{
        position: absolute;
        width:292px;
        height:40px;
        border:0px;
        padding-left: 38px;
        border-radius: 5px;
        outline: none;
      }
      .search_button{
        color:#ccc;
        font-size: 15px;
        position: absolute;
        width: 24px;
        float: left;
        left: 301px;
        z-index: 1000;
        height: 24px;
        top: 10px;
      }
      .search_button:hover{
        color:blue;
      }
      .search_img{
        position: absolute;
        float: left;
        z-index: 1000;
        width:28px;
        height:28px;
        top: 7px;
        left: 4px;
      }
      .search_result{
        max-height: 300px; 
        overflow: auto; 
        margin-top: 42px;
      }
    }
    .map{
      height:100%;
      .amap-controls{
        .amap-geolocation-con{
          bottom:40px;
        }
        .amap-maptypecontrol{
          top:80px;
        }
      }
    }
  }
</style>
