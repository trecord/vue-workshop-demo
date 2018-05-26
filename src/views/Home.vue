<template>
  <div class="home">
    <img src="../assets/logo.png">
    <h1>{{ msg }}</h1>
    <input type="text" name="message" v-model="msg"/>
    <h2>My Pokémon:</h2>
    <v-list two-line>
      <v-list-tile v-for="(monster, index) in monsters" :key="index">
        <v-list-tile-avatar>
          <img :src="monster.avatar">
        </v-list-tile-avatar>
        <v-list-tile-content>
          <v-list-tile-title><strong>Name:</strong> {{ monster.name }}</v-list-tile-title>
          <v-list-tile-sub-title><strong>Species:</strong> {{ monster.species }} <strong>Type:</strong> {{ monster.type }}</v-list-tile-sub-title>
        </v-list-tile-content>
        <v-btn @click.stop="removePokemon(index)">Remove Pokémon</v-btn>
      </v-list-tile>
    </v-list>
    <div>
      <h3>Add a Charmander:</h3>
      <form>
        <v-text-field
          v-model="newName"
          label="New Charmander Name"
        ></v-text-field>
          <v-btn v-if="newName" @click.stop="addPokemon()">Add Pokémon</v-btn>
      </form>
    </div>
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
      newName: "",
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
  methods: {
    removePokemon: function (index) {
      this.monsters.splice(index, 1);
    },
    addPokemon: function () {
      let newPokemon = {
          name:this.newName, 
          species:"Charmander", 
          avatar:"https://cdn.bulbagarden.net/upload/thumb/7/73/004Charmander.png/500px-004Charmander.png",
          type: "Fire"
        };
      this.monsters.push(newPokemon);
      this.newName = "";
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
