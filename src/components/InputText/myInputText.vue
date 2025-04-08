<template>
    <div class="form-group">
      <label :for="id">{{ label }}</label>
      <input
        :id="id"
        type="text"
        :placeholder="placeholder"
        v-model="internalValue"
        @input="emitInput"
        :style="{ height: height + 'px' }"
      />
    </div>
  </template>
  
  <script>
  export default {
    name: 'TextInput',
    props: {
      id: { type: String, required: true },
      label: { type: String, default: 'Digite:' },
      placeholder: { type: String, default: '' },
      modelValue: { type: String, default: '' },
      height: { type: [String, Number], default: 50 }, // altura como parâmetro
    },
    computed: {
      internalValue: {
        get() {
          return this.modelValue;
        },
        set(value) {
          this.$emit('update:modelValue', value);
        }
      }
    },
    methods: {
      emitInput(event) {
        this.$emit('input', event.target.value);
      }
    }
  };
  </script>
  
  <style scoped>
  .form-group {
    display: flex;
    flex-direction: column;
    gap: 4px;
    margin-bottom: 0px;
    font-size: 1rem;
    color: #000000;
  }
  
  label {
    font-weight: bold;
    margin-bottom: 0;
  }
  
  input {
    width: 100%;
    padding: 8px 12px;
    font-size: 1rem;
    border: 3px solid #A1A1A1;
    border-radius: 5px;
    background-color: #fff;
    color: #000000;
    box-sizing: border-box;
  }
  </style>
  