<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click here
    </div>
</template>

<script>
export default {
    props : ['delay'],
    data(){
        return {
            showBlock : false,
            score : 0,
            timer : null,
        }
    },
    // mounted => hook
    mounted(){
        setTimeout(()=>{
            this.showBlock = true;
            this.startTime();
        }, this.delay);
    },
    // // update hook 
    // updated(){
    //     console.log("data update");
    // },
    // //ummounted => when partent is unmount
    // unmounted(){
    //     console.log("components unmounted");
    // },
    methods :{
        startTime(){
            this.timer =setInterval(()=>{
                this.score += 50;
            }, 50)
        },
        stopTimer(){
            clearInterval(this.timer);
            this.$emit("endGame", this.score);
        }
    }

}
</script>

<style scoped>

.block{
    width: 400px;
    height: 300px;
    margin : 20px auto;
    padding-top: 30px;
    background: aqua;
}

</style>