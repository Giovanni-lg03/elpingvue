<template>
  <vue-range-slider
    v-model="userAnswer.prezzo"
    :step="50"
    :min="100"
    :max="1500"
    :enable-cross="false"
  ></vue-range-slider>
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
