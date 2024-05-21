<template>
  <div class="description-text">
    <h2>Описание</h2>
    <div class="plate-number">
      <div class="plate-border">
        <div class="vector-flag">
      <div class="vectors">
        <svg class="vector-1" xmlns="http://www.w3.org/2000/svg" width="10" height="3.61" viewBox="0 0 10 3.61">
          <rect width="10" height="3.61" fill="#005BBB"/>
        </svg>
        <svg class="vector-2" xmlns="http://www.w3.org/2000/svg" width="10" height="3.61" viewBox="0 0 10 3.61">
          <rect width="10" height="3.61" fill="#FFD500"/>
        </svg>
      </div>
      <span class="ua-text">UA</span>
        </div>
      <span class="plate-number-text">АН 1111 НА</span>
      </div>
    </div>
    <p class="description" v-html="displayedDescription"></p>
    <button @click="toggleDescription">
      {{ showMoreText }}
      <svg v-if="!isFullDescriptionVisible" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-chevron-down" viewBox="0 0 16 16">
        <path fill-rule="evenodd" d="M1.646 4.646a.5.5 0 0 1 .708 0L8 10.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z"/>
      </svg>
      <svg v-else xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-chevron-up" viewBox="0 0 16 16">
        <path fill-rule="evenodd" d="M1.646 11.354a.5.5 0 0 1 .708 0L8 6.707l5.646 4.647a.5.5 0 0 1-.708.708l-6-6a.5.5 0 0 1-.708 0l-6 6a.5.5 0 0 1 0 .708z"/>
      </svg>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'DescriptionText',
  setup() {
    const defaultDescription = "Продажа Ford Edge 2016 года. Автомобиль куплен для личного использования. Почти в полной комплектации Sport Двигатель 2.7 Бензин 312 л.с. АКПП – полный привод AWD. Зимняя резина. Новая тормозная система. Android Auto. Подогрев всех сидений.";
    const additionalText = " Продажа Ford Edge 2016 года. Автомобиль куплен для личного использования. Почти в полной комплектации Sport Двигатель 2.7 Бензин 312 л.с. АКПП – полный привод AWD. Зимняя резина. Новая тормозная система. Android Auto. Подогрев всех сидений.";

    const isFullDescriptionVisible = ref(false);
    const displayedDescription = ref(defaultDescription);
    const showMoreText = ref('Показать больше');

    const toggleDescription = () => {
      isFullDescriptionVisible.value = !isFullDescriptionVisible.value;
      displayedDescription.value = isFullDescriptionVisible.value
          ? defaultDescription + additionalText
          : defaultDescription;
      showMoreText.value = isFullDescriptionVisible.value ? 'Показать меньше' : 'Показать больше';
    };

    return {
      displayedDescription,
      toggleDescription,
      showMoreText,
      isFullDescriptionVisible
    };
  }
});
</script>

<style scoped>
.description-text {
  width: 1180px;
  height: auto;
  padding: 10px;
  margin: 0 auto;

}

h2 {
  margin-bottom: 10px;
}

.plate-number {
  width: 100px;
  height: 24px;
  display: flex;
  align-items: center;
  margin-bottom: 10px;
  border-radius: 4px;
  border: 1px solid #07499D;
  font-size: 14px;
  font-family: "Proxima Nova";
  font-weight: 400;
}
.plate-border {

  width: 100px;
  display: flex;

}

.vector-flag {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: blue;
}
.vectors {
  display: flex;
  flex-direction: column;
  gap: 1px;
  margin-right: 8px;
}

.vector-1 {
  width: 10px;
  height: 3.61px;
  top: 1.39px;
  fill: #005BBB;
}

.vector-2 {
  width: 10px;
  height: 3.61px;
  top: 5px;
  fill: #FFD500;
}

.ua-text {
  color: #000000;
  margin-right: 8px;
  display: flex;
  font-size: 14px;
}

.plate-number-text {
  color: #000000;
  display: flex;
  align-items: center;
  margin-left: 10px;
}

.description {
  width: 100%;
  border-radius: 4px;
  border: 1px solid #000000;
  padding: 8px;
}

button {
  background-color: transparent;
  border: none;
  cursor: pointer;
  color: #000000;
  margin-top: 10px;
  display: flex;
  align-items: center;
  gap: 5px;
  margin: 0 auto;
}
button svg {
  color: red;
}
</style>
