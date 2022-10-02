<template>
  <main>
    <div v-if="list.movies.length > 0">
      <h2 class="text_center">My film</h2>
      <br />
      <div class="grid_col_7">
        <div class="pad_x_2" v-for="movie in list.movies" :key="movie.id">
          <p>Title: {{ movie.title }}</p>
          <p>Original title:{{ movie.original_title }}</p>
          <p>Language:{{ movie.original_language }}</p>
          <p>Vote:{{ parseInt(movie.vote_average / 2) }}</p>
        </div>
      </div>
    </div>
    <div v-if="list.tvSeries.length > 0">
      <h2 class="text_center">My series tv</h2>
      <br />
      <div class="grid_col_7">
        <div class="pad_x_2" v-for="serie in list.tvSeries" :key="serie.id">
          <p>Name {{ serie.name }}</p>
          <p>Original name {{ serie.original_name }}</p>
          <p>Language:{{ serie.original_language }}</p>
          <p>Vote:{{ parseInt(serie.vote_average / 2) }}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "MainComp",
  props: {
    list: Object,
  },
};
</script>

<style lang="scss" scoped></style>
