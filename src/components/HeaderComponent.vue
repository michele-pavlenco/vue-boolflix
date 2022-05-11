<template>
  <div class="container">
    <header class="debug">
      <div class="title">
        <h1>Boolflix</h1>
      </div>
      <div class="serch-bar">
        <input @keyup.enter="$emit('performSearch',search)" v-model="search" type="text" />
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
      //state
    };
  },
  // computed:{
  //    mySearch(){
  //   return state.serch
  // },
  methods: {
    cerca(){
      this.$emit('performSerch',this.search)
      this.search = ''
    }
    // leggi(){
    //   state.serch= 'pippo'
    // }
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
.title {
  color: red;
  text-transform: uppercase;
}
.serch-bar input,
button {
  height: 30px;
} 
</style>
