<template>
    <div class="card-body col-3 rounded-3 m-3 shadow-lg bg-light">
        <div class="card-header bg-light d-flex flex-row justify-content-between">
            <h4 class="card-title">{{ person.name }}</h4>
            <i class="fas fa-user-circle fa-2x"></i>
        </div>
        <ul class="list-group list-group-flush">
            <li class="list-group-item">{{person.id}}</li>
            <li class="list-group-item">{{person.username}}</li>
            <li class="list-group-item">{{person.email}}</li>
        </ul>
        <br>
        <div class="d-flex flex-row justify-content-between">
            <a href="#" class="btn btn-primary">
                <span class="me-2">
                     {{person.website}}
                </span>
                <i class="fas fa-external-link-alt"></i>
            </a>
            <button class="btn btn-danger" v-on:click="del(person.id)"><i class="fas fa-trash-alt"></i></button>
        </div>
    </div>
</template>

<script>
    export default {
        data () {
            return {

            }
        },
        props: {
            person : Object
        },
        methods: {
            del(id) {
                console.log(id)
                this.$emit("personDel",id)
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>