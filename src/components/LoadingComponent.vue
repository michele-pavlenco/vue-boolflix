<template>
  <body>
    <div class="loader">
      <span>N</span>
      <span>E</span>
      <span>T</span>
      <span>F</span>
      <span>L</span>
      <span>I</span>
      <span>X</span>
    </div>
  </body>
</template>

<script>
export default {
    name: "LoadingComponent"
};
</script>

<style scoped>
body {
  background-color: rgb(20, 20, 20);
  padding: 0;
  margin: 0;
  height: calc(100vh - 80px);
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
  position: absolute;
  z-index: 1000;
}

.loader {
  -webkit-perspective: 700px;
  perspective: 700px;
}

.loader > span {
  font-size: 130px;
  font-family: "franklin gothic medium", sans-serif;
  display: inline-block;
  animation: flip 2.6s infinite linear;
  transform-origin: 0 70%;
  transform-style: preserve-3d;
  -webkit-transform-style: preserve-3d;
}

@keyframes flip {
  35% {
    transform: rotateX(360deg);
  }
  100% {
    transform: rotatex(360deg);
  }
}
.loader > span{
    color: red;
}

.loader > span:nth-child(even) {
  color: rgba(2, 0, 0, 0.835);
}


.loader > span:nth-child(2) {
  animation-delay: 0.3s;
}

.loader > span:nth-child(3) {
  animation-delay: 0.6s;
}

.loader > span:nth-child(4) {
  animation-delay: 0.9s;
}

.loader > span:nth-child(5) {
  animation-delay: 1.2s;
}

.loader > span:nth-child(6) {
  animation-delay: 1.5s;
}

.loader > span:nth-child(7) {
  animation-delay: 1.8s;
}
</style>
