<template>
  <button
    class="action-button"
    :class="variant"
    :disabled="disabled"
    @click="$emit('click')"
  >
    <span v-if="icon" class="icon">{{ icon }}</span>
    {{ label }}
  </button>
</template>

<script>
export default {
  name: 'MyActionButton',
  props: {
    label: {
      type: String,
      required: true,
    },
    icon: {
      type: String,
      default: '',
    },
    variant: {
      type: String,
      default: 'primary', // 'primary', 'danger', 'secondary', 'cancel'
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style scoped>
.action-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  width: 100%;
  max-width: 45%;
  padding: 10px 20px;
  font-size: 1rem;
  font-weight: bold;
  border: 5px solid;
  cursor: pointer;
  transition: background-color 0.2s ease, color 0.2s ease;
  box-sizing: border-box;
}

.action-button.primary {
  background-color: #14637F;
  border-color: #14637F;
  color: #ffffff;
}

.action-button.cancel {
  background-color: transparent;
  border-color: #14637F;
  color: #14637F;
}
.action-button.cancel:hover {
  background-color: #14627f00;
  border-color: #14637F;
}

.action-button:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}
</style>
