<template>
  <div id="app">
    <IpInput />
    <!-- <IpMap /> -->
    <!-- <Test /> -->
  </div>
</template>

<script>
import IpInput from './components/IpInput.vue'
// import IpMap from './components/IpMap.vue'
// import Test from './components/Test.vue'


export default {
  name: 'App',
  components: {
    IpInput,
    // IpMap
    // Test
  }
}
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rubik:wght@400;500;700&display=swap");
#app {
  font-family: 'Rubik', sans-serif;
}
</style>
