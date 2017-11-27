<template>
  <div id="home">
    <div class="amap-page-container" id="home_map">
      <el-amap ref="map" vid="amapDemo" :amap-manager="amapManager" :center="center" :zoom="zoom" :plugin="plugin" :events="events" class="amap-demo">
      </el-amap>
    </div>
    <div class="search">
      <input type="text" placeholder="搜地点、查公交、找路线" class="search_input"></input>
      <img src="../assets/defavatar.png" alt="" class="search_img">
      <span class="search_button"><i class="fa fa-search fa-lg" aria-hidden="true"></i></span>
      <div id="js-result" class="search_result"></div>
    </div>
  </div>
</template>

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
        height:35px;
        border:0px;
        padding-left: 38px;
        border-radius: 5px;
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
        top: 7px;
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
        top: 4px;
        left: 4px;
      }
      .search_result{
        max-height: 300px; 
        overflow: auto; 
        margin-top: 10px;
      }
    }
  }
</style>


<script>
  import AMap from 'vue-amap';
  let amapManager = new AMap.AMapManager();
  export default{
    data: function() {
      return {
        amapManager,
        zoom: 12,
        center: [121.59996, 31.197646],
        events: {
          init: (o) => {
            console.log(o.getCenter())
            console.log(this.$refs.map.$$getInstance())
            o.getCity(result => {
              console.log(result)
            })
          },
          'moveend': () => {
          },
          'zoomchange': () => {
          },
          'click': (e) => {
            // alert('map clicked');
          }
        },
        plugin: ['ToolBar', {
          pName: 'MapType',
          defaultType: 0,
          events: {
            init(o) {
              console.log(o);
            }
          }
        }]
      };
    },

    methods: {
      getMap() {
        // amap vue component
        console.log(amapManager._componentMap);
        // gaode map instance
        console.log(amapManager._map);
      }
    }
  }
</script>
