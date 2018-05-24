<template>
  <div class="home">
    <img src="../assets/logo.png">
    <h1>{{ msg }}</h1>
    <input type="text" name="message" v-model="msg"/>
    <h2>My Pokémon:</h2>
    <v-list two-line>
      <v-list-tile v-for="monster in monsters">
        <v-list-tile-avatar>
          <img :src="monster.avatar">
        </v-list-tile-avatar>
        <v-list-tile-content>
          <v-list-tile-title><strong>Name:</strong> {{ monster.name }}</v-list-tile-title>
          <v-list-tile-sub-title><strong>Species:</strong> {{ monster.species }} <strong>Type:</strong> {{ monster.type }}</v-list-tile-sub-title>
        </v-list-tile-content>
      </v-list-tile>
    </v-list>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  data () {
    return {
      msg: "Testing v-model",
      monsters: [
        {
          name:"Cougher", 
          species:"Koffing",
          avatar:"https://cdn.bulbagarden.net/upload/1/17/109Koffing.png",
          type: "Gas/Poison"
        },
        {
          name:"Zapper", 
          species:"Jolteon", 
          avatar:"https://cdn.bulbagarden.net/upload/b/bb/135Jolteon.png",
          type: "Electric"
        },
        {
          name:"Scratcher", 
          species:"Mankey", 
          avatar:"https://cdn.bulbagarden.net/upload/4/41/056Mankey.png",
          type: "Fighting"
        }
      ]
    }
  },
  components: {
    HelloWorld
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
