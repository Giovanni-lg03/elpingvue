<template>
  <survey-screen
    :questions="questions"
    :brands="brands"
    type="tablet"
    :defaultUserAnswer="defaultUserAnswer"
  />
</template>

<script>
import SurveyScreen from "@/components/survey/SurveyScreen.vue";
import {
  questions,
  brands,
  defaultUserAnswer,
} from "@/assets/js/TabletQuestions.js";

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
