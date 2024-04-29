<template>
  <div class="home">
    <div>
      <button @click="decreaseCounter" class="btn">-</button>
      <span class="counter">{{ counter }}</span>
      <button @click="increaseCounter" class="btn">+</button>
    </div>
  </div>
</template>

<!-- composition API - script setup pattern -->
<script setup>
import { ref } from 'vue'

const counter = ref(0)

function decreaseCounter() {
  counter.value--
}
function increaseCounter() {
  counter.value++
}

</script>

<!-- composition API - setup function pattern -->
<!-- <script>
import { ref } from 'vue'
export default {
  setup() {
    const counter = ref(0)

    function decreaseCounter() {
      counter.value--
    }
    function increaseCounter() {
      counter.value++
    }

    return {
      counter, increaseCounter, decreaseCounter
    }
  }
}
</script> -->

<!-- Options API -->
<!-- <script>
export default{
  data(){
    return{
      counter:0
    }
  },
 methods:{
  decreaseCounter(){
    this.counter--
  },
   increaseCounter(){
     this.counter++
   }
 }
}
</script> -->

<style>
.home {
  text-align: center;
  padding: 20px;
}

.btn,
.counter {
  font-size: 40px;
  margin: 10px;
}
</style>