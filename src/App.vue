<template>
  <div>
    <div @click="add">{{state.count}}</div>
    <div>{{state.doubleCount}}</div>

    <mouse />
  </div>
</template>

<script>
import { reactive,computed } from 'vue'
import Mouse from "@/components/mouse"

export default {
  name: 'App',
  setup() {
    const state = reactive({ 
      count: 0,
      doubleCount: computed(() => state.count * 2)
    })

    function add() {
      state.count++
    }

    console.log('abc', state)
    return { state, add }
  },
  components: {
    Mouse
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
