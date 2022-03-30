<template>
  <div>
    <h2>serie tv</h2>
      <ul v-for="(el, index) in arrCardTv"  :key="index">
        <li>
          <img :src="immage+el.backdrop_path" :alt="el.name">
        </li>
        <li>
          {{el.name}}
        </li>
        <li>
          {{el.original_name}}
        </li>
        <li>
          <img :src="flag+el.original_language+png" alt="">
          {{el.original_language}}
        </li>
        <li>
          <span v-for="(star, index) in Math.ceil(el.vote_average /2)" :key="index" > ★ </span>
          <span v-for="(star, index) in 5 - (Math.ceil(el.vote_average /2))" :key="index" > ☆ </span>
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
    arrCardTv:Array,
  },
}
</script>

<style>

</style>
