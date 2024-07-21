<template>
  <Carousel :itemsToShow="7" :wrapAround="true" :transition="500">
    <Slide v-for="slide in 10" :key="slide">
      <div class="carousel__item">{{ slide }}</div>
    </Slide>

    <template #addons>
      <Pagination />
    </template>
  </Carousel>
</template>

<script setup>
import { onMounted } from 'vue'
import { Carousel, Pagination, Slide } from 'vue3-carousel'
onMounted(() => {
  const visibleSlide = document.querySelectorAll('.carousel__slide--visible')
  console.log(visibleSlide[0])

  if (visibleSlide) {
    const div = visibleSlide[0].querySelector('div')
    const div2 = visibleSlide[visibleSlide.length - 1].querySelector('div')
    if (div) {
      div.style.color = 'blue'
      div2.style.color = 'blue'
    }
  }
})
</script>

<style lang="stylus">
@import 'vue3-carousel/dist/carousel.css';
  .carousel__item {
    min-height: 200px;
    width: 100%;
    background-color: green;
    color: #fff;
    font-size: 20px;
    border-radius: 8px;
    display: flex;
    justify-content: center;
    align-items: center
}
  .carousel__slide {
    padding: 5;
  }

  .carousel__viewport {
    perspective: 2000px;
  }

  .carousel__track {
    transform-style: preserve-3d;
  }

  .carousel__slide--sliding {
    transition: 0.5s;
  }

  .carousel__slide {
    opacity: 0.9;
    transform: rotateY(-20deg) scale(0.9);
  }
  .carousel__slide--visible:first-of-type[aria-hidden='false'] {
  div {
    color: blue;
  }
}
</style>
<style>
/* .carousel__track
  > .carousel__slide--visible:not(.carousel__slide--visible ~ .carousel__slide--visible) {
  div {
    color: blue;
  }
} */
</style>
