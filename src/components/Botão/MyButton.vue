<template>
  <button
    type="button"
    class="my-button"
    :class="{ disabled: disabled }"
    :disabled="disabled"
    @click="togglePlay"
  >
    <span class="icon">
      {{ isPlaying ? '⏸️' : '▶️' }}
    </span>
    <span class="text">
      {{ isPlaying ? 'Pausar' : 'Reproduzir' }}
    </span>
  </button>
</template>

<script>
export default {
  name: 'MyPlayPauseButton',
  props: {
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  emits: ['play', 'pause'],
  data() {
    return {
      isPlaying: false,
    };
  },
  methods: {
    togglePlay() {
      if (this.disabled) return;

      this.isPlaying = !this.isPlaying;

      if (this.isPlaying) {
        this.$emit('play');
      } else {
        this.$emit('pause');
      }
    },
  },
};
</script>

<style scoped>
.my-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 12px 24px;
  font-size: 1rem;
  font-weight: bold;
  min-width: 200px;
  color: #fff;
  background-color: #007bff;
  border: none;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.my-button:hover {
  background-color: #0056b3;
}

.my-button.disabled,
.my-button:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}

.icon {
  font-size: 1.2rem;
}
</style>
