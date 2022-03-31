<template>
  <main>
      <section>
        <h2>FILM</h2>
        <cardFilmsOriginal :arrCardFilm= 'arrCardFilm'/>
      </section>
      <hr>
      <section>
        <h2>SERIE TV</h2>
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
  }
}
</script>

<style scoped>
  main{
    background-color: gray;
  }

  h2{
    text-align: center;
  }
</style>
