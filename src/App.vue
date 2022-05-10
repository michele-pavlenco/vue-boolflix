<template>
  <div id="app">
    <HeaderComponent />
    <MainComponent />
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import axios from axios;

export default {
  name: "App",
  components: {
    HeaderComponent,
    MainComponent,
  },
};
axios.get("")then((res)=>{
  
})
</script>

<style >
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.debug{
  border: 1px solid black;
}
.container{
  width: 90%;
  margin: 0 auto;
}
</style>
