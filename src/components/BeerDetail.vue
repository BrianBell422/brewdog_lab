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
    </div>
</template>

<script>
export default {
    name: 'beer-detail',
    props: ['beer']
}
</script>

<style>
#beer-img {
    width: 100px;
}
</style>