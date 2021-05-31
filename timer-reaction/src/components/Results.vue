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
            this.level = "You're fast as light";
        } else if (this.score <= 400) {
            this.level = "fast but not insane";
        } else if (this.score <= 600) {
            this.level = "Want some coffe?";
        } else {
            this.level = "take a nap and come back";
        }
    },
};
</script>

<style scoped>
.results {
    width: 40%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: rgba(0, 146, 85, 0.6);
    background: #eee;
    margin-left: 50%;
    transform: translateX(-50%);
    margin-top: 50px;
    border-radius: 20px;
}

h3 {
    font-size: 2rem;
    margin: 30px 0;
}

p {
    font-size: 1.3rem;
}

p:nth-child(2) {
    font-style: italic;
}
</style>
