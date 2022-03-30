<template>
  <div>
      sono una carta film
      <ul v-for="(el, index) in arrCardFilm"  :key="index">
        <li>
          <img :src="immage+el.backdrop_path" :alt="el.title">
        </li>
        <li>
          {{el.title}}
        </li>
        <li>
          {{el.original_title}}
        </li>
        <li>
          {{el.original_language}}
        </li>
        <li>
          {{el.vote_average}}
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  data () {
    return{
      immage:'https://image.tmdb.org/t/p/w300/'
    }
  },
  props: {
    arrCardFilm:Array,
  },
}
</script>

<style>

</style>
