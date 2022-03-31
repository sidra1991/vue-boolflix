<template>
<div class="center-card">
  <div class="container-card">
      <div class="card"  v-for="(el, index) in arrCardFilm"  :key="index">
        <img class="bg-img" :src="immage+el.backdrop_path" :alt="el.title" v-if="el.backdrop_path != null">
        <img class="bg-img"  src="https://picsum.photos/300/350" alt="" v-else>
        <ul>
          <li>
            <strong>TITOLO:</strong> {{el.title}}
          </li>
          <li v-if=" el.title != el.original_title" >
            <strong>TITOLO ORIGINALE:</strong> {{el.original_title}}
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
    width: 90%;
    flex-wrap: wrap;
  }

  .card{
    display: inline-block;
    position: relative;
    height: 350px;
    width: 300px;
    margin :1rem;
    background-color: black;
    color: white;
    border: 2px solid white;
    overflow: auto;
  }

  ul{
    padding-top: 1rem;
    padding-right: 2rem;
    display: none;
  }

  .bg-img{
    position: absolute;
    width: 100%;
    height: 100%;
  }

  .stars {
    color:yellow
  }


  .card:hover ul{
    display: block ;
  }

  .card:hover .bg-img{
    display: none;
  }
</style>
