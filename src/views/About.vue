<template>
  <div class="about">
    <h1>This is an about page {{id}}</h1>
    <h2>{{pokemon}}</h2>
  </div>
</template>
<script>
import axios from 'axios';

export default {
  created() {
    console.log(this.$route.params.id);
    console.log('about created');
    this.id = this.$route.params.id;
    this.searchPokemon();
  },
  data() {
    return {
      id: 0,
      loading: false,
      pokemon: {},
    };
  },
  methods: {
    buscaPokemon() {
      this.$router.push({
        name: 'pokemon',
        params: {
          id: this.id
        }
      });
    },
    searchPokemon: async function(){
      this.loading = true;
      this.baseUrl = 'https://pokeapi.co/api/v2';
      try {
        let { data } = await axios.get(`${this.baseUrl}/pokemon/${this.id}`);
        this.pokemon = data;
      } catch (error) {
        console.log(error);
      }
    },
  }
}
</script>
