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

</style>
