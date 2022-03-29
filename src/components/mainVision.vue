<template>
    <div>
        <navBar @search="model"/>
        <p>{{prova}}</p>
        <ul v-for="(el, index) in this.arrCard"  :key="index">
            <img :src="immage+el.backdrop_path" :alt="el.title">
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
                <!-- <i class="fa-solid fa-star" v-bind:class="{bgy: 1 < el.vote_average, bgg}" ></i> -->
                <i class="fa-solid fa-star"></i>
                <i class="fa-solid fa-star"></i>
                <i class="fa-solid fa-star"></i>
                <i class="fa-solid fa-star"></i>
            </li>
        </ul>
        <p>-------------------------------------------------------------</p>
        <ul v-for="(el, index) in this.arrCardTv"  :key="index" >
            <img :src="immage+el.backdrop_path" :alt="el.title">
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
                {{el.vote_average}}
            </li>
        </ul>

    </div>
</template>

<script>

import navBar from '@/components/navBar.vue';
import axios from 'axios'

export default {
    components: {
        navBar
    },
    name:'mainVision',
    data (){
        return{
            flag:'https://flagcdn.com/16x12/',
            png:'.png',
            immage:'https://image.tmdb.org/t/p/w300/',
            prova:'',
            arrCard:'',
            arrCardTv:'',
            titleMedia: 'naruto'
        }
    },
    methods: {
        model(txt){
            this.prova=txt
            this.titleMedia=txt
            console.log(this.titleMedia);
            axios.get(`https://api.themoviedb.org/3/search/movie?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&query=${this.titleMedia}`)
            .then((response) => {
                this.arrCard = response.data.results
            })
            axios.get(`https://api.themoviedb.org/3/search/tv?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&query=it_IT&query=${this.titleMedia}`)
            .then((responTV) => {
                this.arrCardTv = responTV.data.results
                // console.log('quarto------', responTV.data.results)
            })
        }
    },
    created () {
        axios.get(`https://api.themoviedb.org/3/search/movie?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&query=${this.titleMedia}`)
        .then((response) => {
        this.arrCard = response.data.results
        // console.log('primo -------', response)
        // console.log('secondo -------', response.data)
        // console.log('terzo-----', response.data.results  )
        console.log('quarto------', response.data.results[0])
        })
    },
}




</script>

<style>
.bgY{
    color: gold;
    font-size: 2rem;
}
.bgg{
    color: darkgray;
    font-size: 2rem;
}
</style>
