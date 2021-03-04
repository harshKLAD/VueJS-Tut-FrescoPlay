<template>
    <div :key="task.id" v-for="task in tasks">
        <H3>{{task.id}}</H3>

    </div>
</template>

<script>
export default {
  name: 'tasks',
  props: {
    tasks: Array
  }
}
</script>

<style scoped>

</style>
