<template>
  <v-list-tile>
    <v-list-tile-avatar >
      <img v-if="pokemon" :src="pokemon.sprites.front_default" :alt="pokemon.name">
    </v-list-tile-avatar>
    <v-list-tile-content>
      <v-list-tile-title><strong>Species: </strong> <span v-text="pokemon ? pokemon.name : name"></span></v-list-tile-title>
      <v-list-tile-sub-title><strong>Type: </strong> <span v-if="pokemon" v-text="types"></span></v-list-tile-sub-title>
    </v-list-tile-content>
  </v-list-tile>
</template>
<script>
export default {
  name: "pokemon",
  props: ['url', 'name'],
  data () {
    return {
      pokemon: null
    }
  },
  async mounted() {
    this.pokemon = await this.getPokemon()
  },
  computed: {
    types() {
      const pokeTypes = this.pokemon.types.map(pt => pt.type.name)
      return pokeTypes.join(' / ')
    }
  },
  methods: {
    async getPokemon() {
      const resp = await this.$http.get(this.url);
      return resp.data;
    }
  }
};
</script>
