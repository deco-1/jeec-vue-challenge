<template>
    <div id="header__wrapper">
        <h1 id="title">JEEC Challenge 24</h1>
        <DateTime />
    </div>
    <div id="carousel__wrapper">
        <carousel :items-to-show="1" :wrap-around="true">
            <slide v-for="slide in 4" :key="slide">
                <div v-if="slide == 1" class="carousel__item">
                    <Slide1 @answer="handleAnswer"/>
                </div>
                <div v-if="slide == 2" class="carousel__item">
                    <Slide2 @date="handleDate"/>
                </div>
                <div v-if="slide == 3" class="carousel__item">
                    <Slide3 />
                </div>
                <div v-if="slide == 4" class="carousel__item">
                    <Slide4 />
                </div>
            </slide>
    
            <template #addons>
                <navigation />
                <pagination />
            </template>
        </carousel>
    </div>
    <div id="answer__wrapper">
        <h2 id="answer" ref="answer">{{ answer }}</h2>
        <h2 id="date" ref="date"></h2>
    </div>
</template>

<script>
import { defineComponent } from 'vue'
import { Carousel, Navigation, Pagination, Slide } from 'vue3-carousel'

import 'vue3-carousel/dist/carousel.css'
import DateTime from './components/DateTime.vue'
import Slide1 from './components/Slide1.vue'
import Slide2 from './components/Slide2.vue'
import Slide3 from './components/Slide3.vue'
import Slide4 from './components/Slide4.vue'

export default defineComponent({
    name: 'App',
    components: { Carousel, Slide, Pagination, Navigation, DateTime, Slide1, Slide2, Slide3, Slide4, },
    data() {
        return {
            answer: ""
        }
    },
    methods: {
        handleAnswer(answer, state) {
            this.answer = answer;
            
            if(state) {
                this.$refs.answer.classList.add("correct");
            } else {
                this.$refs.answer.classList.remove("correct");
            }
        },

        handleDate(date) {
            this.$refs.date.innerHTML = date;
        }
    },
}); 
</script>

<style>
@font-face {
    font-display: swap;
    font-family: "Source Code Pro";
    font-style: normal;
    font-weight: 700;
    src: url(./assets/fonts/SourceCodePro-Bold.ttf);
}

@font-face {
    font-display: swap;
    font-family: "Kanit";
    font-style: normal;
    font-weight: 400;
    src: url(./assets/fonts/Kanit-Regular.ttf);
}

@font-face {
    font-display: swap;
    font-family: "Kanit";
    font-style: normal;
    font-weight: 600;
    src: url(./assets/fonts/Kanit-SemiBold.ttf);
}

@font-face {
    font-display: swap;
    font-family: "Kanit";
    font-style: normal;
    font-weight: 700;
    src: url(./assets/fonts/Kanit-Bold.ttf);
}

::-webkit-scrollbar {
    width: 10px;
}

::-webkit-scrollbar-track {
    background: #F2F2F2;
}

::-webkit-scrollbar-thumb {
    background: #BDBDBD;
}

::-webkit-scrollbar-thumb:hover {
    background: #6E6E6E;
}

*,
*::before,
*::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    background-color: #1a1a1a;
    height: 100vh;
}

#header__wrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 90%;
    margin: 0 auto;
}

#title {
    color: white;
    font-family: Kanit;
    font-size: 4rem;
    font-weight: 600;
    text-align: center;
}

#carousel__wrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 60%;
    margin: 0 auto;
}

.carousel__item {
    background-color: #24c992;
    border-radius: 25px;
    display: flex;
    height: 400px;
    justify-content: center;
    overflow: hidden;
    width: 100%;
}

.carousel__slide {
    padding: 50px;
}

.carousel__prev,
.carousel__next {
    color: rgba(255, 255, 255, 0.35);
}

.carousel__prev:hover,
.carousel__next:hover {
    color: white;
}

.carousel__pagination {
    margin: -20px 0 0 0;
}

.carousel__pagination-button {
    position: relative;
    z-index: 1;
}

.carousel__pagination-button::after {
    background-color: rgba(255, 255, 255, 0.35);
}

.carousel__pagination-button:hover::after,
.carousel__pagination-button--active::after {
    background-color: white;
}

.carousel__prev:focus-visible,
.carousel__next:focus-visible,
.carousel__pagination-button:focus-visible {
    border: 1px solid invert;
}

#answer__wrapper {
    font-family: Kanit, sans-serif;
    font-weight: 600;
    font-size: 3rem;
    display: flex;
    justify-content: space-between;
    width: 70%;
    margin: 0 auto;
    flex-wrap: wrap;
}

#answer {
    color: #bb3737;
}

#answer:not(:empty)::before {
    content: url(./assets/cross.svg);
    display: inline-block;
    width: 2.3rem;
    height: 2.3rem;
    color: #bb3737;
    scale: 0.9;
}

#answer.correct {
    color: #38b238;
}

#answer.correct::before {
    content: url(./assets/check.svg);
    color: #38b238;
    scale: 1;
}

#date {
    color: white;
}

</style>
