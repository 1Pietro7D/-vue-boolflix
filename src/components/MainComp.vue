<template>
  <main>
    <div v-if="list.movies.length > 0">
      <h2 class="text_center">My film</h2>
      <br />
      <div class="grid_col_7">
        <div
          class="card_container"
          v-for="movie in list.movies"
          :key="movie.id"
        >
          <div class="card">
            <p>Title: {{ movie.title }}</p>
            <p v-if="movie.title !== movie.original_title">
              Original title:{{ movie.original_title }}
            </p>
            <p>Language:<FlagComp :language="movie.original_language" /></p>
            <p>Vote:{{ parseInt(movie.vote_average / 2) }}</p>
            <p>Description: {{ movie.overview }}</p>
          </div>
        </div>
      </div>
    </div>
    <div v-if="list.tvSeries.length > 0">
      <h2 class="text_center">My series tv</h2>
      <br />
      <div class="grid_col_7">
        <div
          class="card_container"
          v-for="serie in list.tvSeries"
          :key="serie.id"
        >
          <div class="card">
            <p>Name {{ serie.name }}</p>
            <p v-if="serie.title !== serie.original_title">
              Original name {{ serie.original_name }}
            </p>
            <p>Language:<FlagComp :language="serie.original_language" /></p>
            <p>Vote:{{ parseInt(serie.vote_average / 2) }}</p>
            <p>Description: {{ serie.overview }}</p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import FlagComp from "./FlagComp.vue";
export default {
  name: "MainComp",
  components: { FlagComp },
  props: {
    list: Object,
  },
};
</script>

<style lang="scss" scoped>
.card_container {
  height: 400px;
  padding: 1rem;
  margin-bottom: 1.5rem;
  .card {
    overflow-y: auto;
    background-color: aqua;
    height: 100%;
  }
}
</style>
