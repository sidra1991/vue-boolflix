<template>
  <main>
      sono il main
      <section>
        sono la sezione dei film
        <cardFilmsOriginal :arrCardFilm= 'arrCardFilm'/>
      </section>
      <hr>
      <section>
        sono la sezione delle serie tv
        <cardSerieTvOriginal :arrCardTv='arrCardTv'/>
      </section>
      <!-- {{this.arrCardFilm}} -->
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

<style>

</style>
