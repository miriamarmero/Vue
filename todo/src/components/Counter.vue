<template>
  <div>
    <h2>{{porcent}}</h2>
    <h3>{{numero}} init value {{initValue}}</h3>
    <input v-model="numero" type="number"
      :max="max" :min="min"
      :class="{isGreen, isRed, isOrange}"/>
    <button @click="incrementar"
      :disabled="incrementIsDisabled"
      :class="{disabled: incrementIsDisabled}">
      Incrementar
    </button>
    <button @click="decrementar"
      :disabled="decrementIsDisabled"
      :class="{disabled: decrementIsDisabled}">
      Decrementar
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero: 0,
      porcent: 0,
    };
  },
  props: {
    initValue: {
      type: Number,
      default: 0,
    },
    min: {
      type: Number,
      default: 0,
    },
    max: {
      type: Number,
      default: 100,
    },
  },
  methods: {
    incrementar() {
      this.numero = +this.numero + 1;
    },
    decrementar() {
      this.numero = +this.numero - 1;
    },
  },
  computed: {
    incrementIsDisabled() {
      return this.numero >= this.max;
    },
    decrementIsDisabled() {
      return this.numero <= this.min;
    },
    porcentaje() {
      return 100 * (this.numero - this.min) / (this.max - this.min);
    },
    isGreen() {
      return this.porcentaje <= 33;
    },
    isOrange() {
      return this.porcentaje > 33 && this.porcentaje <= 66;
    },
    isRed() {
      return this.porcentaje > 66;
    },
  },
  watch: {
    numero(val) {
      if (val > this.max) {
        this.numero = this.max;
      }

      if (val < this.min) {
        this.numero = this.min;
      }
    },
  },
  created() {
    this.numero = this.initValue;
    console.log('He sido creado', this.initValue);
  },
};
</script>

<style scoped>
  .disabled {
    background: white;
  }

  .isRed {
    background:red;
  }
  .isGreen {
    background:greenyellow;
  }
  .isOrange {
    background:orange;
  }
</style>
