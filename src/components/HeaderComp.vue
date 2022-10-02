<template>
  <header>
    <input type="text" v-model="query" /><input
      type="button"
      value="Search"
      @click="toSend"
    />
  </header>
</template>

<script>
export default {
  name: "HeaderComp",
  data() {
    return { query: "" };
  },
  methods: {
    toSend() {
      this.$emit("inputSearch", this.query);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/style/variables.scss";
</style>
