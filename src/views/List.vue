<template>
  <div class="master-list">
    <h1>Master List</h1>
    <v-list v-if="pokemons">
      <pokemon v-for="pokemon in pokemons" 
        :key="pokemon.name"
        :url="pokemon.url">
      </pokemon>
    </v-list>
  </div>
</template>

<script>
// @ is an alias to /src
import pokemon from '@/components/Pokemon.vue'
export default {
  name: 'list',
  data () {
    return {
      pokemons: []
    }
  },
  components: {
    pokemon
  },
  async mounted() {
    this.pokemons = await this.getPokemons()
  },
  methods: {
    async getPokemons() {
      const resp = await this.$http.get('https://pokeapi.co/api/v2/pokemon')
      return resp.data.results
    }
  }
};
</script>