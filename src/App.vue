<script>
import AppHeader from "./components/AppHeader.vue";
export default{
  components: {
    AppHeader
  },
  
}
</script>

<template>
  <AppHeader/>
  <RouterView></RouterView>
</template>

<style lang="scss">
@use './style/main.scss';

body{
  background-color: rgb(42, 42, 42);
  height: 100vh;
  background-image: var(--gradient2);
  background-size: 1000%;
  animation: bg-animation 8s infinite alternate;
}
@keyframes bg-animation{
    0% {background-position: left;}
    100% {background-position: right;}
}

</style>
