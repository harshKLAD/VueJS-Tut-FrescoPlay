<template>
    <div class="card-body">
        
        <hr>
        <label for="count">{{count}}</label>
        <br>
        <button class="btn btn-primary" v-on:click="add()">Add</button>
        <button class="btn btn-secondary" v-on:click="sub()">Subtract</button>
        <br><br>
        <label class="alert alert-danger" v-if="subZero">Number Cannot go below 0!</label>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                count: 0,
                subZero: false
            }
        },
        methods: {
            add(){
                this.count++
                this.subZero = false
            },
            sub(){
                this.count--
                if (this.count < 0){
                    this.subZero = true
                    this.count++
                    return
                }else{
                    this.subZero = false
                    return
                }
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>