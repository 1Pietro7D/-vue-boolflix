<template>
  <main>
    <div v-if="list.movies.length > 0">
      <h2 class="text_center">My film</h2>
      <br />
      <div class="grid_col_7">
        <div class="pad_2" v-for="movie in list.movies" :key="movie.id">
          <p>Title: {{ movie.title }}</p>
          <p v-if="movie.title !== movie.original_title">
            Original title:{{ movie.original_title }}
          </p>
          <p>Language:<FlagComp :language="movie.original_language" /></p>
          <p>Vote:{{ parseInt(movie.vote_average / 2) }}</p>
        </div>
      </div>
    </div>
    <div v-if="list.tvSeries.length > 0">
      <h2 class="text_center">My series tv</h2>
      <br />
      <div class="grid_col_7">
        <div class="pad_2" v-for="serie in list.tvSeries" :key="serie.id">
          <p>Name {{ serie.name }}</p>
          <p v-if="serie.title !== serie.original_title">
            Original name {{ serie.original_name }}
          </p>
          <p>Language:<FlagComp :language="serie.original_language" /></p>
          <p>Vote:{{ parseInt(serie.vote_average / 2) }}</p>
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

<style lang="scss" scoped></style>
