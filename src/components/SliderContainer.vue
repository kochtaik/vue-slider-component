<template>
  <section class="slider-root">
    <div class="slider-root__container">
      <span class="control control-left" @click="showPreviousSlide">&lt;</span>
      <div ref="slidesElem" class="slides">
        <div class="slide slide-1">1</div>
        <div class="slide slide-2">2</div>
        <div class="slide slide-3">3</div>
        <div class="slide slide-4">4</div>
        <div class="slide slide-5">5</div>
      </div>
      <span class="control control-right" @click="showNextSlide">&gt;</span>
    </div>
  </section>
</template>

<script lang="ts">
import { computed, ComputedRef, defineComponent, ref } from 'vue';

export default defineComponent({
  setup() {
    const slidesElem = ref<HTMLElement | null>(null);
    let currentSlide = ref(0);

    function showNextSlide() {
      if (!slidesNumber.value) return;
      if (currentSlide.value === slidesNumber.value - 1) return;

      currentSlide.value += 1;
      showSlide();
    }

    function showPreviousSlide() {
      if (!currentSlide.value) return;

      currentSlide.value -= 1;
      showSlide();
    }

    function showSlide() {
      if (!slidesElem.value) return;

      slidesElem.value.style.transform = `translateX(-${
        slidesElem.value.offsetWidth * currentSlide.value
      }px)`;
    }

    const slidesNumber: ComputedRef<number | undefined> = computed(() => {
      return slidesElem.value?.childElementCount;
    });

    return {
      slidesElem,
      /* methods */
      showNextSlide,
      showPreviousSlide,
    };
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.slider-root {
  position: relative;
  width: 100%;
  height: 400px;

  &__container {
    width: 100%;
    height: 400px;
    overflow: hidden;

    .control {
      position: absolute;
      top: 0;
      height: 100%;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      user-select: none;
      font-size: 2em;
      z-index: 10;
    }

    .control-right {
      right: 0;
    }

    .control-left {
      left: 0;
    }

    .slides {
      display: flex;
      transition: all 0.3s;

      .slide {
        width: 100%;
        height: 400px;
        background: #49cbff;
        flex-shrink: 0;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 4em;
      }
    }
  }
}
</style>
