<template>
  <section class="results-section">
    <SecondaryFilterMenu />
    <ResultsContainer />
    <PaginationSection />
    <RepresentativeExample />
  </section>
</template>

<style lang="scss" scoped>

.results-section {
  width: 100%;
  @media (min-width: 642px) and (max-width: 992px) {
    padding-left: 15px;
  }
}
</style>
