<template>
  <div class="container">
    <main class="debug">
      <h2>{{ title }}</h2>
      <ul>
        <li class="debug" v-for="item in items" :key="item.id">
          <div class="card-img">
            <img
              :src="'https://image.tmdb.org/t/p/w185/' + item.poster_path"
              alt=""
            />
            <br />
          </div>
          <div class="card-text">
            id:
            {{ item.id }} <br />
            titolo originale:
            {{ item.original_title ? item.original_title : item.original_name }}
            <br />
            titolo:
            {{ item.title ? item.title : item.name }} <br />
            lingua:
            <div class="flag" v-if="item.original_language === 'en'">
              {{ item.original_language }}
              <img :src="require('../assets/img/en.jpg')" alt="" />
            </div>
            <div class="flag" v-else-if="item.original_language === 'it'">
              {{ item.original_language }}
              <img :src="require('../assets/img/ita.jpg')" alt="" />
            </div>
            <div v-else>{{ item.original_language }}</div>
            <br />

            voto:
            {{ item.vote_average }}
          </div>
        </li>
      </ul>
    </main>
  </div>
</template>

<script>
export default {
  name: "MainComponent",
  props: ["items", "loader", "title"],
  data() {
    return {};
  },
  computed: {
    // mySearch(){
    //   return state.serch
    // }
  },
  methods: {},
};
</script>

<style scoped lang="scss">
 main {
   width: 100%;
//   height: calc(100vh - 80px);
 }
ul {
  display: flex;
  overflow-x: auto;
}
  ul li {
    list-style-type: none;
    width: 300px;
    height: 300px;
    position: relative;
  
  }
.card-img{
  background-size: contain;
  
}
.card-text{
  position: absolute;
  top: 0px;
  color: wheat;
  visibility: hidden;
  background-color: black;
  height: 100%;
  width: 100%;

}
li:hover .card-text{
  visibility: visible;
  cursor: pointer;

}

ul .flag img {
  width: 13px;
  height: 10px;
}

</style>
