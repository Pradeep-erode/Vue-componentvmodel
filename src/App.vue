<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="msg" v-model="name" push='dog' />
    {{ msgs }}
    <h1>Composition Returns count as = {{count}}</h1>
    <h2>FirstName - {{firstname}}</h2>
    <h2>LastName - {{lastname}}</h2>
    <button @click="increaseCount">Increase:{{ addcounts.addcounts1 }}</button>
    <h4>{{refcounter.count}}</h4>
    <refandRective hik='Hello' />
  </div>
  
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import refandRective from './components/refandreactive.vue'
import { provide, ref, reactive,toRefs } from 'vue'
export default {
  name: 'App',
  components: {
    HelloWorld, refandRective
  },
  data() {
    return {
      name: 'Ft',
      msgs: 'demonData'
    }
  },
  // setup() { -- other type
  setup() {
    //ref and reactive is for the replacement for data return() in option API
    const count = ref(2);

//by using ref for arrayType the output is ==>  { "count": 5 }
    const refcounter=ref({
      count:5 
    })

    const addcounts = reactive({
      addcounts1:0,
      addcounts2:0
    });

    const fullname = reactive({
      firstname: 'pradeep',
      lastname: 'kumar'
    });
    
    const increaseCount = () => {
      addcounts.addcounts1++;
    }
    provide('refcounter', refcounter)
    provide('count', count)
    provide('fullname', fullname)

    return {
      count:8,
      addcounts,
      increaseCount,
      ...toRefs(fullname),
      refcounter
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
