<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in todos">
            <h1>{{todo.id}}</h1>
            <todo-item v-bind:todo="todo"/>
        </div>
    </div>
</template>

<script>
import todoItem from './todoItem.vue'

export default {
  name: 'Todos',
  props: ['todos'],
  components: {
    todoItem
  }
}
</script>

<style scoped>

</style>
