<template>
    <div class="boxbtn" v-if="showBlock" @Click="stopTimer">
        Click Me Now !
    </div>
</template>

<script>
    export default{
        name:"blockButton",
        data(){
            return{
                showBlock:false,
                timer:null,
                reactionTime:0,
            }
        },
        props:['delay'],
        methods:{
            startTimer(){
                this.timer=setInterval(() => {
                    this.reactionTime+=10;
                },10);
            },
            stopTimer(){
                this.$emit('endGame',this.reactionTime)
                clearInterval(this.timer);
            }
        },
        mounted(){
            setTimeout(()=>{
                this.showBlock=true;
                this.startTimer();
                            },this.delay)
            console.log('The componenet got just mounted in the dom');
        },
        updated(){
            console.log('dom updated');
        },
        unmounted(){
            console.log("It just get unmounted");
        }
    }
</script>

<style scoped>
    .boxbtn{
        margin:auto;
        background-color: aquamarine;
        width:500px;height:350px;
        font-size:25pt;
        margin-top: 5%;border-radius:12px;
    }
</style>