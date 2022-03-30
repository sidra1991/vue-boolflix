<template>
  <form action="" @submit.prevent="" @click="$emit('titleSearch', search)">
      <input type="text"
      id="search"
      name="search"
      v-model="search"
    >
    <button type="button"  >
      x
    </button>
  {{ search }}
  </form>
</template>

<script>
export default {
    data () {
    return{
      search:''
    }
  }
}
</script>

<style>

</style>
