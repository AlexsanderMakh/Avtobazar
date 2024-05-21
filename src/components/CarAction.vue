<template>
  <div class="car-actions">
    <button class="show-phone-button" @click="showPhone">{{ showPhoneText }}</button>
    <div v-if="phoneVisible" class="phone-number">{{ phone }}</div>

    <h3>Заказать услугу</h3>
    <div class="services-buttons">
      <button class="service-button" @click="testDrive">Тест-драйв</button>
      <button class="service-button" @click="tradeIn">Trade in</button>
      <button class="service-button" @click="onlineView">Онлайн просмотр</button>
      <button class="service-button" @click="delivery">Доставка</button>
    </div>

    <h3>Заказать проверку</h3>
    <div class="check-buttons">
      <button class="check-button" @click="orderCheck('CarVertical')">CarVertical</button>
      <button class="check-button" @click="orderCheck('Autopark.ua')">Autopark.ua</button>
      <button class="full-check-button" @click="orderCheck('Полная проверка авто')">Полная проверка авто</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'CarActions',
  setup() {
    const phone = ref('+38 (050) 123-45-67');
    const phoneVisible = ref(false);
    const showPhoneText = ref('Показать телефон');

    const showPhone = () => {
      phoneVisible.value = !phoneVisible.value;
      showPhoneText.value = phoneVisible.value ? 'Скрыть телефон' : 'Показать телефон';
    };

    const testDrive = () => {
      alert('Тест-драйв заказан');
    };

    const tradeIn = () => {
      alert('Trade in заказан');
    };

    const onlineView = () => {
      alert('Онлайн просмотр заказан');
    };

    const delivery = () => {
      alert('Доставка заказана');
    };

    const orderCheck = (checkType: string) => {
      alert(`${checkType} проверка заказана`);
    };

    return {
      phone,
      phoneVisible,
      showPhoneText,
      showPhone,
      testDrive,
      tradeIn,
      onlineView,
      delivery,
      orderCheck
    };
  }
});
</script>

<style scoped>
.car-actions {
  display: flex;
  flex-direction: column;
}

.show-phone-button {
  background-color: #E73A3F;
  color: white;
  width: 380px;
  height: 40px;
  font-weight: 700;
  border-radius: 4px;
  padding: 0 20px;
  border: none;
  cursor: pointer;
}

.phone-number {
  margin-top: 10px;
  font-weight: 700;
}

.services-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  font-weight: 700;
  width: 380px;
}

.service-button {
  width: 184px;
  height: 40px;
  border: 1px solid #000;
  font-weight: 700;
  border-radius: 4px;
  background-color: #fff;
  cursor: pointer;
}

.check-buttons {
  display: flex;
  flex-wrap: wrap;
  font-weight: 700;
  gap: 10px;
  width: 380px;
}

.check-button {
  width: 184px;
  height: 40px;
  border: 1px solid #000;
  font-weight: 700;
  border-radius: 4px;
  background-color: #fff;
  cursor: pointer;
}

.full-check-button {
  background-color: #E73A3F;
  font-weight: 700;
  color: white;
  width: 380px;
  height: 40px;
  border-radius: 4px;
  padding: 0 20px;
  border: none;
  cursor: pointer;
}
</style>
