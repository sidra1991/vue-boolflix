<template>
    <div>
        <navBar @search="model"/>
        <!-- <p>{{prova}}</p> -->
        <ul v-for="(el, index) in this.arrCard"  :key="index" >
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

import navBar from '@/components/navBar.vue';
import axios from 'axios'

export default {
    components: {
        navBar
    },
    name:'mainVision',
    data (){
        return{
            prova:'',
            arrCard:'',
            titleMedia: 'naruto'
        }
    },

    computed: {
        model (text){
            console.log(text)
            console.log(this.titleMedia)
            return{
                titleMedia=text
            }
        }
    },
    created () {
        axios.get(`https://api.themoviedb.org/3/search/movie?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&query=${this.titleMedia}`)
        .then((response) => {
        this.arrCard = response.data.results
        // console.log('primo -------', response)
        // console.log('secondo -------', response.data)
        // console.log('terzo-----', response.data.results  )
        // console.log('quarto------', response.data.results[0])
    })
  }
}




</script>

<style>

</style>
