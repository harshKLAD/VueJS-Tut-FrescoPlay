<template>
    <dir class="todo" v-bind:class="{'is-complete':todo.complete}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{todo.title}}
        </p>
    </dir>
</template>

<script>
export default {
  name: 'todoItem',
  props: ['todo']
}
</script>

<style scoped>
    .todo{
        color: red;
    }
</style>
