<template>
  <div id="app">
    <HeaderComp @inputSearch="Search" />
    <MainComp :list="list" />
    <FooterComp />
  </div>
</template>

<script>
import axios from "axios";
import { apiKey } from "@/env.js";
import HeaderComp from "@/components/HeaderComp.vue";
import MainComp from "@/components/MainComp.vue";
import FooterComp from "@/components/FooterComp.vue";

export default {
  name: "App",
  components: {
    HeaderComp,
    MainComp,
    FooterComp,
  },
  data() {
    return { list: { movies: [], tvSeries: [] } };
  },
  methods: {
    Search(input) {
      if (input.length > 0) {
        this.QueryApi(input.replace(" ", "+"));
      }
    },
    QueryApi(textToSearch) {
      const BaseUrl = "https://api.themoviedb.org/3/";
      // Request
      const SearchMovie = "search/movie?";
      const SearchTv = "search/tv?";

      // Language
      const LanguageIT = "&language=it-IT";

      console.log(BaseUrl, SearchMovie, SearchTv);

      axios
        .get(
          BaseUrl + SearchMovie + apiKey + "&query=" + textToSearch + LanguageIT
        )
        .then((response) => {
          if (response.status === 200) {
            this.list.movies = response.data.results;
          }
        })
        .catch((error) => {
          console.warn(error);
        });
      axios
        .get(
          BaseUrl + SearchTv + apiKey + "&query=" + textToSearch + LanguageIT
        )
        .then((response) => {
          if (response.status === 200) {
            this.list.tvSeries = response.data.results;
          }
        })
        .catch((error) => {
          console.warn(error);
        });
    },
  },
};
</script>

<style lang="scss">
@import "@/assets/style/import.scss";
</style>

<!--

@import "@/assets/style/generics.scss";
@import "@/assets/style/position.scss"; 
@import "@/assets/style/flex.scss";
@import "@/assets/style/grid.scss"; 

@import "@/assets/style/variables.scss";  !! this must be inserted into each component !!
-->
