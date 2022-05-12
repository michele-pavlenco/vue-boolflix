<template>
  <div class="container">
    <main class="debug">
      <h2>{{ title }}</h2>

      <ul>
        <li class="debug" v-for="item in items" :key="item.id">
          <div class="card-img">
            <!-- <img :src="'https://image.tmdb.org/t/p/w185/' + item.poster_path" alt=""/> -->
            <img :src="item.poster_path ? 'https://image.tmdb.org/t/p/w185/' + item.poster_path : require('../assets/img/netflix.png')" alt="">
            <br />
          </div>

          <div class="card-text">
            <!-- <span> <p>id:</p>  {{ item.id }} <br /></span> -->
<div v-if="item.original_title !== item.title" >
            <span>
              <p>Titolo originale:</p>
              {{item.original_title ? item.original_title : item.original_name}} 
             <p>Titolo:</p> <div> {{ item.title ? item.title : item.name }}</div>
              <br
            /></span>

          
</div>
<div v-else>
  <span
              > <p>Titolo:</p> <div> {{ item.title ? item.title : item.name }}</div> <br
            /></span>
</div>
            <span>
              <p >Lingua:</p> 
              <div class="flag" v-if="item.original_language === 'en'">
                {{ item.original_language }}
                <img :src="require('../assets/img/en.jpg')" alt="" />
              </div>
              <div class="flag" v-else-if="item.original_language === 'it'">
                {{ item.original_language }}
                <img :src="require('../assets/img/ita.jpg')" alt="" />
              </div>
              <div class="flag" v-else>{{ item.original_language }}</div>
              <br />
            </span>
            <span>
             <p>Trama:</p> <div> {{item.overview}}</div>
            </span>
           
              <div> 
            <!-- <span> voto: {{ item.vote_average }} </span> -->
            <span v-for="(n,index) in 5"  :key="index">
              <i :class="n <= reduceVotes(item) ? 'fa-solid fa-star yellow-star' : 'fa-solid fa-star empty-star' " ></i>
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
    
  },
  methods: {
    reduceVotes(item){
     
       return Math.ceil(item.vote_average / 2)
   }
  },
};
</script>

<style scoped lang="scss">
main {
  width: 100%;
  background-color: rgba(19, 19, 19, 0.924);
  color: white;
  margin-bottom: 22px;
  // height: calc(50vh - 80px);
}
ul {
  display: flex;
  overflow-x: auto;
  overflow-y: hidden;
  height: 310px;

}
ul li {
  list-style-type: none;
  position: relative;
  color: white;
  transition: 1s ease-in-out;
  transform-style: preserve-3d;
  border-radius: 30px;
  padding: 20px;

}
.flag{
  text-transform:uppercase;
}
.card-img {
  background-size: contain;
  backface-visibility: hidden;
  transition: 1s ease-in-out;
  -webkit-box-reflect: below 0
    linear-gradient(transparent, transparent, rgba(0, 0, 0, 0.4));
}
.card-img img {
  height: 200px;
  width: 140px;
  background-size: cover;

  border-radius: 10px;
}
.card-text {
  position: absolute;
  top: 0px;
  color: white;
  visibility: hidden;
  height: 100%;
  width: 100%;
  padding: 20px;
  overflow-y:scroll ;

}
::-webkit-scrollbar {
  width: 5px;
  height: 5px;
}
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px grey; 
  border-radius: 10px;
}
::-webkit-scrollbar-thumb {
  background: red; 
  border-radius: 10px;
}
::-webkit-scrollbar-thumb:hover {
  background: #b30000; 
}

li:hover {
  transform: rotateY(0.5turn);
}
span{
  margin-top: 5px;
  width: 100%;
}
span p{
  color: rgba(255, 0, 0, 0.534);
}
span div {
font-size: 14px;
}

li:hover .card-text {
transform: rotateY(0.5turn);
  transition-delay: 0.5s;
  visibility: visible;
}
.yellow-star {
  color:yellow;
}
.empty-star {color: rgba(255, 0, 0, 0.212);}
ul .flag img {
  width: 13px;
  height: 10px;
}
</style>
