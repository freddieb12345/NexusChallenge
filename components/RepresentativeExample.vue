<template>
  <section class="representative-example">
    <article>
      <p class="paragraph-text">
        <span class="">Representative example:</span>Borrowing £11,790.00 over 4
        years with a representative APR of 7.9 %, an annual interest rate of
        4.08 % (Fixed) and a deposit of £500.00, the amount payable would be
        £273.59 per month, with a total cost of credit of £1,843.32 and a total
        amount payable of £13,633.32.
      </p>
      <button @click="toggleBreakdown">
        Show breakdown
        <NuxtImg
          alt="Toggle Breakdown"
          class="dropdown-img"
          :src="`/img/WhiteChevronDown.svg`"
          loading="lazy"
          width="24px"
        />
      </button>
    </article>
    <section
      class="breakdown"
      :class="{ 'breakdown-visible': isBreakdownVisible }"
    >
      <div class="breakdown-buttons">
        <button
          :class="{ selected: selectedButton === 'Personal Contract Purchase' }"
          class="paragraph-text"
          @click="selectButton('Personal Contract Purchase')"
        >
          Personal Contract Purchase
        </button>
        <button
          :class="{ selected: selectedButton === 'Hire Purchase' }"
          class="paragraph-text"
          @click="selectButton('Hire Purchase')"
        >
          Hire Purchase
        </button>
      </div>
      <ul>
        <li v-for="info in dummyBreakdownInfo" class="breakdown-info">
          <h3 class="paragraph-text">{{ info.name }}</h3>
          <p class="heading-4">{{ info.value }}</p>
        </li>
      </ul>
    </section>
  </section>
</template>

<script setup lang="ts">
const isBreakdownVisible = ref(false);
const dummyBreakdownInfo = [
  {
    name: "48 Monthly payments",
    value: "£157.25",
  },
  {
    name: "Cash price",
    value: "£9,998.00",
  },
  {
    name: "Customer deposit",
    value: "£250.00",
  },
  {
    name: "Amount of credit",
    value: "£11,980.75",
  },
  {
    name: "APR",
    value: "7.9%",
  },
  {
    name: "Term",
    value: "48 months",
  },
  {
    name: "Total amount payable",
    value: "£12,163.72",
  },
  {
    name: "Rate of interest (fixed)",
    value: "4.08% PA",
  },
  {
    name: "Annual mileage",
    value: "8,000",
  },
  {
    name: "Optional final payment",
    value: "£3,888.04",
  },
];

const selectedButton = ref("Personal Contract Purchase");

const selectButton = (buttonName: string) => {
  selectedButton.value = buttonName;
  console.log(selectedButton.value);
};

const toggleBreakdown = () => {
  isBreakdownVisible.value = !isBreakdownVisible.value;
};
</script>

<style lang="scss">
@import "~/assets/scss/variables.scss";
.representative-example {
  display: flex;
  flex-direction: column;
  margin: 15px 15px 30px 15px;
  width: calc(100% - 30px);
  border-radius: 16px;
  border: 1px solid $framework-borders;
  background-color: $framework-light;
  padding: 15px;
  article {
    display: flex;
    @media (max-width: 1068px) {
      flex-direction: column;
    }
    button {
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: space-between;
      text-align: left;
      background-color: white;
      border: none;
      border-radius: 16px;
      flex-grow: 1;
      width: 200px;
      padding: 24px 13px;
      height: fit-content;
      @media (max-width: 1068px) {
        margin-top: 15px;
        width: 100%;
      }
    }
    p {
      width: 75%;
      margin-right: 15px;
      @media (max-width: 1068px) {
        width: 100%;
      }
      span {
        font-weight: 700 !important;
      }
    }
  }
}

.dropdown-img {
  background-color: $framework-borders;
  padding: 8px;
  border-radius: 8px;
  margin-left: 30px;
}

.breakdown {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.5s ease-in-out;
}

.breakdown-buttons {
  width: 100%;
  margin-top: 15px;
  display: flex;
  button {
    width: 50%;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: transparent;
    padding: 8px 0;
    border-color: transparent;
  }
  .selected {
    border-bottom: 2px solid $brand-primary !important; /* Change to your preferred color and size */
  }
}

.breakdown-visible {
  max-height: 1000px;
}

ul {
  display: flex;
  flex-wrap: wrap;
  gap: 15px;
}

.breakdown-info {
  width: calc((100% - 60px) / 5);
  background-color: white;
  border-radius: 16px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 10px;
  margin-top: 15px;
  text-align: center;
  h3 {
    margin-bottom: 5px;
  }
  
  @media (max-width: 642px) {
    width: calc((100% - 15px) / 2);
  }
  @media (min-width: 642px) and (max-width: 1068px) {
    width: calc((100% - 30px) / 3);
  }
}
</style>
