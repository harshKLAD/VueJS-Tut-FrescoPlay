<template>
    <button :style="{background: color}">{{text}}</button>
</template>

<script>
export default {
  name: 'btn',
  props: {
    text: String,
    color: String
  }
}
</script>

<style scoped>
    button{
        background: black;
        color: white;
        padding: 5px 10px;
    }
</style>
