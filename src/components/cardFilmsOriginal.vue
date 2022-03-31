<template>
<div class="center-card">
  <div class="container-card">
      <div class="card"  v-for="(el, index) in arrCardFilm"  :key="index" :data-id="el.id">
        <img class="bg-img" :src="immage+el.poster_path" :alt="el.title" v-if="el.backdrop_path != null">
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
          <li>
            <button v-on:click="theCast(el)" > x </button>
            <ul v-if="cast.includes(el.id) " >
                <li> <div>{{moment}}
                  {{castObjet}} </div> </li>
            </ul>
          </li>
        </ul>
      </div>
  </div>
</div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return{
      flag:'https://flagcdn.com/16x12/',
      png:'.png',
      immage:'https://image.tmdb.org/t/p/w400/',
      cast:[],
      castObjet:[],
      moment:[]
    }
  },
  props: {
    arrCardFilm:Array,
  },
  methods: {
    theCast (el){
      if(this.cast.includes(el.id) == false ){
        this.cast.push(el.id)
        console.log('preso bastardo')
        axios.get(`https://api.themoviedb.org/3/movie/${el.id}?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&append_to_response=credits`)
        .then((credits) => {
        this.moment = credits.data.credits.cast[0].name
        })
      }else {
        this.cast.pop(el.id,1)
        console.log('eccolo');
      }
      this.castObjet.push(this.moment)

    }
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
    border-radius: 5px;
  }

  ul{
    padding-top: 1rem;
    padding-right: 2rem;
    display: none;
  }

  li{
    margin-top: 10px;
    list-style: none;
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
