<template>
    <section class="intro" v-if="introBlock">
        <p>
            Welcome to the reaction timer game, the principle is simple. How it
            works?
        </p>
        <p>
            Once you're ready you will click on the "play" button, After
            clicking on it a square will appear underneath after a random amount
            of time. When it appears on your screen you will have to click as
            fast as possible on it. Then your score will be showed.
        </p>
        <hr />
        <p>
            Press <span><button @click="understood">here</button></span> to
            continue
        </p>
    </section>
</template>

<script>
export default {
    data() {
        return {
            introBlock: true,
        };
    },

    methods: {
        understood() {
            this.introBlock = false;
            this.playButton = true;
            this.$emit("next", this.playButton);
        },
    },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans&display=swap");

p {
    width: 70%;
    background-color: #e9e9e9;
    margin-left: 50%;
    transform: translateX(-50%);
    padding: 20px;
    border-radius: 20px;
    font-family: "Open Sans", sans-serif;
}

button {
    border: none;
    border-radius: 10px;
    padding: 5px;
    background-color: #b6b6b6;
    font-size: 1rem;
    cursor: pointer;
}
</style>
