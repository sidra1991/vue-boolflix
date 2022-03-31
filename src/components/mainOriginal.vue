<template>
  <main>
      <section>
        film
        <cardFilmsOriginal :arrCardFilm= 'arrCardFilm'/>
      </section>
      <hr>
      <section>
        serie tv
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
</style>
