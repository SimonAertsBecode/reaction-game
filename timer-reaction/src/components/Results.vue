<template>
    <section class="results">
        <h3>Your score</h3>
        <p>You took {{ score }} ms to click</p>
        <p>{{ level }}</p>
    </section>
</template>

<script>
export default {
    props: ["score"],
    data() {
        return {
            level: null,
        };
    },

    mounted() {
        if (this.score <= 250) {
            this.level = "You're fast as light ma boy";
        } else if (this.score <= 400) {
            this.level = "fast but not insane";
        } else if (this.score <= 600) {
            this.level = "Want some coffe ma dude?";
        } else {
            this.level = "Go take a nap and come back";
        }
    },
};
</script>

<style scoped>
.results {
    width: 40%;
    height: 150px;
    color: rgba(255, 45, 0, 0.6);
    background: #eee;
    margin-left: 50%;
    transform: translateX(-50%);
    margin-top: 50px;
    border-radius: 20px;
}
</style>
