<template>
  <div id="app" class="container" v-if="isLoaded">
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.7.1/css/all.css" 
          integrity="sha384-fnmOCqbTlWIlj8LyTjo7mOUStjsKC4pOpQbqyi7RrhN7udi9RwhKkMHpvLbHG9Sr" 
          crossorigin="anonymous">

    <div class="navigation-bar">
      <Breadcrumbs></Breadcrumbs>
    </div>

    <div class="col-first">
      <Controls></Controls>
      <ImagePreview :images="product.images"></ImagePreview>
    </div>

    <div class="col-second">

    </div>
  </div>
</template>

<script>
// components
import Breadcrumbs from './components/Breadcrumbs'
import Controls from './components/Controls'
import ImagePreview from './components/ImagePreview'

import axios from 'axios'

export default {
  name: 'app',
  components: {
    Breadcrumbs,
    Controls,
    ImagePreview
  },
  data: () => {
    return {
      product: {},
      isLoaded: false
    }
  },
  created() {
    axios.get('/json/product.json')
      .then(product => {
        this.product = product.data;
        this.isLoaded = true;
      })
      .catch(error => console.log(error))
  }
}
</script>

<style>

*, *:before, *:after {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  text-decoration: none;
}

.container {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  width: 100%;
  max-width: 1170px;
  margin: 0 auto;
  padding: 10px 15px;
  height: 100%;
}

.navigation-bar {
  width: 100%;
}

.col-first,
.col-second {
  width: 100%;
}

@media screen and (min-width: 768px) {
  .col-first {
    width: 60%;
  }

  .col-second {
    width: 40%
  }
}

</style>
