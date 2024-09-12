<script setup>
import { ref, computed } from "vue";

const price = ref(1000);
const profit = ref(2);
const stoploss = ref(5);
const longProfitPrice = computed(() => {
  return price.value * (1 + profit.value / 100);
});
const longStoplossPrice = computed(() => {
  return price.value * (1 - stoploss.value / 100);
});
const shortProfitPrice = computed(() => {
  return price.value * (1 - profit.value / 100);
});
const shortStoplossPrice = computed(() => {
  return price.value * (1 + stoploss.value / 100);
});
</script>

<template>
  <div class="max-w-xl mx-auto p-4 sm:rounded-md sm:border my-4">
    <h1 class="text-2xl text-gray-900 font-semibold text-center">
      Position Size Calculator
    </h1>
    <div class="grid grid-rows-3 gap-4 mt-4">
      <div>
        <label
          for="price"
          class="block text-sm font-medium leading-6 text-gray-900"
          >Price</label
        >
        <input
          type="number"
          name="price"
          id="price"
          v-model="price"
          class="block w-full rounded-md border-0 py-2 px-3 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        />
      </div>
      <div>
        <label
          for="profit"
          class="block text-sm font-medium leading-6 text-gray-900"
          >Profit %</label
        >
        <input
          type="number"
          name="profit"
          id="profit"
          v-model="profit"
          class="block w-full rounded-md border-0 py-2 px-3 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        />
      </div>
      <div>
        <label
          for="stoploss"
          class="block text-sm font-medium leading-6 text-gray-900"
          >Stoploss %</label
        >
        <input
          type="number"
          name="stoploss"
          id="stoploss"
          v-model="stoploss"
          class="block w-full rounded-md border-0 py-2 px-3 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
        />
      </div>
    </div>

    <div class="mt-4">
      <h1 class="text-xl text-gray-900 font-semibold">Result</h1>
      <div class="mt-4">
        <h2 class="text-base font-semibold">Long</h2>
        <div class="flex mt-1 justify-between">
          <p class="text-sm text-gray-600">Profit Price</p>
          <p class="text-sm text-green-600 font-semibold">
            {{ parseFloat(longProfitPrice.toFixed(8)) }}
          </p>
        </div>
        <div class="flex mt-1 justify-between">
          <p class="text-sm text-gray-600">Stoploss Price</p>
          <p class="text-sm text-red-600 font-semibold">
            {{ parseFloat(longStoplossPrice.toFixed(8)) }}
          </p>
        </div>
      </div>
      <div class="mt-4">
        <h2 class="text-base font-semibold">Short</h2>
        <div class="flex mt-1 justify-between">
          <p class="text-sm text-gray-600">Profit Price</p>
          <p class="text-sm text-green-600 font-semibold">
            {{ parseFloat(shortProfitPrice.toFixed(8)) }}
          </p>
        </div>
        <div class="flex mt-1 justify-between">
          <p class="text-sm text-gray-600">Stoploss Price</p>
          <p class="text-sm text-red-600 font-semibold">
            {{ parseFloat(shortStoplossPrice.toFixed(8)) }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type="number"] {
  -moz-appearance: textfield;
}
</style>
