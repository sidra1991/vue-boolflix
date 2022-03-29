<template>
    <ul>
        <li>
            {{arrCard[0].title}}
        </li>
        <li>
            {{arrCard[0].original_title}}
        </li>
        <li>
            {{arrCard[0].original_language}}
        </li>
        <li>
            {{arrCard[0].vote_average}}
        </li>
    </ul>
</template>

<script>
import axios from 'axios'
export default {
    name:'mainVision',
    data (){
        return{
            arrCard:''
        }
    },
    created () {
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=2a1eafb77e5173892c5f55c2d7d7a8c8&query=naruto')
      .then((response) => {
        this.arrCard = response.data.results
        console.log('primo -------', response)
        console.log('secondo -------', response.data)
        console.log('terzo-----', response.data.results  )
        console.log('quarto------', response.data.results[0])
        // console.log( 'test', this.arrCard[0].vote_average);
    })
  }
}




</script>

<style>

</style>
