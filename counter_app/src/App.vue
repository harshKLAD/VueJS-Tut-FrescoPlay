<template>
  <div id="app" class="card">
    <h1 class="">Counter App</h1>
    <Counter />
    <addCounter />
  </div>
</template>

<script>
import Counter from './components/counter.vue'
import addCounter from './components/addCounter.vue'

export default {
  name: 'App',
  components: {
    Counter, addCounter
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
