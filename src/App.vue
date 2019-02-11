<template>
  <div id="app">
    <div class="navigation-bar">
      <Breadcrumbs></Breadcrumbs>
    </div>
  </div>
</template>

<script>
import Breadcrumbs from './components/Breadcrumbs'

export default {
  name: 'app',
  components: {
    Breadcrumbs
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
