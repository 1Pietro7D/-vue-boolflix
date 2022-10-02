<template>
  <main>
    <div v-if="list.movies.length > 0">
      <h2>My film</h2>
      <div class="grid_col_10">
        <div v-for="movie in list.movies" :key="movie.id">
          <p>{{ movie.original_title }}</p>
        </div>
      </div>
    </div>
    <div v-if="list.tvSeries.length > 0">
      <h2>My series tv</h2>
      <div class="grid_col_10">
        <div v-for="serie in list.tvSeries" :key="serie.id">
          <p>{{ serie.name }}</p>
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

<style lang="scss" scoped>
@import "@/assets/style/grid.scss";
</style>
