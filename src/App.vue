<template>
  <div id="app">
    <Template />
  </div>
</template>

<script>
  import Template from './components/Template.vue'

  export default {
    name: 'app',
    components: {
      Template
    }
  }

</script>

<style>
  * {
    font-family: century-gothic, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    overflow: hidden;
  }
</style>
