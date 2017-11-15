<template>
  <div id="home">
    <div class="amap-page-container" id="home_map">
      <el-amap ref="map" vid="amapDemo" :amap-manager="amapManager" :center="center" :zoom="zoom" :plugin="plugin" :events="events" class="amap-demo">
      </el-amap>
    </div>
    <mt-button icon="back" id="back">back</mt-button>
  </div>
</template>

<style lang="less">
  #home{
    height: 100%;
    width: 100%;
    #home_map{
      height: 100%;
    }
    #back{
      position: absolute;
      top:10px;
      left: 10px;
      z-index: 999;
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
