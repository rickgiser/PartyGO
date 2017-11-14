<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style lang="less">
  html{
    overflow: scroll;
  }
  html, body {
    margin: 0px;
    padding: 0px;
    background: rgb(245, 245, 245);
  }

  #app {
    position: absolute;
    top: 0px;
    bottom: 0px;
    width: 100%;
  }
</style>
