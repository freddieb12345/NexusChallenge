<template>
  <section class="secondary-filter-menu">
    <div class="secondary-filter-menu_left">
      <h2 class="results-number heading-4">Showing 339 cars</h2>
      <FilterButton
        variant="1"
        :selected="selectedButtons[0]"
        @click="selectButton(0)"
        >All</FilterButton
      >
      <FilterButton
        variant="2"
        :selected="selectedButtons[1]"
        @click="selectButton(1)"
        >Used</FilterButton
      >
      <FilterButton
        variant="2"
        :selected="selectedButtons[2]"
        @click="selectButton(2)"
        >New</FilterButton
      >
      <FilterButton
        variant="2"
        :selected="selectedButtons[3]"
        @click="selectButton(3)"
        >Offers</FilterButton
      >
    </div>
    <div class="secondary-filter-menu_right">
      <SortDropdown variant="1" />
    </div>
  </section>
  <section class="secondary-filter-menu-mobile">
    <div class="top-filters">
      <FilterButton
        variant="3"
        :selected="selectedButtons[0]"
        @click="selectButton(0)"
        >All</FilterButton
      >
      <FilterButton
        variant="3"
        :selected="selectedButtons[1]"
        @click="selectButton(1)"
        >Used</FilterButton
      >
      <FilterButton
        variant="3"
        :selected="selectedButtons[2]"
        @click="selectButton(2)"
        >New</FilterButton
      >
      <FilterButton
        variant="3"
        :selected="selectedButtons[3]"
        @click="selectButton(3)"
        >Offers</FilterButton
      >
    </div>
    <div class="bottom-filters">
      <p>Showing 24 of 339 cars</p>
      <SortDropdown variant="2" />
    </div>
  </section>
</template>

<script setup lang="ts">
const selectedButtons = ref([true, false, false, false]);

const selectButton = (index: Number) => {
  selectedButtons.value.forEach((_, idx) => {
    selectedButtons.value[idx] = index === idx;
  });
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/variables.scss";
.secondary-filter-menu {
  width: 100%;
  display: flex;
  justify-content: space-between;
  padding-right: 15px;
  padding-bottom: 30px;

  &_left, &_right {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  @media (max-width: 642px) {
    display: none;
  }
}

.secondary-filter-menu-mobile {
  width: 100%;
  flex-direction: column;
  display: none;

  @media (max-width: 642px) {
    display: flex;
  }

  .top-filters, .bottom-filters {
    display: flex;
    margin-bottom: 23px;
  }

  .bottom-filters {
    justify-content: space-between;
    align-items: center;
    padding: 0px 13px;
    margin-bottom: 20px;
  }
}

.results-number {
  color: $text-black;
  margin-right: 20px;
}
</style>
