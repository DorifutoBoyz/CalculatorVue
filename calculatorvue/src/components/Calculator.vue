<template>
  <div class="calculator">
    <input v-model="input" class="input" type="text">
    <div class="buttons">
      <div class="button-row">
        <button v-for="n in 9" :key="n" @click="input += n">{{ n }}</button>
        <button @click="input += '0'">0</button>
      </div>
      <div class="button-row">
        <button @click="input += '+'">+</button>
        <button @click="input += '-'">-</button>
        <button @click="input += '*'">*</button>
        <button @click="input += '/'">/</button>
      </div>
      <div class="button-row">
        <button @click="clear">C</button>
        <button @click="input = input.slice(0, -1)">←</button>
        <button @click="calculate">=</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line
  name: 'Calculator',
  data() {
    return {
      input: '',
    };
  },
  methods: {
    calculate() {
      try {
        this.input = String(eval(this.input));
      } catch (error) {
        this.input = 'Error';
      }
    },
    clear() {
      this.input = '';
    },
  },
};
</script>


<style scoped>
.calculator {
  width: 300px;
  margin: 0 auto;
  text-align: center;
}

.input {
  width: 100%;
  font-size: 24px;
  padding: 10px;
  margin-bottom: 10px;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

button {
  width: 100%;
  padding: 10px;
  font-size: 18px;
}

.button-row {
  display: grid;
  grid-template-columns: repeat(3, 1fr) 2fr;
  gap: 10px;
}
</style>
