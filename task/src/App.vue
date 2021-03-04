<template>
  <div class="container">
    <Header title="Task Tracker"/>
    <Tasks v-bind:tasks="tasks"/>
  </div>
</template>

<script>
import Header from './components/header'
import Tasks from './components/tasks'

export default {
  name: 'App',
  components: {
    Header,
    Tasks
  },
  data () {
    return {
      tasks: []
    }
  },
  created () {
    this.tasks = [
      {
        id: 1,
        text: 'Task 1',
        reminder: true
      },
      {
        id: 2,
        text: 'Task 2',
        reminder: false
      },
      {
        id: 3,
        text: 'Task 3',
        reminder: true
      }
    ]
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

.container{
  border: 2px black solid;
  margin: auto;
  padding: 10px;
}
</style>
