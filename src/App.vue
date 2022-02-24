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
        
         <a href="https://github.com/Pedro-HM-Franco?tab=repositories" class="github">GitHub</a> 
        </nav>

        

       

    </header>

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

header  {
  background-color: brown;
  height: 70px;
  display: grid;
  justify-content: center;
  margin-bottom: 1rem;
}

#logo {
  width: 150px;
  justify-content: center;
  align-items: center;
  padding: 1rem;
}

.github{
  display: grid;
  color: aliceblue;
  justify-content: center;
  display: grid;
  position: relative;
}

.container {
  display: grid;
}

</style>
