<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" width="25%" />
    <HelloWorld msg="Google Pay Vue Demo App" />
    <GooglePay />
  </div>
</template>

<script setup>
import HelloWorld from './components/HelloWorld.vue'
import GooglePay from './components/GooglePay.vue'
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
