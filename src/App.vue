<template>
  <div id="app">
    <h1>Beers</h1>
    <div class="main-container">
      <beer-list :beers="beers"></beer-list>
      <beer-detail :beer="selectedBeer" :favouriteBeers="favouriteBeers"></beer-detail>
      <favourite-beers :favouriteBeers="favouriteBeers"></favourite-beers>
    </div>
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
    eventBus.$on('favourite-beer', (beer) => {
    this.favouriteBeers.push(beer)
    })
    eventBus.$on('remove-favourite-beer', (favouriteBeer) => {
      const index = this.favouriteBeers.findIndex((beer) => {
        return beer === favouriteBeer
      })
      this.favouriteBeers.splice(index, 1)
    })
  },
}

</script>

<style>
#app {
  
}
</style>