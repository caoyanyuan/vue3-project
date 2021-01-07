<template>
  <div class="hello">
    <div>x: {{ x }} y: {{ y }}</div> 
  </div>
</template>

<script>
import { reactive, onMounted, onUnmounted,toRefs } from "vue"

function useMouse() {
  const state = reactive({ x: 0, y:0 })
  const update = e => {
    state.x = e.pageX
    state.y = e.pageY
  }
  onMounted(() => {
    window.addEventListener('mousemove', update)
  })
  onUnmounted(() => {
    window.removeEventListener('mousemove', update)
  })
  return toRefs(state)
}

export default {
  name: 'mouseMove',
  setup() {
    const { x,y } = useMouse()

    return {
      x,y
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
