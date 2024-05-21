<template>
  <div class="car-images">
    <div class="image-container">
      <img :src="selectedImage" alt="Main Car image" class="main-image" />
      <button class="prev-button" @click="prevImage">&#8249;</button>
      <button class="next-button" @click="nextImage">&#8250;</button>
      <div class="dots">
        <span
            v-for="(image, index) in images"
            :key="index"
            class="dot"
            :class="{ active: image === selectedImage }"
            @click="selectImage(image)"
        ></span>
      </div>
      <div class="total-images">{{ images.length }}</div>
    </div>
    <div class="thumbnail-images">
      <img
          v-for="(image, index) in images"
          :key="index"
          :src="image"
          :class="{ selected: image === selectedImage }"
          @click="selectImage(image)"
          alt="Car thumbnail"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'CarImages',
  setup() {
    const images = [
      '/image/car1.png',
      '/image/car2.png',
      '/image/car3.png',
      '/image/car4.png',
      '/image/car5.png'
    ];
    const selectedImage = ref(images[0]);

    const selectImage = (image: string) => {
      selectedImage.value = image;
    };

    const prevImage = () => {
      const index = images.indexOf(selectedImage.value);
      if (index > 0) {
        selectedImage.value = images[index - 1];
      } else {
        selectedImage.value = images[images.length - 1];
      }
    };

    const nextImage = () => {
      const index = images.indexOf(selectedImage.value);
      if (index < images.length - 1) {
        selectedImage.value = images[index + 1];
      } else {
        selectedImage.value = images[0];
      }
    };

    return {
      images,
      selectedImage,
      selectImage,
      prevImage,
      nextImage
    };
  }
});
</script>

<style scoped>
.car-images {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.image-container {
  position: relative;
}

.main-image {
  width: 780px;
  height: 588px;
  object-fit: cover;
}

.thumbnail-images {
  display: flex;
  gap: 10px;
}

.thumbnail-images img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  cursor: pointer;
  border: 2px solid transparent;
}

.thumbnail-images img.selected {
  border-color: #ffffff;
}

.prev-button,
.next-button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: #000000;
  border-radius: 100%;
  align-items: center;
  color: #ffffff;
  font-size: 20px;
  cursor: pointer;
  z-index: 1;
}

.prev-button {
  left: 10px;
}

.next-button {
  right: 10px;
}

.dots {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 5px;
}

.dot {
  width: 10px;
  height: 10px;
  background-color: #ff0000;
  border-radius: 50%;
  cursor: pointer;
}

.dot.active {
  background-color: #007bff;
}

.total-images {
  display: none;
  position: absolute;
  bottom: 10px;
  right: 10px;
  font-size: 14px;
}
</style>
