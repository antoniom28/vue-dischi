<template>
  <div id="app">
    <Header />
    <Main />
    <Footer />
  </div>
</template>

<script>
import Main from './components/macro/Main.vue'
import Footer from './components/macro/Footer.vue'
import Header from './components/macro/Header.vue'

export default {
  name: 'App',
  components: {
    Main,
    Footer,
    Header,
  }
}
</script>

<style lang="scss">
@import './assets/style/globals.scss';

#app {
 height: 100vh;
 background-color: $bg_color;
}
</style>
