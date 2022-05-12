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
              <div> voto:
            <!-- <span> voto: {{ item.vote_average }} </span> -->
            <span v-for="(n,index) in 5" :key="index">
              <i :class="n <= reduceVotes ? 'fa-solid fa-star empty-star  ' : 'fa-solid fa-star yellow-star '"></i>
                </span>
            </div>
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
    reduceVotes(){
       return parseInt(this.items.vote_average / 2)
    }
  },
  methods: {},
};
</script>

<style scoped lang="scss">
main {
  width: 100%;
  // height: calc(50vh - 80px);
}
ul {
  display: flex;
  overflow-x: auto;
  overflow-y: hidden;
  height: 280px;
}
ul li {
  list-style-type: none;
  position: relative;

  color: white;
  cursor: pointer;
  transition: 1s ease-in-out;
  transform-style: preserve-3d;
}
.card-img {
  background-size: contain;

  backface-visibility: hidden;
  transition: 1s ease-in-out;
  -webkit-box-reflect: below 0
    linear-gradient(transparent, transparent, rgba(0, 0, 0, 0.4));
}
.card-img img {
  height: 100%;
  background-size: contain;
}
.card-text {
  position: absolute;
  top: 0px;
  color: black;
  visibility: hidden;
  height: 100%;
  width: 100%;
}
.card-text span {
  margin-top: 50px;
}
li:hover {
  transform: rotateY(0.5turn);
}
li:hover .card-text {
transform: rotateY(0.5turn);
  transition-delay: 0.5s;
  visibility: visible;
}
.yellow-star {
  color:yellow;
}
.empty-star {color: red;}
ul .flag img {
  width: 13px;
  height: 10px;
}
</style>
