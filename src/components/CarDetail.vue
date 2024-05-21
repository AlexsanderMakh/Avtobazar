<template>
  <div class="car-detail">
    <div class="car-desk">
    <CarImages />
    <CarDescription/>
    </div>
    <div class="car-info-actions">
      <CarInfo :car="car" />
      <CarActions :car="car" />
    </div>
  </div>
  <div class="dsk-txt">
  <DescriptionText/>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import CarImages from './CarImages.vue';
import CarInfo from './CarInfo.vue';
import CarActions from './CarAction.vue';
import CarDescription from "@/components/CarDescription.vue";
import DescriptionText from "@/components/DescriptionText.vue";


export default defineComponent({
  name: 'CarDetails',
  components: {
    DescriptionText,
    CarDescription,
    CarImages,
    CarInfo,
    CarActions,
  },
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
  }
});
</script>

<style scoped>
.car-detail {
  max-width: 1180px;
  display: flex;
  flex-direction: row;
  background-color: #fff;
  width: 100%;
  margin: 0 auto;
  border-radius: 10px;
}

.car-info-actions {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  margin-left: 20px;
}

</style>
