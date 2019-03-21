<template>
  <div class="container">
    <Navbar/>
    <!--    <Container/>-->
    <MapChart/>
    <Footer/>
  </div>
</template>

<script>
  import Navbar from './Navbar.vue'
//  import Container from './Container.vue'
  import Footer from './Footer.vue'
  import MapChart from './MapChart'
  
  export default {
    name: 'app',
    components: {
      Navbar,
//      Container,
      Footer,
      MapChart
    }
  }

</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

<style lang="scss" scoped>
  @import "../assets/scss/custom.scss"
</style>
