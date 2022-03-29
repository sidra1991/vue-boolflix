<template>
  <div>
    <!-- <navBar @search="model"/> -->
    <mainVision  />
  </div>
</template>

<script>

// import navBar from '@/components/navBar.vue';
import mainVision from './components/mainVision.vue'

export default {
  components: {
    mainVision,
    // navBar
  },
  // data (){
  //   return{
  //     prova:'',
  //   }
  // },
  methods: {
  // model (titleFilms){
  //   console.log(titleFilms);
  // }
}
}
</script>

<style>
</style>
