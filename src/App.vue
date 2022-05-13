<template>
  <div id="app">
    <HeaderComponent
      @performSearch="search"
      @hidden-films="hiddenClassFilm"
      @hidden-series="hiddenClassSeries"
    />
    <LoadingComponent v-if="loading" />

    <MainComponent
      :items="films"
      title="Film"
      :loader="loading"
      :class="{ disBlockFilm: isNotActivefilm }"
    />

    <MainComponent
      title="Serie tv"
      :items="series"
      :loader="loadingSeries"
      :class="{ disBlockSeries: isNotActiveseries }"
    />
    <!--  -->
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import LoadingComponent from "./components/LoadingComponent.vue";
import axios from "axios";

export default {
  name: "App",

  components: {
    HeaderComponent,
    MainComponent,
    LoadingComponent,
  },
  data() {
    return {
      films: [],
      series: [],
      apiKey: "e99307154c6dfb0b4750f6603256716d",
      myApi: "https://api.themoviedb.org/3/search/",
      isNotActivefilm: false,
      isNotActiveseries: false,

      ///movie?api_key=e99307154c6dfb0b4750f6603256716d&query=ritorno+al+futuro
      loading: false,
      loadingSeries: false,
    };
  },
  methods: {
    hiddenClassFilm() {
      this.isNotActivefilm = true;
      console.log("active");
      this.isNotActiveseries = false;
    },
    hiddenClassSeries() {
      this.isNotActiveseries = true;
      (this.isNotActivefilm = false), console.log("active");
    },
    getMovies(queryParams) {
      axios
        .get(this.myApi + "movie", queryParams)
        .then((res) => {
          console.log("ogg", res.data.results);
          this.films = res.data.results;
          this.loading = false;
        })
        .catch((error) => {
          console.log(error);
        });
    },
    getSeries(queryParams) {
      axios
        .get(this.myApi + "tv", queryParams)
        .then((res) => {
          //console.log("ogg", res.data.results);
          this.series = res.data.results;
          this.loadingSeries = false;
        })
        .catch((error) => {
          console.log(error);
        });
    },

    search(text) {
      this.loadingSeries = true;
      console.log(text);
      const queryParams = {
        params: {
          api_key: this.apiKey,
          query: text,
        },
      };
      this.loading = true;
      this.loadingSeries = true;
      this.getMovies(queryParams);
      this.getSeries(queryParams);
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
.disBlockSeries {
  display: none;
}
.disBlockFilm {
  display: none;
}
#app {
  background-color: black;
  height: 100vh;
  font-family: Arial, Helvetica, sans-serif;
}

.container {
  width: 90%;
  margin: 0 auto;
}
</style>
