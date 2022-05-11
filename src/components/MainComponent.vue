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
            <span> id: {{ item.id }} <br /></span>

            <span>
              titolo originale:
              {{
                item.original_title ? item.original_title : item.original_name
              }}
              <br
            /></span>

            <span
              >titolo: {{ item.title ? item.title : item.name }} <br
            /></span>

            <span>
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
            </span>

            <span> voto: {{ item.vote_average }} </span>
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
  },
  methods: {},
};
</script>

<style scoped lang="scss">
main {
  width: 100%;
  //   height: calc(50vh - 80px);
}
ul {
  display: flex;
  overflow-x: auto;
}
ul li {
  list-style-type: none;
  width: 300px;
  height: 284px;
  position: relative;
}
.card-img {
  background-size: contain;
}
.card-text {
  position: absolute;
  top: 0px;
  color: white;
  visibility: hidden;
  background-color: black;
  height: 100%;
  width: 100%;
  transition: opacity 0.2s, visibility 0.2s;
}
.card-text span {
  margin-top: 50px;
}
li:hover .card-text {
  visibility: visible;
}

ul .flag img {
  width: 13px;
  height: 10px;
}
</style>
