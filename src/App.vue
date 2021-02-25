<template>
  <div id="app">
    <h1>Beers</h1>
    <div class="main-container">


    </div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return {
      beers: [],
      selectedBeer: null
    };
  },
  components: {
    
  },
  mounted(){
    fetch('https://api.punkapi.com/v2/beers')
    .then(res => res.json())
    .then(beers => this.beers = beers)
  }
}
</script>

<style>
#app {
  
}
</style>
