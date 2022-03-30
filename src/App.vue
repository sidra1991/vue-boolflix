<template>
  <div>
    <!-- <mainVision  /> -->
    <headerOriginal />
    <mainOriginal :arrCardFilm= 'arrCardFilm' />
    <footerOriginal />
  </div>
</template>

<script>
// import mainVision from './components/mainVision.vue'
import headerOriginal from './components/headerOriginal.vue'
import mainOriginal from './components/mainOriginal.vue'
import footerOriginal from './components/footerOriginal.vue'
import axios from 'axios'
export default {
  components: {
    // mainVision,
    headerOriginal,
    mainOriginal,
    footerOriginal
  },
   data (){
        return{
          arrCardTv:'',
          arrCardFilm:'',
          titleMedia: 'naruto'
        }
  },
  created (){
    axios.get(`https://api.themoviedb.org/3/search/movie?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&query=${this.titleMedia}`)
    .then((arrFilm)=> {
    this.arrCardFilm = arrFilm.data.results
    // console.log('film----------', this.arrCardFilm);
    })
    axios.get(`https://api.themoviedb.org/3/search/movie?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&query=${this.titleMedia}`)
    .then((arrTv)=> {
    this.arrCardTv= arrTv.data.results
    // console.log('serie tv-------------------', this.arrCardTv)
    })
  }

}
</script>

<style>
</style>
