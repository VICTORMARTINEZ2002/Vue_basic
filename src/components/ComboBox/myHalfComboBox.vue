<template>
    <div class="form-group">
      <label :for="id">{{ label }}</label>
      <select :id="id" v-model="selectedValue" @change="emitChange" :disabled="items.length === 0">
        <option v-if="items.length === 0" disabled value="">
          Nenhuma opção disponível
        </option>
        <option v-else v-for="item in items" :key="item.id" :value="item.id">
          {{ item.nome }}
        </option>
      </select>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ComboBox',
    props: {
      id: { type: String, required: true },
      label: { type: String, default: 'Selecione:' },
      placeholder: { type: String, default: 'Placeholder' },
      items: { type: Array, required: true },
      modelValue: { type: [String, Number], default: '' },
    },
    computed: {
      selectedValue: {
        get() {
          return this.modelValue;
        },
        set(value) {
          this.$emit('update:modelValue', value);
        },
      },
    },
    methods: {
      emitChange(event) {
        this.$emit('change', event.target.value);
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
    width: 50%; /* Ocupa metade do contêiner pai */
  }
  
  label {
    font-weight: bold;
    margin-bottom: 0;
  }
  
  select {
    width: 100%;
    height: 50px;
    padding: 8px 40px 8px 12px;
    font-size: 1rem;
    border: 3px solid #A1A1A1;
    border-radius: 5px;
    appearance: none;
    background-color: #fff;
    background-image: url("data:image/svg+xml,%3Csvg fill='black' viewBox='0 0 24 24' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M7 10l5 5 5-5z'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-position: right 12px center;
    background-size: 18px;
    cursor: pointer;
  }
  </style>
  