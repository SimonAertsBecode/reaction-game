<template>
    <div id="app">
        <h1>Becode's competition reaction timer</h1>
        <Intro @next="nextstep"></Intro>
        <button v-if="playButton" @click="start" :disabled="isPlaying">
            Play
        </button>
        <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
        <results v-if="showResults" :score="score"></results>
    </div>
</template>

<script>
import Intro from "./components/Intro.vue";
import Block from "./components/Block";
import Results from "./components/Results.vue";

export default {
    name: "App",
    props: ["level"],
    components: {
        Intro,
        Block,
        Results,
    },

    data() {
        return {
            playButton: false,
            // will become true when the button is clicked
            isPlaying: false,

            // amount of time de delay will be for the block appearing on the screen
            delay: null,

            score: null,
            showResults: false,
        };
    },

    methods: {
        nextstep(playButton) {
            this.playButton = playButton;
        },

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

<style scoped>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}

button {
    border: none;
    border-radius: 20px;
    margin-top: 50px;
    padding: 20px;
    font-size: 1.3rem;
    font-weight: bold;
    letter-spacing: 2px;
    cursor: pointer;
}

button:hover {
    box-shadow: 0px 0px 0px 2px rgba(0, 0, 0, 0.397);
    transition: 0.5s;
}
</style>
