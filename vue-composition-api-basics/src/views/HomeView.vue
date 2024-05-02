<template>
  <div class="home">

<h2>{{ appTitle }}</h2>
  <h3>{{ counterData.title }} : </h3>
    <div>
      <button @click="decreaseCounter(2)" class="btn">--</button>
      <button @click="decreaseCounter(1)" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter(1, $event)" class="btn">+</button>
      <button @click="increaseCounter(2)" class="btn">++</button>
    </div>

    <p>
    This Counter is {{oddOrEven}} </p>

    <div class="edit">
      <h4>Edot Counter Title:</h4>
      <input v-model ="counterData.title"type="text">
    </div>

  </div>
</template>

<!-- composition API - script setup pattern -->
<script setup>
import { ref,reactive,computed,watch, onBeforeMount,onMounted } from 'vue'

const appTitle='My Counter App'

// const counter = ref(0),counterTitle = ref('Counter')

// reactive object
const counterData=reactive({
  count:0,
  title:"My Counter"
})

// computed property
const oddOrEven = computed(() => {
  if(counterData.count %2 ===0){
    return 'even'
  }
  return 'odd'
})

//watch
watch(()=>counterData.count,(newValue,oldValue)=>{
  if(newValue===20){
    alert('Way to go! you made it to 20!!')
  }
  console.log("newCount "+newValue,oldValue)
})


function decreaseCounter(value) {
  // counter.value--
  counterData.count -=value
}
function increaseCounter(value,event) {
  // counter.value++
  counterData.count +=value
}

// const increaseCounter =(value,e)=>{
//   console.log(event)
//   counterData.count +=value
// }


onBeforeMount(()=>{
  console.log('onBeforeMount')
})

onMounted(() => {
  console.log('onMounted')})

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

// <script>
// export default {
//   data() {
//     return {
//       count:0
//     }
//   },
//   computed:{
//     myComputedProperty(){
//       // return some logic based on data property
//       return 'my result'
//     }
//   },
//   watch: {
//     count(newCount,oldCount){
//       if(newCount==20){
//         alert('20 Value')
//       }
//     }
//   },
//   mounted () {
//     //do stuff when component is loaded
//     console.log('mounted')
//   },
//   unmounted () {
//     console.log('unmounted')
//   }
// }
// </script>

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