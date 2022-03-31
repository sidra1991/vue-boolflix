<template>
  <header>
    <div class="center-header">
      <div class="logo" >
        <h1>BOOLFLIX</h1>
      </div>
      <form @submit.prevent="" @keyup.enter="$emit( 'ric', titleFilms)" >
        <input class="inp" type="text" v-model="titleFilms"/>
        <button id="spostamus" type="button" @click="$emit( 'ric', titleFilms)" >cerca</button>
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

#spostamus {
  position: relative;
  right: 40px;
}

header{
  background: black;
  height: 3rem;
  display: flex;
  flex-wrap: nowrap;
  justify-content: center;
  align-items: center;
}

.center-header{
  width: 80%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo{
  flex-basis: 200px;
  flex-shrink: 1;
}

form{
  flex-shrink: 0;
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
