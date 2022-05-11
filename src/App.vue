<template>
  <div id="app">
    <HeaderComponent @performSearch="search" />
    <MainComponent :items="films" :loader=loading />
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import axios from "axios";

export default {
  name: "App",
  // props:{},
  components: {
    HeaderComponent,
    MainComponent,
  },
  data() {
    return {
      films: [],
      apiKey: "e99307154c6dfb0b4750f6603256716d",
      myApi: "https://api.themoviedb.org/3/search/",
      ///movie?api_key=e99307154c6dfb0b4750f6603256716d&query=ritorno+al+futuro
      loading: false,
    };
  },
  methods: {
    getMovies(queryParams) {
      axios
        .get(this.myApi + "movie",queryParams)
        .then((res) => {
          console.log("ogg", res.data.results);
          this.films = res.data.results;
          this.loading= false
        })
        .catch((error) => {
          console.log(error);
        });
    },

    search(text) {
      console.log(text);
      const queryParams = {
        params: {
          api_key: this.apiKey,
          query: text,
        },
      };
this.loading= true
      this.getMovies(queryParams);
    },
  },
  mounted() {},
  created() {},
};
</script>

<style lang="scss">
@import "./style/general.scss";
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.debug {
  border: 1px solid black;
}
.container {
  width: 90%;
  margin: 0 auto;
}
</style>
