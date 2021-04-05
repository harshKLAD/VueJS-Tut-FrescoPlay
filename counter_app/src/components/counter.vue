<template>
    <div class="card-body">
        <div>
            {{hr}} : {{min}} : {{sec}}
        </div>
        <button class="btn btn-primary" @click="showTime2()">Get time</button>
    </div>
</template>

<script>
    export default {
        data () {
            return{
                message: "",
                hr: "0",
                min: "0",
                sec: "0",
                currTime: "0"
            }
        },
        mounted () {
            this.showTime2()
        },
        methods: {
            showTime2(){
                setInterval(()=>
                {
                    //this.hr ++
                    let x = new Date();
        
                    this.hr = x.getHours()
                    this.min = x.getMinutes()
                    this.sec = x.getSeconds()

                    this.currTime = this.hr + " : " + this.min + " : " + this.sec
                    //console.log(this.currTime)
                }
                , 1000)
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>