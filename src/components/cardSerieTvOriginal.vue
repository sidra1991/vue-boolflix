<template>
<div class="center-card">
  <div class="container-card">
      <div class="card"  v-for="(el, index) in arrCardTv"  :key="index" :data-id="el.id" >
        <img class="bg-img" :src="immage+el.poster_path" :alt="el.title" v-if="el.backdrop_path != null">
        <img class="bg-img"  src="https://picsum.photos/300/350" alt="" v-else>
        <ul>
          <li>
            <button class="b-cast" v-on:click="theCast(el)" > show cast </button>
            <ul v-if="cast.includes(el.id) " >
                <li v-for="(mon, index) in 5" :key="index" >
                  <div class="star-tried" >
                    <img :src="star+moment[index].profile_path" :alt="moment[index].name" v-if="moment[index].profile_path != null">
                     <img src="https://picsum.photos/50/50" :alt="moment[index].name" v-else>
                    {{moment[index].name}}
                  </div>
                </li>
            </ul>
          </li>
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
import axios from 'axios'
export default {
  data () {
    return{
      flag:'https://flagcdn.com/16x12/',
      png:'.png',
      immage:'https://image.tmdb.org/t/p/w400/',
      star:'https://image.tmdb.org/t/p/w45/',
      cast:[],
      castObjet:[],
      moment:[]
    }
  },
  props: {
    arrCardTv:Array,
  },
  methods: {
    theCast (el){
      if(this.cast.includes(el.id) == false ){
        this.cast.push(el.id)
        axios.get(`https://api.themoviedb.org/3/tv/${el.id}?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&append_to_response=credits`)
        .then((credits) => {
        this.moment = credits.data.credits.cast

        })
      }else {
        this.cast.pop(el.id,1)

      }
      this.castObjet.push(this.moment)

    }
  }
}
</script>

<style>

</style>
