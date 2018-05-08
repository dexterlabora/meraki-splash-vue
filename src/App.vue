<template>
  <div id="app" class="bg">
    <img src="./assets/transparent_legos-192px.png">
    <router-view/>
    <footer class="page-footer font-small blue-grey lighten-5 pt-0 footer">
        <a href="https://meraki.io">Meraki.io</a>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  margin-bottom: 10px;
  height: 100%;
}
.bg { 
    /* The image used */
    background-image: url("./assets/beach.jpg");

    /* Full height */
    height: 100%; 

    /* Center and scale the image nicely */
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}         
.footer {
    position: fixed;
    left: 0;
    bottom: 10px;
    width: 100%;
    background-color: white;
    color: white;
    text-align: center;
}
</style>
