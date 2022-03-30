<template>
  <div>
      sono una carta film
      <ul v-for="(el, index) in this.arrCardFilm"  :key="index">
        <li>
          qui va il titolo
        </li>
        <li>
          qui va il titolo originale
        </li>
        <li>
          qui va la lingua
        </li>
        <li>
          qui va il voto {{this.arrCardFilm}}
        </li>
      </ul>
  </div>
</template>

<script>
export default {
    props: {
    arrCardFilm:Array,
  },
}
</script>

<style>

</style>
