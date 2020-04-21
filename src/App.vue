<template>
  <div id="app">
    <ChangePage />
  </div>
</template>

<script>
import ChangePage from './components/ChangePage.vue'

export default {
  name: 'App',
  components: {
    ChangePage
  }
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin: 0;
    padding: 0;
  }
  .button-add {
    flex: 2;
    background-color: #2DCC70;
    color: white;
    font-size: 12px;
    border-radius: 5px;
    height: 40px;
    border: 2px solid #2DCC70;
    margin-right: 20px;
  }
</style>
