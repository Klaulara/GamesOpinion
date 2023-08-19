<template>
  <div class="home">
    <h1 class="container text-start mt-5">Lista de juegos disponibles</h1>
    <div class="container d-flex flex-wrap">
      <div class="m-2 p-2" v-for="game in games" :key="game.name">
        <CardComponent
          :title="game.name"
          :image="game.background_image"
          :rating="game.rating"
          :released="game.released"
          :update="game.updated"
        />
      </div>
    </div>
  </div>
</template>

<script>
import CardComponent from "@/components/CardComponent.vue";

const API_KEY = "b686700b4f174c728ffe389c52195dc6";

export default {
  name: "HomeView",
  components: {
    CardComponent,
  },
  data() {
    return {
      games: [],
    };
  },
  methods: {
    async getGames() {
      await fetch(`https://api.rawg.io/api/games?key=${API_KEY}`)
        .then((response) => response.json())
        .then((data) => (this.games = data.results))
    },
  },
  mounted() {
    this.getGames();
  },
};
</script>
