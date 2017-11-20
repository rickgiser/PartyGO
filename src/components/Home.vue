<template>
  <div id="home">
    <div class="amap-page-container" id="home_map">
      <el-amap ref="map" vid="amapDemo" :amap-manager="amapManager" :center="center" :zoom="zoom" :plugin="plugin" :events="events" class="amap-demo">
      </el-amap>
    </div>
    <div class="search">
      <mt-search cancel-text="" placeholder="搜地点、查公交、找路线" class="search_input"></mt-search>
      <mt-button size="large" type="default" class="search_button">搜索</mt-button>
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
        width:270px;
      }
      .search_button{
        font-size:15px;
        position: absolute;
        width: 76px;
        border-top:8px #d9d9d9 solid;
        border-right:8px #d9d9d9 solid;
        border-bottom:8px #d9d9d9 solid;
        border-left:2px #d9d9d9 solid;
        float: left;
        left:250px;
        z-index:1000;
        height:52px;
        background-color: white;
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
            alert('map clicked');
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
