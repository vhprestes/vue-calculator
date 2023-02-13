<template>
  <div :class="{ 'calculator': true, 'dark': darkMode }">
    <input type="text" v-model="result" />
    <div class="buttons">
      <button class="button" v-for="button in buttons" :key="button.value" @click="handleClick(button)">
        {{ button.label }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    darkMode: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      result: "0",
      buttons: [
        { label: "C", value: "clear" },
        { label: "/", value: "/" },
        { label: "*", value: "*" },
        { label: "7", value: "7" },
        { label: "8", value: "8" },
        { label: "9", value: "9" },
        { label: "4", value: "4" },
        { label: "5", value: "5" },
        { label: "6", value: "6" },
        { label: "1", value: "1" },
        { label: "2", value: "2" },
        { label: "3", value: "3" },
        { label: "-", value: "-" },
        { label: "0", value: "0" },
        { label: ".", value: "." },
        { label: "+", value: "+" },
        { label: "√", value: "sqrt" },
        { label: "=", value: "=" }
      ]

    };
  },
  methods: {
    handleClick(button) {
      if (this.result === "0" && ["+", "-", "/", "*", "."].includes(button.value)) {
      return;
  }
  if (["+", "-", "/", "*", "."].includes(button.value) && ["+", "-", "/", "*", "."].includes(this.result.slice(-1))) {
    this.result = this.result.slice(0, -1) + button.value;
    }
      if (button.value === "clear") {
        this.result = "0";
      } else if (button.value === "sqrt") {
        this.result = Math.sqrt(parseFloat(this.result)).toString();
      } else if (button.value === "=") {
        this.result = eval(this.result).toString();
      } else {
        if (this.result === "0" && button.value !== ".") {
          this.result = button.value;
        } else {
          this.result += button.value;
        }
      }
    }
  }
};
</script>

<style>
.calculator {
  display: inline-block;
  width: 23%;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
}

.dark .calculator {
  background-color: #212121;
  color: #fff;
}

input[type="text"] {
  width: 100%;
  border: none;
  font-size: 28px;
  margin-bottom: 10px;
  padding: 5px;
  border-radius: 5px;
}

input[type="text"].dark {
  background-color: #333;
  color: #fff;
}

button {
  width: 70px;
  height: 70px;
  margin-right: 10px;
  margin-bottom: 10px;
  font-size: 24px;
  border-radius: 5px;
  border: none;
  cursor: pointer;
  background-color: #f2f2f2;
  color: #333;
  transition: all 0.2s ease;
}

button.dark {
  background-color: #444;
  color: #fff;
}

button:hover {
  background-color: #e6e6e6;
}

button:active {
  transform: scale(0.95);
}
</style>