<template>
  <div>
      <h2>film</h2>
      <ul v-for="(el, index) in arrCardFilm"  :key="index">
        <li>
          <img :src="immage+el.backdrop_path" :alt="el.title" v-if="el.backdrop_path != null">
          <div class="ssimmage" v-else></div>

        </li>
        <li>
          {{el.title}}
        </li>
        <li>
          {{el.original_title}}
        </li>
        <li>
           <img :src="flag+el.original_language+png" alt="">
            {{el.original_language}}
        </li>
        <li>
          <span v-for="(star, index) in Math.ceil(el.vote_average /2)" :key="index" > ★ </span>
          <span v-for="(star, index) in  5 - (Math.ceil(el.vote_average /2))" :key="index" > ☆ </span>
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  data () {
    return{
      flag:'https://flagcdn.com/16x12/',
      png:'.png',
      immage:'https://image.tmdb.org/t/p/w300/',
    }
  },
  props: {
    arrCardFilm:Array,
  }
}
</script>

<style>
  .ssimmage {
    height: 100px;
    widows: 100px;
    background: black;
  }
</style>
