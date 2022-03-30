<template>
  <main>
      sono il main
      <section   v-for="(el, index) in this.arrCardfilm"  :key="index" >
        sono la sezione dei film
        <cardFilmsOriginal :arrCardFilm= 'arrCardFilm'/>
      </section>
      <section>
        sono la sezione delle serie tv
        <cardSerieTvOriginal />
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
  }
}
</script>

<style>

</style>
