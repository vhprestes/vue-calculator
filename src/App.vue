<template>
  <div class="toggle">
      <button @click="toggleDarkMode" class="toggle-button">Toggle Dark Mode</button>
    </div>
  <div>
    <Calculator :dark-mode="darkMode" />
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue';

export default {
  data() {
    return {
      darkMode: false,
    }
  },
  
  methods: {
    toggleDarkMode() {
      this.darkMode = !this.darkMode;
      document.body.classList.toggle('dark-mode');
      console.log('toggleDarkMode', this.darkMode)
    }
  },
  components: {
    Calculator
  }
}
</script>

<style>
.dark {
  background-color: #696969 !important;
  color: #fff;
}

.dark .toggle {
  background-color: #1e88e5;
  color: #fff;
}

.calculator {
  background-color: #b1b1b1;
  color: #333333;
}

.toggle {
  background-color: #e0e0e0;
  color: #212121;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
  width: 200px !important;
  height: 50px !important
}

.toggle-button {
  background-color: #e0e0e0;
  color: #212121;
  border: none;
  padding: 5px 10px;
  border-radius: 5px;
  cursor: pointer;
  width: 200px !important;
  height: 50px !important
}

body {
  background-color: #f0f0f0; /* modo claro */
}

.dark-mode {
  background-color: #222; /* modo escuro */
}

</style>