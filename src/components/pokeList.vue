<template>
  <div class="list">
    <article
      
      class="teste"
      v-for="(pokemon, index) in pokemons"
      :key="'poke' + index"
      @click="setPokemonUrl(pokemon.url)"
    >
      <img
        :src="imageUrl + pokemon.id + '.png'"
        width="96"
        height="96"
        alt=""
      />

      <h3>{{ pokemon.name }}</h3>
      <p>Nº {{ pokemon.id }}</p>
     

    </article>

    <div  id="scroll-trigger" ref="infinitescrolltrigger">
      <i class="fas fa-spinner fa-spin"></i>
    </div>

  <!--   <a href="" v-on:click="loadpoke" id="loadMore">
            <span class="button-lightblue">Carregar mais Pokémon</span>
    </a>
-->
  </div>
  
</template>

<script>
export default {
  props: ["imageUrl", "apiUrl"],
  data: () => {
    return {
      pokemons: [],
      nextUrl: "",
      currentUrl: "",
      menuActive: false,
    };
  },
  methods: {
    fetchData() {
      let req = new Request(this.currentUrl);
      fetch(req)
        .then((resp) => {
          if (resp.status === 200) return resp.json();
        })
        .then((data) => {
          this.nextUrl = data.next;
          data.results.forEach((pokemon) => {
            pokemon.id = pokemon.url
              .split("/")
              .filter(function (part) {
                return !!part;
              })
              .pop();
            this.pokemons.push(pokemon);
          });
        })
        .catch((error) => {
          console.log(error);
        });
    },


    scrollTrigger() {
      const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry) => {
          if (entry.intersectionRatio > 0 && this.nextUrl) {
            this.next();
          }
        });
      });
      observer.observe(this.$refs.infinitescrolltrigger);
    },
    next() {
      this.currentUrl = this.nextUrl;
      this.fetchData();
    },
    setPokemonUrl(url) {
      this.$emit("setPokemonUrl", url);
    },
  },
  created() {
    this.currentUrl = this.apiUrl;
    this.fetchData();
  },
  mounted() {
    this.scrollTrigger();
  },

  loadpoke: function(){
    this.menuActive = true;
  },

  closepoke: function(){
    this.menuActive = false;
  }
};


</script>

<style   scoped>
.list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 5fr));
  grid-gap: 10px;
  width: 100%;
  max-width: 100vh;
  border: border-box;
  background-color: #efefef;
  text-align: center;
  text-transform: capitalize;
  border-radius: 10px;
  cursor: pointer;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2), 0 10px 10px rgba(0, 0, 0, 0.2);
}

h3 {
  margin: 0;
  font-size: 16px;
}

p {
  font-size: 11px;
  margin-bottom: 10px;
  border-radius: 20px;
  padding: 0.1rem 2rem;
  color: #fff;
  background-color: #265300;
  margin: 10px;
}

.teste {
    background-color: #d1d1d1;
    border-radius: 1rem;
    margin: 0.5rem;
}

#loadMore {
  background-color: brown;
  border-radius: 10rem;
  color: #efefef;
  align-items: center;
  width: 100%;
  display: flex;
  justify-content: center;
}

</style>

