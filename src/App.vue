<template>
  <div id="app" class="container" v-if="isLoaded">
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.7.1/css/all.css" 
          integrity="sha384-fnmOCqbTlWIlj8LyTjo7mOUStjsKC4pOpQbqyi7RrhN7udi9RwhKkMHpvLbHG9Sr" 
          crossorigin="anonymous">

    <InfoMessage v-if="showInfoMessage"></InfoMessage>

    <div class="navigation-bar">
      <Breadcrumbs></Breadcrumbs>
    </div>

    <div class="main-content">
      <div class="col-first">
        <Controls></Controls>
        <ImagePreview :images="product.images"></ImagePreview>
        <ProductsList :title="'Często kupowane z tym produktem'"
                      :itemsPerSlide="4">
        </ProductsList>
      </div>

      <div class="col-second">
        <ProductInfo :product="product"></ProductInfo>
        <AddToCart :product="product"></AddToCart>
        <TrackProduct></TrackProduct>
        <ProductsList :title="'Inni klienci sprawdzali również'"></ProductsList>
        <ProductDetails :title="'opis produktu'" 
                        :isExpanded="true">
        </ProductDetails>
        <ProductDetails :title="'opinie klientów'"></ProductDetails>
        <ProductDetails :title="'wymiary produktu'"></ProductDetails>
        <ProductDetails :title="'materiał i pielęgnacja'"></ProductDetails>
        <ProductDetails :title="'czas i koszt dostawy'"></ProductDetails>
        <ProductDetails :title="'podziel się'"></ProductDetails>
        <ProductsList :title="'Często kupowane z tym produktem'"></ProductsList>
      </div>
    </div>
  </div>
</template>

<script>
// components
import Breadcrumbs from './components/Breadcrumbs'
import Controls from './components/Controls'
import ImagePreview from './components/ImagePreview'
import ProductInfo from './components/ProductInfo'
import AddToCart from './components/AddToCart'
import InfoMessage from './components/InfoMessage'
import TrackProduct from './components/TrackProduct'
import ProductsList from './components/ProductsList'
import ProductDetails from './components/ProductDetails'

import axios from 'axios'
import { EventBus } from './EventBus.js'

export default {
  name: 'app',
  components: {
    Breadcrumbs,
    Controls,
    ImagePreview,
    ProductInfo,
    AddToCart,
    InfoMessage,
    TrackProduct,
    ProductsList,
    ProductDetails
  },
  data: () => {
    return {
      product: {},
      isLoaded: false,
      showInfoMessage: false
    }
  },
  created() {
    axios.get('/json/product.json')
      .then(product => {
        this.product = product.data;
        this.isLoaded = true;
      })
      .catch(error => console.log(error))

    EventBus.$on('info-message', () => {
      this.showInfoMessage = true;
      setTimeout(() => {
        this.showInfoMessage = false;
      }, 4000)
    });
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
  padding: 10px 25px;
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
  .main-content {
    display: flex;
    justify-content: space-between;
  }

  .col-first {
    width: 60%;
  }

  .col-second {
    width: 35%
  }
}

</style>
