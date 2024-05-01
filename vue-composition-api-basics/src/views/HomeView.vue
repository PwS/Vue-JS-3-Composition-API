<template>
  <div class="home">

<h2>{{ appTitle }}</h2>
  <h3>{{ counterData.title }} : </h3>
    <div>
      <button @click="decreaseCounter" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter" class="btn">+</button>
    </div>

    <div class="edit">
      <h4>Edot Counter Title:</h4>
      <input v-model ="counterData.title"type="text">
    </div>

  </div>
</template>

<!-- composition API - script setup pattern -->
<script setup>
import { ref,reactive } from 'vue'

const appTitle='My Counter App'

// const counter = ref(0),counterTitle = ref('Counter')


// reactive object
const counterData=reactive({
  count:0,
  title:"My Counter"

})

function decreaseCounter() {
  // counter.value--
  counterData.count--
}
function increaseCounter() {
  // counter.value++
  counterData.count++
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
},
.edit{
  margin: 60px;
}
</style>