<template>
  <main>
    <div v-if="list.movies.length > 0">
      <h2 class="text_center">My film</h2>
      <div class="grid_col_7">
        <CardComp
          v-for="movie in list.movies"
          :key="movie.id"
          :title="movie.title"
          :originalTitle="movie.original_title"
          :language="movie.original_language"
          :vote="Math.floor(movie.vote_average / 2)"
          :overview="movie.overview"
          :image="movie.poster_path"
        />
      </div>
    </div>
    <div v-if="list.tvSeries.length > 0">
      <h2 class="text_center">My series tv</h2>
      <div class="grid_col_7">
        <CardComp
          v-for="tv in list.tvSeries"
          :key="tv.id"
          :title="tv.name"
          :originalTitle="tv.original_title"
          :language="tv.original_language"
          :vote="Math.floor(tv.vote_average / 2)"
          :overview="tv.overview"
          :image="tv.poster_path"
        />
      </div>
    </div>
  </main>
</template>

<script>
import CardComp from "./CardComp.vue";
export default {
  name: "MainComp",
  components: { CardComp },
  props: {
    list: Object,
  },
  data() {
    return {
      baseUrlImg: "https://image.tmdb.org/t/p/w",
    };
  },
};
</script>

<style lang="scss" scoped>
.card_container {
  height: 400px;
  padding: 1rem;
  margin-bottom: 1.5rem;
  position: relative;
  .card {
    width: 100%;
    height: 100%;
    img {
      max-width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
  .card_back {
    overflow-y: auto;
    background-color: black;
    height: 100%;
    width: 100%;
    color: white;
    display: none;
  }
}

.card_container:hover > .card {
  display: none;
}

.card_container:hover > .card_back {
  display: inline-block;
}
</style>
