<template>
  <div class="container">
    <main class="debug">
       <ul>
        <li v-for="item in items" :key="item.id">
          id: {{ item.id }} titolo originale:
          {{ item.original_title }} titolo: {{ item.title }} lingua:
          {{ item.original_language }} voto: {{ item.vote_averge }}
        </li>
      </ul>
    </main>
  </div>
</template>

<script>
export default {
  name: "MainComponent",
  props:['items', 'loader'],
data(){
  return{}
},
computed:{
  // mySearch(){
  //   return state.serch
  // }


},
methods:{}
};
</script>

<style scoped lang="scss">
main {
  height: calc(100vh - 80px);
}
</style>
