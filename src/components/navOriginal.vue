<template>
  <div>
    <form @submit.prevent="">
      <input id="nameFilms" type="text" v-model="titleFilms"/>
      <button type="button" @click="$emit(search, titleFilms)">x</button>
    </form>
    {{titleFilms}}
  </div>
</template>

<script>
export default {
    name: 'navOriginal',
    data () {
    return{
      titleFilms:''
    }
  },
  con (){
    console.log('io parto');
  }
}
</script>

<style>

</style>
