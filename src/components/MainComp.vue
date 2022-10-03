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
            <img
              :src="baseUrlImg + 342 + movie.poster_path"
              alt=""
              @error="errImg($event)"
            />
          </div>
          <div class="card_back">
            <p>Title: {{ movie.title }}</p>
            <p v-if="movie.title !== movie.original_title">
              Original title:{{ movie.original_title }}
            </p>
            <p>Language:<FlagComp :language="movie.original_language" /></p>
            <p>
              Vote:<StarVoteComp :vote="parseInt(movie.vote_average / 2)" />
            </p>
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
            <img
              :src="baseUrlImg + 342 + serie.poster_path"
              alt=""
              @error="errImg($event)"
            />
          </div>
          <div class="card_back">
            <p>Name {{ serie.name }}</p>
            <p v-if="serie.title !== serie.original_title">
              Original name {{ serie.original_name }}
            </p>
            <p>Language:<FlagComp :language="serie.original_language" /></p>
            <p>
              Vote: <StarVoteComp :vote="parseInt(serie.vote_average / 2)" />
            </p>
            <p>Description: {{ serie.overview }}</p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import FlagComp from "./FlagComp.vue";
import StarVoteComp from "./StarVoteComp.vue";
export default {
  name: "MainComp",
  components: { FlagComp, StarVoteComp },
  props: {
    list: Object,
  },
  data() {
    return {
      baseUrlImg: "https://image.tmdb.org/t/p/w",
    };
  },
  methods: {
    errImg(event) {
      event.target.src =
        "https://r.search.yahoo.com/_ylt=AwrEssafMjpjuy0M5YkdDQx.;_ylu=c2VjA3NyBHNsawNpbWcEb2lkAzc1NmQwYWJjMTM5ZDQ4MDcwYTJiYmI0ZmZjNmYwOWViBGdwb3MDNTMEaXQDYmluZw--/RV=2/RE=1664787231/RO=11/RU=https%3a%2f%2fseotomize.com%2f21-best-404-error-page-examples-must-know-best-practices%2f/RK=2/RS=Y5P_eEycW817vOrNaftkCZ4P6aI";
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
