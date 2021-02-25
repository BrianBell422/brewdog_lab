<template lang="html">
    <div>
        <h2>Favourite Beers</h2>
        <ul>
            <li v-for="favouriteBeer in favouriteBeers">{{favouriteBeer.name}} <button v-on:click="removeFromFavourites(favouriteBeer)">Remove from favourites</button> </li>
        </ul>
    </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
    name: 'favourite-beers',
    props: ['favouriteBeers'],
    methods: {
        removeFromFavourites: function(favouriteBeer){
            eventBus.$emit('remove-favourite-beer', favouriteBeer)
        },
    }
}
</script>

<style>

</style>