<template>
  <div class="card_container">
    <div class="card">
      <img :src="baseUrlImg + 342 + image" alt="" @error="errImg($event)" />
    </div>
    <div class="card_back">
      <p>Title: {{ title }}</p>
      <p v-if="title !== originalTitle">Original title:{{ originalTitle }}</p>
      <p>Language:<FlagComp :language="language" /></p>
      <p>Vote:<StarVoteComp :vote="vote" /></p>
      <p>Description: {{ overview }}</p>
    </div>
  </div>
</template>

<script>
import FlagComp from "./FlagComp.vue";
import StarVoteComp from "./StarVoteComp.vue";
export default {
  name: "CardComp",
  props: {
    title: String,
    originalTitle: String,
    language: String,
    vote: Number,
    overview: String,
    image: String,
  },
  data() {
    return {
      baseUrlImg: "https://image.tmdb.org/t/p/w",
    };
  },
  components: { FlagComp, StarVoteComp },
  methods: {
    errImg(event) {
      event.target.src =
        "https://www.metrorollerdoors.com.au/wp-content/uploads/2018/02/unavailable-image-300x225.jpg";
    },
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
