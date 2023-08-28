<script>
import HelloWorld from './components/HelloWorld.vue'
import TheHeader from './components/TheHeader.vue'
import TheFooter from './components/TheFooter.vue'
import FilterThe from './components/FilterThe.vue'



export default {
  components : {
    TheFooter,
    TheHeader,
    FilterThe
  }
};
</script>

<template>

  <TheFooter></TheFooter>
  <FilterThe></FilterThe>
  <TheHeader></TheHeader>



  <HelloWorld msg="Vite + Vue" />
</template>

<style  lang="scss" scoped>


</style>
