<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <audio src="" id="eventAudio"></audio>
    <router-view/>
  </div>
</template>

<script>
export default {
  name:'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
html,body{
            height: 100%;
        }
</style>
