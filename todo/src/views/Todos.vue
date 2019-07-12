<template>
  <div>
    <h1>Habra algo....</h1>
    <h2>{{nombre}}</h2>
    <Counter :initValue="200"/>
    <Counter/>
    <Counter/>
    <Counter/>
    <Counter/>
  </div>
</template>

<script>
import Counter from '@/components/Counter.vue';

export default {
  data() {
    return {
      nombre: 'Counter',
    };
  },
  components: {
    Counter,
  },
};
</script>
