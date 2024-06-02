<template>
    <div class="carousel">
      <div class="carousel-inner" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
        <div
          v-for="(image, index) in images"
          :key="index"
          class="carousel-item"
        >
          <img :src="image" alt="" />
        </div>
      </div>
      <button @click="prev" class="carousel-control prev">‹</button>
      <button @click="next" class="carousel-control next">›</button>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    name: 'Carousel',
    props: {
      images: {
        type: Array,
        required: true,
      },
    },
    setup(props) {
      const currentIndex = ref(0);
  
      const next = () => {
        currentIndex.value = (currentIndex.value + 1) % props.images.length;
      };
  
      const prev = () => {
        currentIndex.value =
          (currentIndex.value - 1 + props.images.length) % props.images.length;
      };
  
      return {
        currentIndex,
        next,
        prev,
      };
    },
  };
  </script>
  
  <style scoped>
  .carousel {
    position: relative;
    width: 100%;
    max-width: 600px;
    margin: auto;
    overflow: hidden;
  }
  
  .carousel-inner {
    display: flex;
    transition: transform 0.5s ease-in-out;
  }
  
  .carousel-item {
    min-width: 100%;
  }
  
  img {
    width: 100%;
    display: block;
  }
  
  .carousel-control {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: rgba(0, 0, 0, 0.5);
    color: white;
    border: none;
    padding: 1rem;
    cursor: pointer;
  }
  
  .carousel-control.prev {
    left: 0;
  }
  
  .carousel-control.next {
    right: 0;
  }
  </style>
  