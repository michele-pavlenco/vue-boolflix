<template>
  <div id="app">
    <HeaderComponent />
    <MainComponent />
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import axios from "axios";

export default {
  name: "App",
  props:{

  },
  components: {
    HeaderComponent,
    MainComponent,
  },
  data() {
    return {
      filmCards: {},
      myApi: 'https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=ritorno+al+futuro'
    };
  },
  mounted() {
    axios
      .get(this.myApi)
      .then((res) => { 
        console.log("ogg", res);
        this.filmCards = res.data.results;
      }) .catch((error) => {
        console.log(error);
      });

      console.log("film",this.filmCards)
  },
  created(){


  }
};
</script>

<style>
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
