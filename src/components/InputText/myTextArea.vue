<template>
    <div class="form-group">
      <label :for="id">{{ label }}</label>
      <textarea
        :id="id"
        :placeholder="placeholder"
        v-model="internalValue"
        @input="emitInput"
        :style="{ height: height + 'px' }"
      ></textarea>
    </div>
  </template>
  
  <script>
  export default {
    name: 'TextAreaInput',
    props: {
      id: { type: String, required: true },
      label: { type: String, default: 'Digite:' },
      placeholder: { type: String, default: '' },
      modelValue: { type: String, default: '' },
      height: { type: [String, Number], default: 100 }, // altura padrão para textarea
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
    margin-bottom: 40px;
    font-size: 1rem;
    color: #000000;
  }
  
  label {
    font-weight: bold;
    margin-bottom: 0;
  }
  
  textarea {
    width: 100%;
    padding: 12px;
    font-size: 1rem;
    border: 3px solid #A1A1A1;
    border-radius: 5px;
    background-color: #fff;
    color: #000000;
    resize: none;
    box-sizing: border-box;
  }
  </style>
  