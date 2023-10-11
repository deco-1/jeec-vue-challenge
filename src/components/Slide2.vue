<template>
    <div id="wrapper">
        <h2>Choose Your Date</h2>
        <input @input="handleDate" type="date">
    </div>
</template>

<script>
    export default {
        methods: {
            handleDate(e) {
                const formattedDate = e.target.value.replaceAll("-", "/");

                this.$emit("date", formattedDate);
            }
        },
    }

</script>

<style scoped>
    #wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }

    #wrapper h2 {
        font-family: Kanit, sans-serif;
        font-size: 3rem;
        padding-bottom: 4rem;
        color: #1a1a1a;
    }

    input {
        font-size: 1.5rem;
        border-radius: 2rem;
        padding-left: 2rem;
        border: 3px solid #4e967e;
        background-color: #6ed3b1;
        color: rgb(0, 0, 0);
        font-family: Kanit, sans-serif;
        display: inline-flex;
        align-items: center;
    }
</style>