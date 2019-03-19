<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <TestFetchAPI msg="test auto déploiement avec vue js et netifly + branche dev"/>
  </div>
</template>

<!-- <script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
</script> -->

<script>
    import TestFetchAPI from './components/TestFetchAPI.vue'
    export default {
        name: 'app',
        components: {
            TestFetchAPI
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
