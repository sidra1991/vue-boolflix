<template>
  <div>
    <form @submit.prevent="" @keyup.enter="$emit(titleFilms)">
      <input type="text" v-model="titleFilms"/>
      <button type="button" @click="$emit( 'ric', titleFilms)" >x</button>
    </form>
    {{titleFilms}}
  </div>
</template>

<script>
export default {
    name: 'navOriginal',
    data () {
    return{
      titleFilms:'naruto'
    }
  },
}
</script>

<style>

</style>
