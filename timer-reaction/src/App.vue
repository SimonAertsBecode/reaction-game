<template>
    <div id="app">
        <h1>Becode's competition reaction timer</h1>
        <button @click="start" :disabled="isPlaying">Play</button>
        <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
        <results v-if="showResults" :score="score"></results>
    </div>
</template>

<script>
import Block from "./components/Block";
import Results from "./components/Results.vue";

export default {
    name: "App",
    props: ["level"],
    components: {
        Block,
        Results,
    },

    data() {
        return {
            // will become true when the button is clicked
            isPlaying: false,

            // amount of time de delay will be for the block appearing on the screen
            delay: null,

            score: null,
            showResults: false,
        };
    },

    methods: {
        start() {
            this.isPlaying = true;
            this.delay = 1000 + Math.random() * 6000;
            this.showResults = false;
        },
        // in this function we have access to the parameter defined in the this.$emit in Block.vue => reactionTime
        endGame(reactionTime) {
            this.score = reactionTime;
            this.isPlaying = false;
            this.showResults = true;
        },
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
