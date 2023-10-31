<template>
  <select v-if="variant == '1'" class="dropdown-button paragraph-text">
    <option value="lowest-price">Lowest Price</option>
    <option value="highest-price">Highest Price</option>
    <option value="oldest">Oldest</option>
    <option value="newest">Newest</option>
  </select>
  <select v-if="variant == '2'" class="dropdown-button2 paragraph-text">
    <option value="lowest-price">Lowest Price</option>
    <option value="highest-price">Highest Price</option>
    <option value="oldest">Oldest</option>
    <option value="newest">Newest</option>
  </select>
</template>

<script setup lang="ts">
defineProps({
  variant: {
    type: String,
  }
});
</script>

<style lang="scss" scoped>
@import "~/assets/scss/variables.scss";

.dropdown-button {
  background-color: $framework-light;
  border: none;
  cursor: pointer;
  padding: 13px;
  border-radius: 16px;
  color: $text-gray;
}

.dropdown-button2 {
  background-color: transparent;
  border: none;
  cursor: pointer;
  padding: 13px;
  color: $text-black;
  line-height: 21px;
  font-size: 14px;
}

.chevron-dropdown {
  margin-left: 14px;
  width: 10px;
  height: 10px;
}
</style>
