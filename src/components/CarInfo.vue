<template>
  <div class="car-info">
    <h1>{{ car.name }}</h1>
    <div class="city-code">
      <p class="code">Код товара: {{ car.code }}</p>
      <p>{{ car.location }}</p>
    </div>
    <div class="price-selection"> <strong>Цена</strong>
      <button :class="{ selected: selectedCurrency === 'ГРН' }" @click="selectedCurrency = 'ГРН'">ГРН</button>
      <button :class="{ selected: selectedCurrency === 'USD' }" @click="selectedCurrency = 'USD'">USD</button>
      <button :class="{ selected: selectedCurrency === 'EUR' }" @click="selectedCurrency = 'EUR'">EUR</button>
      <button :class="{ selected: selectedCurrency === 'crypto' }" @click="selectedCurrency = 'crypto'">CRYPTO</button>
    </div>
    <p class="price">{{ convertedPrice }}</p>
    <p class="credit-price">{{ car.creditPrice }}</p>
    <p class="credit-description">{{ car.creditDescription }}</p>
    <div class="tags">
      <span v-for="(tag, index) in car.tags" :key="index" class="tag">{{ tag }}</span>
    </div>
    <p class="publik">Опубликовано {{ car.publicationDate }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType, ref, computed } from 'vue';

export default defineComponent({
  name: 'CarInfo',
  props: {
    car: {
      type: Object as PropType<{
        name: string;
        code: string;
        location: string;
        price: number;
        creditPrice: string;
        details: string[];
        creditDescription: string;
        tags: string[];
        publicationDate: string;
      }>,
      required: true
    }
  },
  setup(props) {
    const selectedCurrency = ref('USD');

    const conversionRates = {
      ГРН: 41, // example conversion rate to UAH
      USD: 1,
      EUR: 0.85,
      crypto: 0.000034 // example conversion rate to Bitcoin
    };

    const convertedPrice = computed(() => {
      const rate = conversionRates[selectedCurrency.value as keyof typeof conversionRates];
      const formattedPrice = (props.car.price * rate).toLocaleString('ru-RU', { minimumFractionDigits: 0, maximumFractionDigits: 0 });
      return `${formattedPrice} ${selectedCurrency.value}`;
    });

    return {
      selectedCurrency,
      convertedPrice
    };
  }
});
</script>

<style scoped>
.car-info {
  display: flex;
  flex-direction: column;
}
.car-info h1 {
  font-family: Proxima Nova Condensed ;
  font-weight: 700;
  font-size: 24px;
  line-height: 29.23px;
  text-transform: uppercase;
}
.code {
  font-family: "Proxima Nova";
  font-size: 14px;
  color: #16161699;
}
.price-selection {
  display: flex;
  align-items: center;
  gap: 5px;
}
.price-selection button {
  padding: 5px 10px;
  font-size: 16px;
  background-color: transparent;
  border: none;
  cursor: pointer;
}
.price-selection button.selected {
  color: red;
  text-decoration: underline;
}
.price {
  color: #000;
  margin: 0;
  padding: 5px;
  font-weight: bold;
  font-weight: 700;
  font-size: 24px;
}
.city-code {
  display: flex;
  justify-content: space-between;
}
.credit-description {
  font-size: 14px;
  color: grey;
}
.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 5px;
  margin-top: 10px;
}
.tag {
  padding: 5px 10px;
  font-size: 16px;
  width: auto;
  border-radius: 5px;
  border: 1px solid red;
}
.publik {
  font-family: "Proxima Nova";
  font-weight: 400;
  font-size: 14px;
  color: #16161699;
}
</style>
