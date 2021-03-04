<template>
    <header>
        <h1>{{ title }}</h1>
        <btn text="Green" color="green"/>
        <btn text="Blue" color="blue"/>
        <btn text="Red" color="red"/>
    </header>
</template>

<script>
import btn from './button'
export default {
  name: 'header',
  props: ['title'],
  components: {
    btn
  }
}
</script>

<style scoped>
    header{
        display: flex;
        justify-content: space-between;
        align-content: center;
        color: black;
    }
</style>
