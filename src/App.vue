<template>
  <div id="app">
    <radioDemo></radioDemo>
  </div>
</template>

<script>
import radioDemo from "@/components/radioDemo";

export default {
  name: 'app',
  components: {
    radioDemo
  }
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
}
</style>
