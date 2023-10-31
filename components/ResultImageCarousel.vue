<template>
  <section class="result-image-carousel">
    <div class="carousel-navigation">
      <p class="caption-text">{{imageIndex + 1}} of {{imagePaths.length }}</p>
      <button @click="previousImage">
        <NuxtImg
          alt="Previous Image"
          :src="`/img/LeftChevron.svg`"
          loading="lazy"
          width="10px"
        />
      </button>
      <button @click="nextImage">
        <NuxtImg
          alt="Next Image"
          :src="`/img/RightChevron.svg`"
          loading="lazy"
          width="10px"
        />
      </button>
    </div>
    <section class="images-container">
      <NuxtImg
        v-for="imagePath in imagePaths"
        :style="slideStyle"
        alt="Result Image"
        class="result-image"
        :src="`/img/${imagePath}`"
        loading="lazy"
      />
    </section>
  </section>
</template>

<script setup lang="ts">
const props = defineProps({
  imagePaths: {
    type: Array,
    required: true,
    default: () => [],
  },
});
const imageIndex = ref(0);

const previousImage = () => {
  if (imageIndex.value < 1) return;
  imageIndex.value--;
};

const nextImage = () => {
  if (imageIndex.value >= props.imagePaths.length - 1) return;
  imageIndex.value++;
};

const slideStyle = computed(() => ({
  transform: `translateX(-${imageIndex.value * 100}%)`,
}));
</script>

<style lang="scss" scoped>
@import "~/assets/scss/variables.scss";

.result-image-carousel {
  display: flex;
  width: 100%;
  overflow-x: hidden;
  position: relative;
  &:hover .carousel-navigation {
    opacity: 1;
    visibility: visible;
  }

  .carousel-navigation {
    display: flex;
    visibility: hidden;
    opacity: 0;
    align-items: center;
    gap: 5px;
    position: absolute;
    right: 10px;
    top: 10px;

    p {
      color: $text-white;
      z-index: 20;
    }

    button {
      z-index: 20;
      display: flex;
      padding: 8px;
      justify-content: center;
      align-items: center;
      border-radius: 8px;
      border: 1px solid rgba(255, 255, 255, 0.2);
      background-color: $framework-dark-1;
      cursor: pointer;
    }

    @media (max-width: 642px) {
      display: none;
    }
  }

  .images-container {
    display: flex;
    transition: transform 0.3s ease;
    scrollbar-width: none;
    -ms-overflow-style: none;

    &::-webkit-scrollbar {
      display: none;
    }

    @media (max-width: 642px) {
      gap: 5px;
      overflow-x: scroll;
    }
  }

  .result-image {
    transition: transform 0.3s ease;
    height: 250px;
    min-width: 100%;

    @media (max-width: 642px) {
      min-width: 113px;
      max-height: 84px;
      border-radius: 16px;
    }
  }
}
</style>
