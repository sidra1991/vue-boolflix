<template>
  <form @submit.prevent="">
    <input id="nameFilms" type="text" v-model="titleFilms"/>
    <button type="button" @click="$emit(search, titleFilms)">x</button>
  </form>
</template>

<script>
export default {
    name: "navBar"
};
</script>

<style>
</style>
