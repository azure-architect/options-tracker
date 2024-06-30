<template>
    <div class="stock-symbol-input">
      <label for="stockSymbol">Enter Stock Symbol:</label>
      <input
        type="text"
        id="stockSymbol"
        v-model="stockSymbol"
        @input="validateSymbol"
      />
      <p v-if="errorMessage" class="error">{{ errorMessage }}</p>
      <button @click="submitSymbol">Submit</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        stockSymbol: '',
        errorMessage: '',
      };
    },
    methods: {
      validateSymbol() {
        if (this.stockSymbol.trim() === '') {
          this.errorMessage = 'Stock symbol cannot be empty';
        } else {
          this.errorMessage = '';
        }
      },
      submitSymbol() {
        if (this.stockSymbol.trim() === '') {
          this.errorMessage = 'Stock symbol cannot be empty';
        } else {
          this.errorMessage = '';
          this.$emit('symbol-submitted', this.stockSymbol);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .stock-symbol-input {
    display: flex;
    flex-direction: column;
    max-width: 300px;
    margin: 0 auto;
  }
  
  .error {
    color: red;
  }
  </style>
  