<template>
  <div class="px-4">
    <h1 class="display-4 text-center" v-html="currentQuestion.title" />
    <p class="font-weight-light">{{ currentQuestion.description }}</p>

    <div
      class="input-container text-center"
      :class="currentQuestion.type !== 'checkbox' && 'mt-5'"
    >
      <div
        v-if="currentQuestion.type === 'checkbox'"
        class="d-flex flex-wrap justify-content-center"
      >
        <check-box
          @onChecked="handleChecked"
          v-for="(brand, index) in brands"
          :brand="brand"
          :key="'input' + index"
        />
      </div>
      <div
        v-if="currentQuestion.type === 'radio'"
        class="d-flex flex-wrap justify-content-center"
      >
        <radio
          @onChecked="handleRadioChecked"
          v-for="(option, index) in currentQuestion.radioOptions"
          :option="option"
          :key="'input' + index"
        />
      </div>
      <template v-else-if="currentQuestion.type === 'slider'">
        <vue-slider
          @change="emitUserAnswer"
          :min="1"
          :max="10"
          v-model="sliderValue"
          :tooltip="'always'"
        ></vue-slider>
      </template>
      <template v-else-if="currentQuestion.type === 'doubleSlider'">
        <vue-slider
          @change="emitUserAnswer"
          v-model="doubleSliderValue"
          :min="100"
          :max="1500"
          :min-range="100"
          :interval="50"
          :tooltip="'always'"
          :tooltip-formatter="'€{value}'"
        ></vue-slider>
      </template>
    </div>
  </div>
</template>

<script>
import CheckBox from "./CheckBox.vue";
import Radio from "./Radio.vue";
import VueSlider from "vue-slider-component";
export default {
  data() {
    return {
      doubleSliderValue: this.defaultUserAnswer.prezzo,
      sliderValue: 5,
      checkedBrands: [],
    };
  },
  props: {
    currentQuestion: {
      type: Object,
      required: true,
    },
    brands: {
      type: Array,
      required: true,
    },
    defaultUserAnswer: {
      type: Object,
      required: true,
    },
    currentQuestionNumber: {
      type: Number,
      required: true,
    },
  },
  methods: {
    handleChecked(e) {
      if (e.isChecked) {
        this.checkedBrands.push(e.brand);
      } else {
        this.checkedBrands.pop(e.brand);
      }
      this.emitUserAnswer(this.checkedBrands);
    },
    handleRadioChecked(e) {
      this.emitUserAnswer(e.isChecked);
    },
    emitUserAnswer(payload) {
      this.$emit("onAnswerChange", {
        [this.currentQuestion.shortName]: payload,
      });
      console.log("emitted", { [this.currentQuestion.shortName]: payload });
    },
  },
  watch: {
    currentQuestionNumber(newQuestion, oldQuestion) {
      if (newQuestion !== oldQuestion) {
        // Next pressed
        this.sliderValue = this.defaultUserAnswer[
          this.currentQuestion.shortName
        ];
      }
    },
  },
  components: {
    CheckBox,
    VueSlider,
    Radio,
  },
};
</script>
