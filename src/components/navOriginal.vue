<template>
  <header>
    <div class="center-header">
      <div>
        <h1>BOOLFLIX</h1>
      </div>
      <form @submit.prevent="" @keyup.enter="$emit( 'ric', titleFilms)" >
        <input class="inp" type="text" v-model="titleFilms"/>
        <button type="button" @click="$emit( 'ric', titleFilms)" >cerca</button>
      </form>
    </div>
  </header>
</template>

<script>
export default {
    name: 'navOriginal',
    data () {
    return{
      titleFilms:''
    }
  }
}
</script>

<style>
h1{
  color: red;
}

header{
  background: black;
  height: 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
}
.center-header{
  width: 80%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

button{
  border-radius: 20px;
}

button:hover{
  box-shadow:2px -2px 10px dimgray;
  color: darkslategray;
}

.inp{
  border-radius: 20px;
}
</style>
