<template>
  <div class="container">

    <PokeSearch 
      :apiUrl="apiUrl" 
      @setPokemonUrl="setPokemonUrl" />
    
    <PokemonList 
      :imageUrl="imageUrl" 
      :apiUrl="apiUrl"
      @setPokemonUrl="setPokemonUrl" />

    <PokemonDetail 
      v-if="showDetail"
      :pokemonUrl="pokemonUrl"
      :imageUrl="imageUrl"
      @closeDetail="closeDetail" />
  </div>
</template>

<script>
import PokeSearch from "./PokeSearch"
import PokemonList from "./pokeList";
import PokemonDetail from "./pokeDatail";

export default {
  data: () => {
    return {
      imageUrl:
        "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/",
      apiUrl: "https://pokeapi.co/api/v2/pokemon/",
      pokemonUrl: "",
      showDetail: false,
    };
  },
  components: {
    PokemonList,
    PokemonDetail,
    PokeSearch,
  },
  methods: {
    setPokemonUrl(url) {
      this.pokemonUrl = url;
      this.showDetail = true;
    },
    closeDetail() {
      this.pokemonUrl = "";
      this.showDetail = false;
    },
  },
};
</script>

<style scoped>

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 10px;
  min-height: calc(100vh - 20px);
  background: radial-gradient(#156f99, #0a2e50);
  font-family: "Acme", arial;
  font-size: 1rem;
  font-weight: normal;
}
h1 {
  color: #efefef;
}
</style>