<template>
  <main>
    <button id="btnSectionOne" v-on:click="cange()" >Films</button>
    <button id="btnSectionTwo" v-on:click="cange()" >Serie Tv</button>
    <section v-if="donde === 'Films'" >
      <cardFilmsOriginal :arrCardFilm= 'arrCardFilm'/>
    </section>
    <section v-else >
      <cardSerieTvOriginal :arrCardTv='arrCardTv'/>
    </section>
  </main>
</template>

<script>

import cardSerieTvOriginal from '@/components/cardSerieTvOriginal.vue'
import cardFilmsOriginal from '@/components/cardFilmsOriginal.vue'

export default {
  components: {
    cardSerieTvOriginal,
    cardFilmsOriginal
  },
  props: {
    arrCardFilm:Array,
    arrCardTv:Array
  },
  data (){
    return{
      donde:'Films',
    }
  },
  methods: {
    cange (){
      if( this.donde === 'Films' ){
      this.donde = 'SerieTv'
      }else{
      this.donde = 'Films'
      }
    }
  },
}
</script>

<style scoped>

  #btnSectionOne {
    font-size: 1rem;
    position: absolute;
    top:20px;
    left:20px;
    width: 50px;
    height: 30px;
    background-color: transparent;
    border-radius: 50px;
    color: silver;
  }

    #btnSectionTwo {
    font-size: 1rem;
    position: absolute;
    top:20px;
    right: 20px;
    width: 75px;
    height: 30px;
    background-color: transparent;
    border-radius: 50px;
    color: silver;
  }

  #btnSection:hover{
    border: red;
    font-size: 1.2rem;
    background-color: silver;
  }

  section{
    height: calc(100vh - 6rem);
    overflow: auto;
  }

  main{
    position: relative;
    background-color: gray;
  }

  h2{
    text-align: center;
  }
</style>
