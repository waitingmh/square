<template>
  <div id="app">
      <router-view/>
  </div>
</template>

<script>
import Square from '@/components/Square'
export default {
  name: 'App',
  components:{
    Square
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
