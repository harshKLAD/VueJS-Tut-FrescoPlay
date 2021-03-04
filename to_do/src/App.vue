<template>
  <div id="app">
    <Todos v-bind:todos="todos" />
  </div>
</template>

<script>
import Todos from './components/todo.vue'

export default {
  name: 'App',
  components: {
    Todos
  },
  data () {
    return {
      todos: [
        {id: 1,
          title: 'hi',
          completed: false
        },
        {id: 2,
          title: 'harsh',
          completed: true
        }
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
