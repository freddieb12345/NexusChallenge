<template>
  <article class="result-card">
    <figure>
      <ResultImageCarousel
        :imagePaths="[
          data.imgPath,
          data.imgPath,
          data.imgPath,
          data.imgPath,
          data.imgPath,
          data.imgPath,
          data.imgPath,
          data.imgPath,
        ]"
      />
      <section class="figure-captions">
        <figcaption class="new-or-used-caption button-text">
          {{ data.usedOrNew }}
        </figcaption>
        <ul class="car-information-captions caption-text">
          <li v-if="data.carInformation.miles" class="car-information-caption">
            {{ data.carInformation.miles }} Miles
          </li>
          <li class="car-information-caption">
            {{ data.carInformation.engine }}
          </li>
          <li class="car-information-caption">
            {{ data.carInformation.gearbox }}
          </li>
          <li class="car-information-caption">
            {{ data.carInformation.carType }}
          </li>
        </ul>
      </section>
    </figure>
    <section class="card-description">
      <button class="favorite-button" @click="toggleFavorite">
        <NuxtImg
          v-if="!favorited"
          alt="Favorite Button"
          class="favorite-image"
          src="/img/Favorite.svg"
          loading="lazy"
        />
        <NuxtImg
          v-else
          alt="Unfavorite Button"
          class="favorite-image"
          src="/img/FavoriteSelected.svg"
          loading="lazy"
        />
      </button>
      <button class="view-car-button button-text">View</button>
      <h3 class="card-header paragraph-text">
        <span>{{ data.carYear }} {{ data.carBrand }}</span>
      </h3>
      <p class="car-name caption-text">
        {{ data.carName }}
      </p>
      <h4 class="car-monthly-payment heading-4">
        {{ data.monthlyPayment }}<span class="caption-text">/mo (PCP)</span>
      </h4>
      <div class="car-price caption-text">
        <p v-if="!data.discountedPrice">{{ data.price }}</p>
        <p v-else class="new-price">
          {{ data.discountedPrice }}
          <span class="old-price">{{ data.price }}</span>
        </p>
        <button class="calculate-finance-button caption-text">
          Calculate finance
        </button>
      </div>
    </section>
  </article>
  <article class="result-card-mobile">
    <ResultImageCarousel
      :imagePaths="[
        data.imgPath,
        data.imgPath,
        data.imgPath,
        data.imgPath,
        data.imgPath,
        data.imgPath,
        data.imgPath,
        data.imgPath,
      ]"
    />
    <section class="card-description">
      <p class="new-or-used-caption-mobile caption-text">
        {{ data.usedOrNew }}
      </p>
      <button class="favorite-button" @click="toggleFavorite">
        <NuxtImg
          v-if="!favorited"
          alt="Favorite Button"
          class="favorite-image"
          src="/img/Favorite.svg"
          loading="lazy"
        />
        <NuxtImg
          v-else
          alt="Unfavorite Button"
          class="favorite-image"
          src="/img/FavoriteSelected.svg"
          loading="lazy"
        />
      </button>
      <h3 class="card-header paragraph-text">
        <span>{{ data.carYear }} {{ data.carBrand }}</span>
      </h3>
      <p class="car-name caption-text">
        {{ data.carName }}
      </p>

      <section class="car-information-section-mobile">
        <ul class="car-information-captions-mobile caption-text">
          <li v-if="data.carInformation.miles">
            {{ data.carInformation.miles }} Miles |&nbsp;
          </li>
          <li>{{ data.carInformation.engine }} |&nbsp;</li>
          <li>{{ data.carInformation.gearbox }} |&nbsp;</li>
          <li>
            {{ data.carInformation.carType }}
          </li>
        </ul>
        <div class="car-price caption-text">
          <h4 class="car-monthly-payment paragraph-text">
            {{ data.monthlyPayment }}<span class="caption-text">/mo (PCP)</span>
          </h4>
          <p v-if="!data.discountedPrice">{{ data.price }}</p>
          <p v-else class="new-price">
            {{ data.discountedPrice }}
            <span class="old-price">{{ data.price }}</span>
          </p>
        </div>
      </section>
    </section>
  </article>
