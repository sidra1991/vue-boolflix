<template>
<div class="center-card">
  <div class="container-card">
      <div class="card"  v-for="(el, index) in arrCardFilm"  :key="index">
        <img class="bg-img" :src="immage+el.backdrop_path" :alt="el.title" v-if="el.backdrop_path != null">
        <ul>
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
  </div>
</div>
</template>

<script>
export default {
  data () {
    return{
      flag:'https://flagcdn.com/16x12/',
      png:'.png',
      immage:'https://image.tmdb.org/t/p/w342/',
    }
  },
  props: {
    arrCardFilm:Array,
  }
}
</script>

<style>
  .center-card {
    display: flex;
    justify-content: center;
  }

  .container-card {
    display: flex;
    width: 80%;
    flex-wrap: wrap;
  }

  .card{
    display: inline-block;
    position: relative;
    height: 200px;
    width: 350px;
    background: black;
    margin :2rem;
  }

  .bg-img{
    position: absolute;
    width: 100%;
    height: 100%;
  }


</style>
