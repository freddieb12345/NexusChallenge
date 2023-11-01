<template>
  <article class="value-card value-my-car">
    <section>
      <h2 class="heading-3">Value Your Car</h2>
      <p class="paragraph-text">
        Find Out the value of your car in just minutes
      </p>
      <form @submit.prevent="onSubmit">
        <div class="input-section">
          <label class="caption-text" for="vrm">VRM <span>*</span></label>
          <input
            class="paragraph-text"
            id="vrm"
            v-model="vrm"
            type="text"
            placeholder="Enter VRM"
          />
        </div>
        <div class="input-section">
          <label class="caption-text" for="mileage"
            >Mileage <span>*</span></label
          >
          <input
            class="paragraph-text"
            id="mileage"
            v-model="mileage"
            type="text"
            placeholder="Enter mileage"
          />
        </div>
        <button type="submit" class="submit-button button-text">
          Value my car
        </button>
      </form>
    </section>
  </article>
  <article class="value-card value-my-car-mobile">
    <section>
      <h2 class="heading-4">Value your car</h2>
      <p class="caption-text">Find out in just a few minutes</p>
    </section>
    <button class="button-text">Get valuation</button>
  </article>
</template>

<script setup lang="ts">
const vrm = ref("");
const mileage = ref("");
const onSubmit = () => {
  console.log("hello");
};
</script>

<style lang="scss" scoped>
@import "~/assets/scss/variables.scss";

.value-card {
  width: 100%;
  height: 364px;
  flex-shrink: 0;
  border-radius: 16px;
  border: 1px solid $framework-borders;
  background-color: $framework-light;

  section {
    width: 100%;
    padding: 30px;
    display: flex;
    flex-direction: column;
    text-align: center;

    h2 {
      text-align: center;
      padding-bottom: 10px;
    }

    p {
      color: $text-black;
      text-align: center;
      margin-bottom: 34px;
    }

    form {
      display: flex;
      flex-direction: column;
      width: 100%;
    }
  }
}

@media (max-width: 642px) {
  .value-card {
    display: none;
  }
}

.value-my-car-mobile {
  display: none;
  width: calc(100% - 20px);
  margin: 0px 10px 15px 10px;
  height: auto;
  flex-shrink: 0;
  border-radius: 16px;
  border: 1px solid $framework-borders;
  background-color: $framework-light;
  padding: 13px 13px 13px 20px;

  section {
    margin-right: 10px;
    padding: 0;
    width: 50%;

    h2 {
      color: $text-black;
      text-align: left;
    }

    p {
      text-align: left;
      margin-bottom: 0;
    }
  }

  button {
    flex-grow: 1;
    background-color: $brand-primary;
    border: 1px solid transparent;
    color: $text-white;
    border-radius: 16px;
    padding: 12px 25px;

    &:active {
      border-color: black;
      color: $text-black;
    }
  }

  @media (max-width: 642px) {
    display: flex;
  }
}

.input-section {
  position: relative;
  width: 100%;

  label {
    position: absolute;
    top: -9px;
    left: 10px;
    background-color: $framework-light;
    padding: 0 6px;
    border-radius: 100px;

    span {
      color: $traffic-light-red;
    }
  }

  input {
    padding: 13px;
    width: 100%;
    border-radius: 16px;
    margin-bottom: 15px;
    border: none;
  }
}

.submit-button {
  padding: 11px 25px;
  text-align: center;
  border: 1px solid transparent;
  color: $text-white;
  border-radius: 16px;
  background-color: $brand-primary;
  cursor: pointer;

  &:active {
    border: 1px solid black;
    color: $text-black;
  }
}
</style>
