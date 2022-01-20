<template>
  <div class="container mx-auto my-5 ">
    <h1 class="text-center text-4xl font-black mb-5">My Pokedex</h1>
    <img src="../assets/pokedex.webp" alt="pokedex" class="block mx-auto" width="250">
    <div class="flex flex-wrap items-center justify-center mb-16 mt-8">
      <input 
        type="search"
        name="search"
        v-model="search"
        placeholder="Buscar Pokemon por nome"
        class="rounded-md outline-none px-5 py-3 mr-4 max-w-xl">
      <button class="bg-gray-800 px-5 py-3 rounded-md text-gray-200">Buscar</button>
    </div>

    <Types/>

    <div v-show="!loading" class="grid lg:grid-cols-4 md:grid-cols-3 sm:grid-cols-2 gap-4 px-4">
      <div v-for="(pokemon, index) in filteredPokemons" :key="index" >
        <Pokemon 
          :name="pokemon.name"
          :front="pokemon.front"
          :back="pokemon.back"
          :type="pokemon.type"
          :url="pokemon.url"
          :num="index+1"
          />
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Pokemon from '../components/Pokemon';
import Types from '../components/Types';

export default {
  name: 'Home',
  data() {
    return {
      loading: false,
      search: '',
      pokemons: []
    };
  },
  created: async function() {
    this.pokemons.length === 0 ? this.getPokemons() : '';
  },
  components: {
    Pokemon,
    Types
  },
  computed: {
    filteredPokemons: function() {
      let search = this.search.toLowerCase().trim();
      if(!search) return this.pokemons;
      else{
        let filteredList = this.pokemons.filter(poke => poke.name.toLowerCase().indexOf(search) !== -1);
        return filteredList;
      }
    }
  },
  methods: {
    getPokemons: async function() {
      this.loading = true;
      this.baseUrl = 'https://pokeapi.co/api/v2';
      try {
        let { data } = await axios.get(`${this.baseUrl}/pokemon?limit=151&offset=0`);
        this.pokemons = data.results;
        this.getData();
      } catch (error) {
        console.log(error);
      }
    },
    getData: async function() {
      this.pokemons.forEach( pokemon => {
        axios.get(pokemon.url)
        .then( response => {
          pokemon.type = response.data.types[0].type.name;
          pokemon.front = response.data.sprites.front_default;
          pokemon.back = response.data.sprites.back_default;
        })
        .catch(err => console.log(err));
      });
      this.loading = false;
    }
  }
}
</script>

<style>
  *{
    font-family: 'Inter', sans-serif;
  }
</style>
