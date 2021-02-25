<template lang="html">
    <div v-if="beer" id="beerDetail">
        <h3>{{beer.name}}</h3>
        <div>
            <p><span>Description</span>: {{beer.description}}</p>
            <p><span>ABV</span>: {{beer.abv}}</p>
            <p><span>Volume</span>: {{beer.volume.value}} {{beer.volume.unit}}</p>
        </div>
        <div>
            <img id="beer-img" :src="beer.image_url" :alt="beer.name">
        </div>
        <button v-if="!favouriteBeers.includes(beer)" v-on:click="addToFavourites" >Add beer to favourites</button>
    </div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
    name: 'beer-detail',
    props: ['beer', 'favouriteBeers'],
    methods: {
    addToFavourites: function(){
        eventBus.$emit('favourite-beer', this.beer)
    },
  }
}
</script>

<style>
#beer-img {
    width: 100px;
}
</style>