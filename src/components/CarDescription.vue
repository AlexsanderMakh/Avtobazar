<template>
  <div class="car-description">
    <div class="car-stats">
      <div class="stat-item">
        <svg><!-- SVG для пробега --></svg>
        <span class="stat-label">Пробег:</span>
        <span class="stat-value">180 000 км</span>
      </div>
      <div class="stat-item">
        <svg><!-- SVG для объема двигателя --></svg>
        <span class="stat-label">Объем двигателя:</span>
        <span class="stat-value">2,7 л</span>
      </div>
      <div class="stat-item">
        <svg><!-- SVG для привода --></svg>
        <span class="stat-label">Привод:</span>
        <span class="stat-value">Полный</span>
      </div>
      <div class="stat-item">
        <svg><!-- SVG для лошадиных сил --></svg>
        <span class="stat-label">Лошадиные силы:</span>
        <span class="stat-value">15</span>
      </div>
    </div>
    <div class="car-details">
      <div class="detail-item">
        <svg><!-- SVG для топлива --></svg>
        <span class="detail-label">Топливо:</span>
        <span class="detail-value">Бензин</span>
      </div>
      <div class="detail-item">
        <svg><!-- SVG для трансмиссии --></svg>
        <span class="detail-label">Трансмиссия:</span>
        <span class="detail-value">Автомат</span>
      </div>
      <div class="detail-item">
        <svg><!-- SVG для расхода топлива --></svg>
        <span class="detail-label">Расход:</span>
        <span class="detail-value">15л/100км</span>
      </div>
      <div class="detail-item">
        <svg><!-- SVG для ДТП --></svg>
        <span class="detail-label">ДТП:</span>
        <span class="detail-value">Без ДТП, не бито, не крашено</span>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'CarDescription'
});
</script>

<style scoped>
.car-description {
  display: flex;
  flex-direction: row;
  gap: 20px;
  margin-top: 20px;
}

.car-stats, .car-details {
  display: flex;
  flex-direction: column;
  gap: 10px;
  border: 1px solid #afafaf;
  border-radius: 10px;
  padding: 5px;
}

.stat-item, .detail-item {
  display: flex;
  align-items: center;
  gap: 10px;
  width: 360px;

}

.stat-label, .detail-label {
  flex: 1;

  text-align: left;
}

.stat-value, .detail-value {
  flex: 1;
  text-align: right;
}
.detail-value :last-child {
  width: auto;
}

svg {
  width: 24px;
  height: 24px;
}
</style>
