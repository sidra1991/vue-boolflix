<template>
<div class="center-card">
  <div class="container-card">
      <div class="card"  v-for="(el, index) in arrCardTv"  :key="index" >
        <img class="bg-img" :src="immage+el.poster_path" :alt="el.title" v-if="el.backdrop_path != null">
        <img class="bg-img"  src="https://picsum.photos/300/350" alt="" v-else>
        <ul>
          <li>
            <strong>TITOLO:</strong> {{el.name}}
          </li>
          <li v-if=" el.name != el.original_name" >
            <strong>TITOLO ORIGINALE:</strong> {{el.original_name}}
          </li>
          <li>
            <strong>LINGUA:</strong>
              <img :src="flag+el.original_language+png" alt="">
              {{el.original_language}}
          </li>
          <li>
            <strong>VOTO:</strong>
            <span class="stars" v-for="(star, index) in Math.ceil(el.vote_average /2)" :key="index" > ★ </span>
            <span v-for="(star, index) in  5 - (Math.ceil(el.vote_average /2))" :key="index" > ☆ </span>
          </li>
          <li>
            <strong>TRAMA:</strong>
             {{el.overview}}
          </li>
          <li>
          </li>
        </ul>
      </div>
  </div>
</div>
</template>

<script>
export default {
  data () {
    return{
      flag:'https://flagcdn.com/16x12/',
      png:'.png',
      immage:'https://image.tmdb.org/t/p/w400/',
    }
  },
  props: {
    arrCardTv:Array,
  },
}
</script>

<style>

</style>
