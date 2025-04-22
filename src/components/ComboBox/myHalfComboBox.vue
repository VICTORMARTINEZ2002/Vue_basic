<template>
  <div class="form-group">
    <label :for="id">{{ label }}</label>
    <div class="custom-select-container">
      <div class="custom-select" @click="toggleDropdown">
        <span>{{ selectedLabel || placeholder }}</span>
        <div class="arrow"></div>
      </div>
      <div v-if="dropdownOpen" class="custom-options">
        <div v-if="items.length === 0" class="custom-option" disabled>
          Nenhuma opção disponível
        </div>
        <div v-else v-for="item in items" :key="item.id" class="custom-option" @click="selectItem(item)">
          {{ item.nome }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ComboBox',
  props: {
    id: { type: String, required: true },
    label: { type: String, default: 'Selecione:' },
    placeholder: { type: String, default: ' ' },
    items: { type: Array, required: true },
    modelValue: { type: [String, Number], default: '' },
  },
  data() {
    return {
      dropdownOpen: false,
    };
  },
  computed: {
    selectedLabel() {
      const selectedItem = this.items.find(item => item.id === this.modelValue);
      return selectedItem ? selectedItem.nome : '';
    },
  },
  methods: {
    toggleDropdown() {
      this.dropdownOpen = !this.dropdownOpen;
    },
    selectItem(item) {
      this.$emit('update:modelValue', item.id);
      this.dropdownOpen = false;
    },
  },
};
</script>

<style scoped>
.form-group {
  display: flex;
  flex-direction: column;
  gap: 4px;
  margin-bottom: 40px;
  font-size: 1rem;
  color: #000000;
  width: 50%;
}

label {
  font-weight: bold;
  margin-bottom: 0;
}

.custom-select-container {
  position: relative;
  width: 100%;
}

.custom-select {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 50px;
  padding: 8px 40px 8px 12px;
  font-size: 1rem;
  border: 3px solid #A1A1A1;
  border-radius: 5px;
  cursor: pointer;
  background-color: #fff;
}

.arrow {
  width: 18px;
  height: 18px;
  background-image: url("data:image/svg+xml,%3Csvg fill='black' viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M7 10l5 5 5-5z'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
}

.custom-options {
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  max-height: 200px;
  overflow-y: auto;
  border: 3px solid #A1A1A1;
  border-radius: 5px;
  background-color: #fff;
  z-index: 10;
}

.custom-option {
  padding: 10px;
  cursor: pointer;
}

.custom-option:hover {
  background-color: #f0f0f0;
}

.custom-option[disabled] {
  color: #aaa;
}
</style>
