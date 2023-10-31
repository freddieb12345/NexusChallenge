<template>
  <button 
    class="paragraph-text"
    :class="['button-variant' + variant, { selected }]" 
    @click="handleClick"
  >
    <slot></slot>
  </button>
</template>

<script setup>
const props = defineProps({
  variant: {
    type: String,
  },
  selected: {
    type: Boolean,
  }
});

const emit = defineEmits();

const handleClick = () => {
  emit('click');
}
</script>

<style lang="scss" scoped>
@import "~/assets/scss/variables.scss";

%btn-shared-styles {
  border: none;
  cursor: pointer;
  border-radius: 12px;
  padding: 8px 25px;
  margin-right: 5px;
  
}

.button-variant1,
.button-variant2 {
  @extend %btn-shared-styles;
  @media (min-width: 642px) and (max-width: 720px) {
    font-size: 14px;
  }
  &.selected {
    border: solid 1px black;
    color: $text-black;
  }
}

.button-variant1 {
  background-color: $brand-primary;
  color: $text-white;
  border: white solid 1px;
}

.button-variant2 {
  background-color: $brand-secondary;
  color: $text-gray;
  border: $framework-borders solid 1px;
}

.button-variant3 {
  border: none;
  cursor: pointer;
  font-size: 14px;
  padding: 8px 0;
  width: 25%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: $text-white;
  
  &.selected {
    border-bottom: solid 3px $brand-primary;
  }
}
</style>
