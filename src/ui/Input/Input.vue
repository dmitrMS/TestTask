<template>
    <div class="input-container">
      <!-- Классы состояний -->
      <div
        :class="['form-group', 
          { 'input-error': hasError, 'input-success': isValid, 'hover-input': isHovering }
        ]"
        @mouseenter="isHovering = true"
        @mouseleave="isHovering = false"
      >
        <div class="input-wrapper">
          <input
            v-model="fullname"
            @input="validateInput"
            @focus="onFocus"
            @blur="onBlur"
            :class="inputClass"
            id="fullname"
            type="text"
            :placeholder="this.parameter + '*'"
          />
          <!-- Ошибка -->
          <span v-if="hasError" class="error-icon">✕</span>
          <!-- Success icon -->
          <span v-if="isValid" class="success-icon">✔</span>
        </div>
        <!-- Сообщение ошибки -->
        <p v-if="hasError" class="error-message">Пожалуйста, введите корректное значение</p>
      </div>
    </div>
  </template>
  
  <script>
  import "./Input.css";

  export default {
    data() {
      return {
        fullname: '',
        hasError: false,
        isValid: false,
        isFocused: false,
        isHovering: false,
      };
    },
    props: {
        parameter: String
    },
    computed: {
      inputClass() {
        return {
          'focus-input': this.isFocused && !this.hasError && !this.isValid,
          'error-input': this.hasError,
          'success-input': this.isValid,
        };
      },
    },
    methods: {
      validateInput() {
        // Валидация
        if (this.fullname.length > 5) {
          this.hasError = false;
          this.isValid = true;
        } else {
          this.hasError = true;
          this.isValid = false;
        }
      },
      onFocus() {
        this.isFocused = true;
      },
      onBlur() {
        this.isFocused = false;
        this.validateInput();
      },
    },
  };
  </script>