<template>
  <NavBar />
  <FinanceSection />
  <section class="main-listings_container container">
    <FilterMenu />
    <ResultsSection />
  </section>
  <section class="filter-button-section">
    <button class="filter-button">
      <NuxtImg
        alt="Filter Image"
        class="filter-image"
        src="/img/Filters.svg"
        loading="lazy"
      />
      Filters
    </button>
  </section>
</template>

<style lang="scss" scoped setup>
@import "~/assets/scss/variables.scss";

.main-listings_container {
  margin-top: 20px;
  display: flex;
  position: relative;
}

.filter-button-section {
  display: none;
  width: 100%;
  position: fixed;
  top: calc(100vh - 59px);
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.00) 0%, #FFF 100%);
  padding-bottom: 10px;

  @media (max-width: 642px) {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .filter-button {
    padding: 11px 25px 12px;
    color: white;
    background-color: $brand-primary;
    border-radius: 16px;
    font: 600 16px/27px "Overpass", sans-serif;
    border: none;

    &:active {
      color: black;
      border: 1px solid black;
    }
  }
}
</style>
