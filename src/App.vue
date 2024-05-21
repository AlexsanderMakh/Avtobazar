<template>
  <div id="app">
    <CarDetails :car="car" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import CarDetails from './components/CarDetail.vue';

export default defineComponent({
  name: 'App',
  components: {
    CarDetails
  },
  setup() {
    const car = ref({
      name: 'Ford Edge 2016',
      code: '40845',
      location: 'Львов',
      price: 62490, // price in USD
      creditPrice: 'от 511$/мес',
      details: ['ГРН', 'USD', 'EUR', 'crypto'],
      creditDescription: '*Ежемесячный платеж носит информационный характер и может меняться на момент получения детального расчета. *Возможна оплата криптовалютой',
      tags: ['Все авто', 'Официальное авто', 'Авто с Европы'],
      publicationDate: '14.12.2023'
    });

    return { car };
  }
});
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
*{
  font-family: Proxima Nova Condensed;
}
</style>