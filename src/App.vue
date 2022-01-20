<template>
  <div id="app">
    <div class="column is-half is-offset-one-quarter">
      <hr>
      <h4 class="is-size-4">Pokedex</h4>
      
       <div v-for="(poke, index) in pokemons" :key="index">
      <Pokemon :name="poke.name" :url="poke.url" :num="index+1"/>
    </div>

    </div>
   
    
  </div>
</template>

<script>
import axios from 'axios';
import Pokemon from "./components/Pokemon"

export default {
  name: 'App',
  data(){
    return {
      pokemons: [],
      filteredPokemons: [],
      busca: ''

    }

  },
  created: function(){
  axios.get("https://pokeapi.co/api/v2/pokemon/?limit=151&offset=0").then(res => {
    console.log("Pegou a lista de pokemon")
    this.pokemons = res.data.results;
    this.filteredPokemons = res.data.results;
   
  })
  }, 
components: {
  Pokemon
}, 
computed: {

}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#buscaBtn {
  margin-top: 2%;
}
</style>
