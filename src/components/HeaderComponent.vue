<template>
  <div class="container">
    <header class="debug">
      <div class="title">
        <h1>Boolflix</h1>
      </div>
      <div class="serch-bar">
        <input type="text" />
        <button>Cerca</button>
      </div>
    </header>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",
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
.serch-bar input, button{
    height: 30px;

}
</style>
