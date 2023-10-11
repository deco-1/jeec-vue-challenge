<template>
    <div id="wrapper" @mousemove="followMouse" ref="mouseBox">
        <div id="svg__wrapper">
            <div class="svg__container">
                <svg width="110" height="100">
                    <circle stroke="white" fill="white" v-bind:cx="cx1" v-bind:cy="cy1" r="23" />
                    <path stroke="#24c992" fill="#24c992" stroke-width="1px"
                        d="M 0 50 L 0 0 L 110 0 L 110 50 L 105 50 q -50 -50 -100 0 Z" />~
                    <path stroke="#24c992" fill="#24c992" stroke-width="1px"
                        d="M 0 50 L 0 100 L 110 100 L 110 50 L 105 50 q -50 40 -100 0 Z" />
                    <path stroke="white" stroke-width="3px" fill="none" d="M 5 51 q 50 -50 100 0" />
                    <path stroke="white" stroke-width="3px" fill="none" d="M 5 49 q 50 40 100 0" />
                </svg>
            </div>
            <div class="svg__container">
                <svg width="110" height="100">
                    <circle stroke="white" fill="white" v-bind:cx="cx2" v-bind:cy="cy2" r="23" />
                    <path stroke="#24c992" fill="#24c992" stroke-width="1px"
                        d="M 0 50 L 0 0 L 110 0 L 110 50 L 105 50 q -50 -50 -100 0 Z" />~
                    <path stroke="#24c992" fill="#24c992" stroke-width="1px"
                        d="M 0 50 L 0 100 L 110 100 L 110 50 L 105 50 q -50 40 -100 0 Z" />
                    <path stroke="white" stroke-width="3px" fill="none" d="M 5 51 q 50 -50 100 0" />
                    <path stroke="white" stroke-width="3px" fill="none" d="M 5 49 q 50 40 100 0" />
                </svg>
            </div>
        </div>
        <div id="question__wrapper">
            <h2>Lorem ipsum?</h2>
            <input @input="handleAnswer" placeholder="Answer...">
        </div>
    </div>
</template>

<script>
export default ({
    data() {
        return {
            cx1: 55,
            cy1: 47,
            cx2: 55,
            cy2: 47,
        }
    },
    methods: {
        followMouse(e) {
            const box = this.$refs.mouseBox;
            const wrapperRect = box.getBoundingClientRect();

            const xMax = window.screen.width,
                xCenter1 = wrapperRect.left + (wrapperRect.width / 2) - 65,
                xCenter2 = wrapperRect.left + (wrapperRect.width / 2) + 65;
            const yMax = window.screen.height,
                yCenter = wrapperRect.top + 50;

            const rangeX1 = (e.pageX - xCenter1) / (xMax/2);
            const rangeX2 = (e.pageX - xCenter2) / (xMax/2);
            const rangeY = (e.pageY - yCenter) / (yMax/2);

            this.cx1 = 55 + 110 * (rangeX1/3);
            this.cy1 = 47 + 100 * (rangeY/5);
            this.cx2 = 55 + 110 * (rangeX2/3);
            this.cy2 = 47 + 100 * (rangeY/5);
        },

        handleAnswer(e) {
            const formattedAnswer = e.target.value.toLowerCase();

            if (formattedAnswer == "dolor") {
                this.$emit("answer", e.target.value, true);
            } else {
                this.$emit("answer", e.target.value, false);
            }
        }
    }
});

</script>

<style scoped>
#wrapper {
    width: 100%;
    border-radius: 25px;
    display: flex;
    flex-direction: column;
    overflow-y: auto;
    overflow-x: hidden;
}

#svg__wrapper {
    pointer-events: none;
    align-items: center;
    display: flex;
    gap: 20px;
    justify-content: center;
}

.svg__container {
    pointer-events: none;
    scale: 1.1;
}

#question__wrapper {
    flex-grow: 1;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;
    pointer-events: none;
}

#question__wrapper h2{
    color: #1a1a1a;
    font-family: Kanit, sans-serif;
    font-size: 3.45rem;

}

#question__wrapper input {
    font-size: 1.7rem;
    border-radius: 2rem;
    padding-left: 2rem;
    border: 3px solid #4e967e;
    background-color: #6ed3b1;
    color: rgb(0, 0, 0);
    max-width: 300px;
    pointer-events: all;
}

#question__wrapper input::placeholder {
    color: rgb(0, 0, 0);  
}
</style>