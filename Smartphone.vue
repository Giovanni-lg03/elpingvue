<template>
  <survey-screen
    :questions="questions"
    :brands="brands"
    :defaultUserAnswer="defaultUserAnswer"
  />
</template>

<script>
import SurveyScreen from "@/components/survey/SurveyScreen.vue";
import {
  questions,
  brands,
  defaultUserAnswer,
} from "@/assets/js/SmartphoneQuestions.js";

export default {
  data() {
    return {
      questions,
      brands,
      defaultUserAnswer,
    };
  },
  components: {
    SurveyScreen,
  },
};
</script>
