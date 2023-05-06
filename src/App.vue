<template>
  <div class="container">
    <!-- NAVBAR -->
    <navbar-component-vue></navbar-component-vue>

    <!-- NAVIGATION -->
    <navigation-component-vue></navigation-component-vue>

    <router-view/>

    <!-- FOOTER -->
    <footer-component-vue></footer-component-vue>
  </div>

</template>

<script>
  import NavbarComponentVue from './components/NavbarComponent.vue'
  import NavigationComponentVue from './components/NavigationComponent.vue'
  import FooterComponentVue from './components/FooterComponent.vue'

  export default {
    name: 'App',

    components: {
      NavbarComponentVue,
      NavigationComponentVue,
      FooterComponentVue
    }


  }


</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  nav {
    padding: 30px;
  }

  nav a {
    font-weight: bold;
    color: #2c3e50;
  }

  nav a.router-link-exact-active {
    color: #42b983;
  }
</style>
