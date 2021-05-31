<template>
    <section class="block" v-if="showBlock" @click="stopTimer">
        ... Click me
    </section>
</template>

<script>
export default {
    // props "delay" allow us to use this property in another component, "block.vue" in here
    props: ["delay"],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
        };
    },
    // Vue calls the mounted() hook when your component is added to the DOM => which is call in App.vue when "play" is pressed (CF lifeCycle hooks)
    mounted() {
        // After whatever the value of delay is => turn shoBlock to true
        setTimeout(() => {
            this.showBlock = true;
            this.startTimer();
        }, this.delay);
    },
    methods: {
        // each 10ms, 10 is gonne be added in reactionTime
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10;
            }, 10);
        },
        stopTimer() {
            // it's gonne stop the setInterval assigned to this.timer and clear reaction time
            clearInterval(this.timer);
            // $emit creates a custom event which is named as the string in ("name", data we want to send when event occurs)
            this.$emit("end", this.reactionTime);
        },
    },
};
</script>

<style scoped>
.block {
    width: 400px;
    height: 300px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: rgba(255, 47, 0, 0.678);
    margin-left: 50%;
    margin-top: 50px;
    transform: translateX(-50%);
    border-radius: 20px;
    font-size: 2.5rem;
    color: white;
}
</style>
