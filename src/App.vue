<template>
  <div id="app">
    <header>
      <nav class="container">
        <a href="/">
          <img
            src="https://upload.wikimedia.org/wikipedia/commons/9/98/International_Pok%C3%A9mon_logo.svg"
            alt="Logo"
            id="logo"
          />
        </a>

        
      </nav>
    </header>
<!--
    <form action="" class="search">
          <input
            type="search"
            class="search-input"
            placeholder=" nome ou número"
          />
          
          <button class="search-button">Pesquisar</button>
      </form>
-->      
    <PokemonMain />

  </div>
</template>

<script>
import "./styles/style.css";
import PokemonMain from "./components/PokemonMain.vue";

export default {
  name: "App",
  components: {
    PokemonMain,
  },
};

// API endpoint
// const baseUrl = 'https://pokeapi.co/api/v2/pokemon/';
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@100;200&display=swap");

header,
a {
  background-color: brown;
  height: 60px;
  display: flex;
  justify-content: center;
}

#logo {
  width: 130px;
}

.search {
  display: flex;
  margin: 1rem;
  padding: 1rem;
  
  justify-content: center;
  
  
}

.search-input {
  border: none;
  outline: none;
  appearance: none;
  border-radius: 0.15rem;
}

</style>
