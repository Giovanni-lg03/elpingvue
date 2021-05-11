<template>
  <div class="slider-container">
    <div class="slider-range mt-5">
      <vue-range-slider
        v-model="sliderValue"
        :step="1"
        :min="1"
        :max="10"
      ></vue-range-slider>
    </div>
  </div>
</template>

<script>
import "vue-range-component/dist/vue-range-slider.css";
import VueRangeSlider from "vue-range-component";
export default {
  components: {
    VueRangeSlider,
  },
};
</script>
