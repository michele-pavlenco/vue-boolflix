<template>
  <div class="container">
    <header class="debug">
      <div class="title">
        <h1><a href="./">Boolflix</a> </h1>
      </div>
      <div class="serch-bar">
         <input type="text" class="search-click" name="" placeholder="Cerca qui..."  @keyup.enter="$emit('performSearch',search)" v-model="search" />
        <button @click="cerca" >Cerca</button>

      </div>
    </header>
  </div>
</template>

<script>
//import state from "../store.js"
export default {
  name: "HeaderComponent",
  data() {
    return {
      search: ""

    };
  },
  // computed:{
  //   
  // },
  methods: {
    cerca(){
      this.$emit('performSearch',this.search)
      this.search = ''
    }
   
  },
};
</script>
<style>
 header {
  height: 80px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
button{
  border-radius: 20px;
  padding: 5px;
  background-color: black;
  color: red;
  border: 1px solid red;
  cursor: pointer;
  }
.title a {
  color: red;
  text-transform: uppercase;
  text-decoration: none;
}
.serch-bar input,
button {
  height: 30px;
} 
.search-click {
  border: 1px solid rgb(255, 0, 0);
  margin-right: 10px;
  background-size: 22px;
  background-position: 13px;
  border-radius: 50px;
  width: 50px;
  height: 50px;
  padding: 25px;
  transition: all 0.5s;
}
.search-click:focus {
  width: 200px;
  padding-left: 25px;
   background-image: url(../assets/img/lens.svg); 
  background-position: left;
    border: none ;
}
.search-click {
  position: relative;
  overflow: hidden;
  height: 50px;
    border: 3px solid rgb(255, 0, 0);
}
.search-click input {
  background: transparent;
  outline: none;
  position: absolute;
  width: 200px;
  height: 50px;
  left: 2%;
  padding: 10px;
}
.search-click{
 background-image: url(../assets/img/lens.svg); 
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
}
</style>
