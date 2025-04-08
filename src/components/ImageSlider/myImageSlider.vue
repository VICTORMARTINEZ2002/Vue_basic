<template>
  <div class="slider">
    <div class="image-counter">
      Imagem {{ currentIndex + 1 }} de {{ imagePaths.length }}
    </div>
    <img :src="currentImage" alt="Imagem da atividade" class="slider-image" />

    <div class="controls">
      <button @click="prevImage" class="slider-button">‹</button>
      <button @click="nextImage" class="slider-button">›</button>
    </div>

    <div class="play-button-wrapper">
      <MyButton @click="togglePlay">
        {{ isPlaying ? 'Pausar' : 'Reproduzir' }}
      </MyButton>
    </div>

    <div class="thumbnails">
      <div
        class="thumbnail-wrapper"
        v-for="(img, index) in imagePaths"
        :key="index"
      >
        <img
          :src="img"
          :ref="el => thumbnailRefs[index] = el"
          :class="['thumbnail', { active: index === currentIndex }]"
          @click="selectImage(index)"
          alt="Miniatura"
        />
        <span class="thumbnail-number">{{ index + 1 }}</span>
      </div>
    </div>
  </div>
</template>

<script>
import { nextTick } from 'vue';
import MyButton from '../Buttons/MyButton.vue';

export default {
  name: 'MyImageSlider',
  components: {
    MyButton,
  },
  props: {
    imagePaths: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      currentIndex: 0,
      isPlaying: false,
      intervalId: null,
      thumbnailRefs: [],
    };
  },
  computed: {
    currentImage() {
      return this.imagePaths[this.currentIndex];
    },
  },
  watch: {
    currentIndex() {
      nextTick(() => {
        const el = this.thumbnailRefs[this.currentIndex];
        if (el && el.scrollIntoView) {
          el.scrollIntoView({ behavior: 'smooth', inline: 'center', block: 'nearest' });
        }
      });
    },
  },
  methods: {
    nextImage() {
      this.currentIndex = (this.currentIndex + 1) % this.imagePaths.length;
    },
    prevImage() {
      this.currentIndex = (this.currentIndex - 1 + this.imagePaths.length) % this.imagePaths.length;
    },
    selectImage(index) {
      this.currentIndex = index;
    },
    togglePlay() {
      if (this.imagePaths.length <= 1) return;

      if (this.isPlaying) {
        clearInterval(this.intervalId);
        this.intervalId = null;
        this.isPlaying = false;
      } else {
        this.intervalId = setInterval(() => {
          this.nextImage();
        }, 20);
        this.isPlaying = true;
      }
    },
  },
  beforeUnmount() {
    clearInterval(this.intervalId);
  },
};
</script>

<style scoped>
.slider {
  position: relative;
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
  overflow: hidden;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.15);
  background-color: white;
}

.slider-image {
  width: 100%;
  max-height: 500px;
  object-fit: contain;
  display: block;
  background-color: #f5f5f5;
  border-bottom: 1px solid #ccc;
}

.image-counter {
  text-align: center;
  font-size: 1.1rem;
  color: #474747;
  margin-top: 8px;
}

.controls {
  position: absolute;
  top: 50%;
  left: 0;
  right: 0;
  display: flex;
  justify-content: space-between;
  transform: translateY(-50%);
  padding: 0 10px;
  pointer-events: none;
}

.slider-button {
  background-color: rgba(0, 0, 0, 0.5);
  border: none;
  color: white;
  font-size: 2rem;
  padding: 5px 15px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.2s;
  pointer-events: all;
}

.slider-button:hover {
  background-color: rgba(0, 0, 0, 0.7);
}

.thumbnails {
  display: flex;
  flex-wrap: nowrap;
  overflow-x: auto;
  gap: 5px;
  padding: 10px;
  background: #fafafa;
  border-top: 1px solid #ddd;
  justify-content: flex-start;
}

.thumbnail-wrapper {
  flex: 0 0 auto;
  text-align: center;
}

.thumbnail {
  width: 50px;
  height: auto;
  object-fit: cover;
  border: 2px solid transparent;
  border-radius: 5px;
  cursor: pointer;
  transition: border 0.2s;
}

.thumbnail:hover {
  border: 4px solid #000000;
}

.thumbnail.active {
  border: 4px solid #007bff;
}

.thumbnail-number {
  font-size: 1rem;
  color: #000000;
  margin-top: 2px;
  display: block;
}
.play-button-wrapper {
  text-align: center;
  margin: 15px 0 10px;
}
</style>
