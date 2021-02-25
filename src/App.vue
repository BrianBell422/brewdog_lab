<template>
  <div id="app">
    <h1>Beers</h1>
    <div class="main-container">
      <beer-list :beers="beers"></beer-list>
      <beer-detail :beer="selectedBeer"></beer-detail>
    </div>
    <button v-if="!favouriteBeers.includes(selectedBeer)" v-on:click="addToFavourites" >Add beer to favourites</button>
  </div>
</template>

<script>
import BeerList from './components/BeerList.vue'
import BeerDetail from './components/BeerDetail.vue'
import FavouriteBeers from './components/FavouriteBeers.vue'

import { eventBus } from './main.js';

export default {
  name: 'App',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    };
  },
  components: {
    "beer-list": BeerList,
    "beer-detail": BeerDetail,
    "favourite-beers": FavouriteBeers
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer
    })
  },
  methods: {
    addToFavourites: function(){
      this.favouriteBeers.push(this.selectedBeer)
    },
  }
}
</script>

<style>
#app {
  
}
</style>
