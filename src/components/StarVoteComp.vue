<template>
  <span>
    <span v-for="(x, index) in vote" :key="index">X</span>
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
