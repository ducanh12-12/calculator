<template>
<section>
  <div class='app'>
    <input type="text" v-model="screen"  placeholder="nhập sô gì vào đi nà" />
  <div>
    <button @click="handleReload" >AC</button>
    <button @click="handleDetele" >DL</button>
    <button @click="handleCalc" >*</button>
    <button @click="handleCalc" >/</button>
 </div>
 <div>
    <button @click="handleCalc">1</button>
    <button @click="handleCalc">2</button>
    <button @click="handleCalc">3</button>
    <button @click="handleCalc">+</button>
 </div>
 <div>
    <button @click="handleCalc">4</button>
    <button @click="handleCalc">5</button>
    <button @click="handleCalc">6</button>
    <button @click="handleCalc">-</button>
 </div>
 <div>
    <button @click="handleCalc">7</button>
    <button @click="handleCalc">8</button>
    <button @click="handleCalc">9</button>
    <button @click='handleEqual'>=</button>
 </div>
  </div>
 </section>
</template>

<script>
import {ref} from 'vue'

export default {
  name: 'App',
  setup() {
    const screen = ref('');
    const equal = ref('');
    const arr = ref([])
    function handleCalc(e) {
      arr.value.push(e.target.innerHTML);
      screen.value= arr.value.toString().replace(/,/g,"")
    }
    function handleEqual() {
        equal.value = eval(screen.value)
        screen.value = equal.value
        arr.value = []
        arr.value.push(eval(screen.value))
      
    }
    function handleReload() {
      arr.value = []
      screen.value = ''
    }
    function handleDetele() {
      arr.value.pop()
      screen.value= arr.value.toString().replace(/,/g,"")
    }
    return{
      screen:screen,
      handleCalc,
      handleEqual,
      handleReload,
      handleDetele
    }
  }
}
</script>

<style>
html{
  text-align: center;
}
.app{
  display: inline-block;
  padding: 10px 5px;
  border: 1px solid black;
}
.app input {
  padding: 10px;
  border-radius: 5px;
  background-color: pink;
  font-size: 0.9rem;
  font-weight: 500;
}
button{
  font-size: 1rem;
  font-weight: 500;
  width: 40px;
  height: 30px;
  text-align: center;
  padding: 5px;
  border-radius: 5px;
  margin:5px
}
</style>
