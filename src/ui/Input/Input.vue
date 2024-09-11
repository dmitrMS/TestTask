<template>
    <div class="input-container">
      <!-- Input field with dynamic classes for different states -->
      <div
        :class="['form-group', 
          { 'input-error': hasError, 'input-success': isValid, 'hover-input': isHovering }
        ]"
        @mouseenter="isHovering = true"
        @mouseleave="isHovering = false"
      >
        <!-- <label for="fullname">{{this.parameter}} *</label> -->
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
          <!-- Error icon -->
          <span v-if="hasError" class="error-icon">✕</span>
          <!-- Success icon -->
          <span v-if="isValid" class="success-icon">✔</span>
        </div>
        <!-- Error message -->
        <p v-if="hasError" class="error-message">Пожалуйста, введите корректное значение</p>
      </div>
    </div>
  </template>
  
  <script>
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
        // Simple validation: if length of fullname is less than 5, show error, otherwise success
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
  
  <style scoped>
  .input-container {
    width: 100%;
    margin-bottom: 5px;
  }
  
  .form-group {
    display: flex;
    flex-direction: column;
    position: relative;
    margin-bottom: 10px;
  }
  
  .input-wrapper {
    position: relative;
  }
  
  input {
    width: 100%;
    padding: 10px;
    border: 1px solid grey;
    transition: border 0.3s ease, background-color 0.3s ease;
  }
  
  /* Hover state */
  input:hover,
  .form-group.hover-input input {
    background-color: #f6f6f6;
  }
  
  /* Focus state */
  input:focus,
  input.focus-input {
    /* border: 1px solid #187cd3; */
    background-color: white;
    outline: none;
  }
  
  /* Error state */
  .input-error input {
    border: 1px solid red;
  }
  
  .input-error .error-icon {
    position: absolute;
    right: 10px;
    top: 50%;
    transform: translateY(-50%);
    color: red;
    font-size: 18px;
  }
  
  .input-error .error-message {
    color: red;
    margin-top: 5px;
    font-size: 12px;
  }
  
  /* Success state */
  .input-success input {
    /* border: 1px solid #0bb071; */
    background-color: #f6f6f6;
  }
  
  .input-success .success-icon {
    position: absolute;
    right: 10px;
    top: 50%;
    transform: translateY(-50%);
    color: #0bb071;
    font-size: 18px;
  }
  
  /* Error message */
  .error-message {
    color: red;
    font-size: 12px;
    margin-top: 5px;
  }
  </style>
  