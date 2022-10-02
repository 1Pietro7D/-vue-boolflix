<template>
  <main>
    <div v-if="list.movies.length > 0">
      <h1>My film</h1>
    </div>
    <div v-if="list.tvSeries.length > 0">
      <h1>My series tv</h1>
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
