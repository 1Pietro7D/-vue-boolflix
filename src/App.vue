<template>
  <div id="app">
    <HeaderComp />
    <MainComp />

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
    return {};
  },
  created() {
    const BaseUrl = "https://api.themoviedb.org/3/";
    const SearchMovie = "search/movie?";
    const Query = "&query=";
    console.log(BaseUrl, SearchMovie);
    axios
      .get(BaseUrl + SearchMovie + apiKey + Query + "Jack+Reacher")
      .then((response) => {
        console.log(response);
      })
      .catch((error) => {
        console.warn(error);
      });
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