</template>

<script setup lang="ts">
import { defineProps } from "vue";
const favorited = ref(false);

const toggleFavorite = () => {
  favorited.value = !favorited.value;
};

interface CarData {
  carYear: string;
  carBrand: string;
  carName: string;
  monthlyPayment: string;
  price: string;
  discountedPrice: string | null;
  imgPath: string;
  usedOrNew: string;
  carInformation: {
    miles: string | null;
    engine: string;
    gearbox: string;
    carType: string;
  };
}

const props = withDefaults(
  defineProps<{
    data: CarData;
  }>(),
  {}
);

</script>

<style lang="scss" scoped>
@import "~/assets/scss/variables.scss";

.result-card {
  overflow: hidden;
  width: calc((100% - 30px) / 3);
  height: 364px;
  flex-shrink: 0;
  border-radius: 16px;
  box-shadow: 0px 6px 25px 0px rgba(0, 0, 0, 0.15);

  .view-car-button {
    opacity: 0;
    visibility: hidden;
    transition: opacity 0.3s, visibility 0.3s;
    position: absolute;
    right: 10px;
    bottom: 10px;
    border-radius: 16px;
    color: $text-white;
    background-color: $brand-primary;
    padding: 12px 25px;
    border: none;
    cursor: pointer;
  }

  .view-car-button:active {
    color: $text-black;
    border: 1px solid black;
  }

  &:hover {
    .view-car-button {
      opacity: 1;
      visibility: visible;
    }
  }

  @media (min-width: 642px) and (max-width: 1068px) {
    width: calc((100% - 15px) / 2);
  }

  @media (max-width: 642px) {
    display: none;
  }
}
.result-card-mobile {
  width: 100%;
  padding: 0 13px;

  @media (min-width: 643px) {
    display: none;
  }
}

figure {
  position: relative;
  margin: 0px;
  height: 250px;
}

.figure-captions {
  position: absolute;
  pointer-events: none;
  top: 0;
  z-index: 10;
  padding: 10px;
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.new-or-used-caption,
.new-or-used-caption-mobile {
  background-color: $framework-dark-1;
  padding: 1px 10px;
  color: $text-white;
  border-radius: 8px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  width: fit-content;

  &.new-or-used-caption-mobile {
    position: absolute;
    right: 40px;
  }
}

.car-information-captions {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
}

.car-information-caption {
  background-color: $framework-dark-1;
  padding: 4px 10px;
  color: white;
  border-radius: 8px;
  border: 1px solid rgba(255, 255, 255, 0.2);
  width: fit-content;
}

.car-information-captions-mobile {
  width: 50%;
  color: $text-gray;
  display: flex;
  flex-wrap: wrap;
}

.car-information-section-mobile {
  display: flex;
}

.card-description {
  padding: 10px;
  position: relative;
  @media (max-width: 642px) {
    padding-bottom: 0px;
  }
}

.car-monthly-payment {
  color: $text-black;
  font-weight: bold;
  @media (max-width: 642px) {
    font-size: 14px;
    line-height: 21px;
  }
}

.card-header {
  display: flex;
  justify-content: space-between;
  color: $text-black;
  align-self: stretch;
  @media (max-width: 642px) {
    font-size: 14px;
    line-height: 21px;
  }
}

.car-name {
  color: $text-gray;
  margin-bottom: 10px;
}

.old-price {
  text-decoration: line-through;
  color: $text-gray;
}

.new-price {
  color: $traffic-light-red;
}

.car-price {
  display: flex;
  @media (max-width: 642px) {
    width: 50%;
    flex-direction: column;
  }
}

.calculate-finance-button {
  color: $brand-primary;
  background-color: transparent;
  cursor: pointer;
  border: none;
}

.favorite-image {
  width: 24px;
  height: 24px;
}

.favorite-button {
  padding: 0;
  background-color: transparent;
  outline: none;
  border: none;
  cursor: pointer;
  position: absolute;
  right: 10px;
}
</style>
