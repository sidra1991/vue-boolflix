<template>
  <body>
    <navOriginal  @ric='cry'/>
    <mainOriginal :arrCardFilm= 'arrCardFilm' :arrCardTv='arrCardTv' />
    <footerOriginal />
  </body>
</template>

<script>
// import mainVision from './components/mainVision.vue'
import navOriginal from './components/navOriginal.vue'
import mainOriginal from './components/mainOriginal.vue'
import footerOriginal from './components/footerOriginal.vue'
import axios from 'axios'
export default {
  components: {
    // mainVision,
    navOriginal,
    mainOriginal,
    footerOriginal
  },
   data (){
        return{
          prova:'',
          arrCardTv:[],
          arrCardFilm:[],
          titleMedia: ''
        }
  },
  created (){
    axios.get(`https://api.themoviedb.org/3/search/movie?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&query=${this.titleMedia}`)
    .then((arrFilm)=> {
    this.arrCardFilm = arrFilm.data.results
    // console.log('film----------', this.arrCardFilm);
    })
    axios.get(`https://api.themoviedb.org/3/search/tv?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&query=${this.titleMedia}`)
    .then((arrTv)=> {
    this.arrCardTv= arrTv.data.results
    // console.log('serie tv-------------------', this.arrCardTv)
    })
  },
methods: {
  cry (txt){
      this.prova = txt
      console.log(txt);
      this.titleMedia=txt
      console.log(this.titleMedia);
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&query=${this.titleMedia}`)
      .then((response) => {
        this.arrCardFilm = response.data.results
      })
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&query=it_IT&query=${this.titleMedia}`)
      .then((responTV) => {
        this.arrCardTv = responTV.data.results
        console.log('quarto------', responTV.data.results)
      })
    }
  },
}
</script>

<style>
*{
  margin: 0;
  box-sizing: border-box;
}

body{
  background-color: gray;
  height: 100vh;
  overflow:auto;
}

</style>
