<template>
  <span>
    <span v-for="x in vote" :key="x">X</span>
  </span>
</template>

<script>
export default {
  name: "StarVoteComp",
  components: {},
  props: {
    vote: Number,
  },
  data() {
    return {};
  },
  methods: {},
};
</script>

<style lang="scss" scoped></style>
