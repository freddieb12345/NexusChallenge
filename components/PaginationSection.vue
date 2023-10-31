<template>
  <section class="pagination-section">
    <button class="back-to-top paragraph-text">Back to top</button>
    <ul>
      <li>
        <button @click="previousPage">
          <NuxtImg
            alt="Previous page"
            class="left-chevron"
            :src="`/img/LeftChevron.svg`"
            loading="lazy"
            width="10px"
          />
        </button>
      </li>
      <li v-for="page in visiblePages" :key="page">
        <button
          @click="selectPage(page)"
          :class="{ selected: page === currentPage }"
        >
          {{ page }}
        </button>
      </li>
      <li>
        <button @click="nextPage">
          <NuxtImg
            alt="Next page"
            class="right-chevron"
            :src="`/img/RightChevron.svg`"
            loading="lazy"
            width="10px"
          />
        </button>
      </li>
      <li>
        <button @click="lastPage">
          <NuxtImg
            alt="Next page"
            class="right-chevron"
            :src="`/img/RightChevron.svg`"
            loading="lazy"
            width="10px"
          />
          <NuxtImg
            alt="Next page"
            class="right-chevron"
            :src="`/img/RightChevron.svg`"
            loading="lazy"
            width="10px"
          />
        </button>
      </li>
    </ul>
    <div class="sort-dropdown">
      <SortDropdown variant="1" />
    </div>
    <button class="back-to-top-mobile paragraph-text">Back to top</button>
  </section>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";

const pages = ref(10);
const currentPage = ref(1);

const previousPage = () => {
  if (currentPage.value > 1) {
    currentPage.value -= 1;
  }
};

const nextPage = () => {
  if (currentPage.value < pages.value) {
    currentPage.value += 1;
  }
};

const lastPage = () => {
  currentPage.value = pages.value;
};

const selectPage = (index: number) => {
  currentPage.value = index;
  console.log(currentPage.value);
};

const visiblePages = computed(() => {
  const maxVisiblePages = 3;
  const startPage = Math.max(
    1,
    currentPage.value - Math.floor(maxVisiblePages / 2)
  );
  const endPage = Math.min(pages.value, startPage + maxVisiblePages - 1);
  const pagesArray = [];

  for (let i = startPage; i <= endPage; i++) {
    pagesArray.push(i);
  }

  return pagesArray;
});
</script>

<style lang="scss" scoped>
@import "~/assets/scss/variables.scss";
.pagination-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  position: relative;
  width: 100%;
  margin: 40px 0px;
  ul {
    display: flex;
    justify-content: center;
    align-items: center;
    button {
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 8px;
      border-radius: 8px;
      border: 1px solid $framework-borders;
      width: 50px;
      height: 30px;
      background-color: transparent;
      color: $text-gray;
      cursor: pointer;
      &:hover {
        color: $text-black;
        border: 1px solid black;
        .left-chevron,
        .right-chevron {
          filter: invert(1);
        }
      }
    }
    .left-chevron,
    .right-chevron {
      filter: invert(0.5);
    }
  }
}

.back-to-top {
  position: absolute;
  left: 0;
  top: 5px;
  background-color: transparent;
  text-decoration: underline;
  color: $text-gray;
  border: none;
  @media (max-width: 740px) {
    display: none;
  }
}

.back-to-top-mobile {
  background-color: transparent;
  text-decoration: underline;
  color: $text-gray;
  border: none;
  margin-top: 30px;
  @media (min-width: 740px) {
    display: none;
  }
}

.sort-dropdown {
  position: absolute;
  right: 15px;
  top: -10px;
  @media (max-width: 740px) {
    display: none;
  }
}

.selected {
  background-color: $brand-primary !important;
  color: $text-white !important;
}
</style>
