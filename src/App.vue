<template>
  <slider-container></slider-container>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import SliderContainer from './components/SliderContainer.vue';
export default defineComponent({
  components: {
    SliderContainer,
  },
});
</script>

<style lang="scss">
#app {
  font-size: 16px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 0;
  padding: 0;
  border: 0;
  box-sizing: border-box;
}

@media (min-width: 767px) {
  #app {
    font-size: 19px;
  }
}
</style>
