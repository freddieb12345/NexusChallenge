<template>
  <section class="results-container">
      <ResultCard v-for="result in firstFourItems" :data="result" :key="result.id" />
      <ValueMyCar/>
      <ResultCard v-for="result in remainingItems" :data="result" :key="result.id" />
  </section>
</template>

<script setup lang="ts">
const dummyData = [
  {
    id: 1,
    carYear: "2014 (64)",
    carBrand: "Mercedes-Benz",
    carName: "CLA 250e Coupe Shooting Break",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: null,
    imgPath: "mercedes.jpg",
    usedOrNew: "Used",
    carInformation: {
      miles: "32k",
      engine: "Hybrid",
      gearbox: "Automatic",
      carType: "SUV",
    },
  },
  {
    id: 2,
    carYear: "2020 (20)",
    carBrand: "Peugeot 208",
    carName: "1.2 PureTech 100 GT-Line",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: null,
    imgPath: "peugeot.jpg",
    usedOrNew: "New",
    carInformation: {
      miles: null,
      engine: "Petrol",
      gearbox: "Automatic",
      carType: "Hatchback",
    },
  },
  {
    id: 3,
    carYear: "2019 (19)",
    carBrand: "Renault Zoe",
    carName: "i R135 Rapid Charge ZE50",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: "£20,300",
    imgPath: "renault.jpg",
    usedOrNew: "Used",
    carInformation: {
      miles: "325",
      engine: "EV",
      gearbox: "Automatic",
      carType: "Hatchback",
    },
  },
  {
    id: 4,
    carYear: "2014 (64)",
    carBrand: "Mercedes-Benz",
    carName: "CLA 250e Coupe Shooting Break",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: null,
    imgPath: "mercedes.jpg",
    usedOrNew: "Used",
    carInformation: {
      miles: "32k",
      engine: "Hybrid",
      gearbox: "Automatic",
      carType: "SUV",
    },
  },
  {
    id: 5,
    carYear: "2020 (20)",
    carBrand: "Peugeot 208",
    carName: "1.2 PureTech 100 GT-Line",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: null,
    imgPath: "peugeot.jpg",
    usedOrNew: "New",
    carInformation: {
      miles: null,
      engine: "Petrol",
      gearbox: "Automatic",
      carType: "Hatchback",
    },
  },
  {
    id: 6,
    carYear: "2019 (19)",
    carBrand: "Renault Zoe",
    carName: "i R135 Rapid Charge ZE50",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: "£20,300",
    imgPath: "renault.jpg",
    usedOrNew: "Used",
    carInformation: {
      miles: "325",
      engine: "EV",
      gearbox: "Automatic",
      carType: "Hatchback",
    },
  },
  {
    id: 7,
    carYear: "2014 (64)",
    carBrand: "Mercedes-Benz",
    carName: "CLA 250e Coupe Shooting Break",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: null,
    imgPath: "mercedes.jpg",
    usedOrNew: "Used",
    carInformation: {
      miles: "32k",
      engine: "Hybrid",
      gearbox: "Automatic",
      carType: "SUV",
    },
  },
  {
    id: 8,
    carYear: "2020 (20)",
    carBrand: "Peugeot 208",
    carName: "1.2 PureTech 100 GT-Line",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: null,
    imgPath: "peugeot.jpg",
    usedOrNew: "New",
    carInformation: {
      miles: null,
      engine: "Petrol",
      gearbox: "Automatic",
      carType: "Hatchback",
    },
  },
  {
    id: 9,
    carYear: "2019 (19)",
    carBrand: "Renault Zoe",
    carName: "i R135 Rapid Charge ZE50",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: "£20,300",
    imgPath: "renault.jpg",
    usedOrNew: "Used",
    carInformation: {
      miles: "325",
      engine: "EV",
      gearbox: "Automatic",
      carType: "Hatchback",
    },
  },
  {
    id: 10,
    carYear: "2014 (64)",
    carBrand: "Mercedes-Benz",
    carName: "CLA 250e Coupe Shooting Break",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: null,
    imgPath: "mercedes.jpg",
    usedOrNew: "Used",
    carInformation: {
      miles: "32k",
      engine: "Hybrid",
      gearbox: "Automatic",
      carType: "SUV",
    },
  },
  {
    id: 11,
    carYear: "2020 (20)",
    carBrand: "Peugeot 208",
    carName: "1.2 PureTech 100 GT-Line",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: null,
    imgPath: "peugeot.jpg",
    usedOrNew: "New",
    carInformation: {
      miles: null,
      engine: "Petrol",
      gearbox: "Automatic",
      carType: "Hatchback",
    },
  },
  {
    id: 12,
    carYear: "2019 (19)",
    carBrand: "Renault Zoe",
    carName: "i R135 Rapid Charge ZE50",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: "£20,300",
    imgPath: "renault.jpg",
    usedOrNew: "Used",
    carInformation: {
      miles: "325",
      engine: "EV",
      gearbox: "Automatic",
      carType: "Hatchback",
    },
  },
  {
    id: 14,
    carYear: "2014 (64)",
    carBrand: "Mercedes-Benz",
    carName: "CLA 250e Coupe Shooting Break",
    monthlyPayment: "£550.90",
    price: "£23,300",
    discountedPrice: null,
    imgPath: "mercedes.jpg",
    usedOrNew: "Used",
    carInformation: {
      miles: "32k",
      engine: "Hybrid",
      gearbox: "Automatic",
      carType: "SUV",
    },
  },
];

const firstFourItems = dummyData.slice(0, 4);
const remainingItems = dummyData.slice(4);
</script>

<style lang="scss" scoped>
.results-container {
  position: relative;
  padding-right: 15px;
  width: 100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 15px;
  @media (max-width: 642px) {
    padding: 0px;
    display: flex;
    flex-wrap: wrap;
  
  }
  @media (min-width: 642px) and (max-width: 1068px) {
    grid-template-columns: repeat(2, 1fr);
  }

}
</style>
