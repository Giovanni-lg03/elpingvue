<template>
  <div class="full-height-wrapper" style="min-height: 650px;">
    <loading-screen
      loadingText="Accesso in corso"
      v-if="!isIframeLoaded"
      :fullWidth="true"
    />
    <iframe
      v-show="isIframeLoaded"
      title="Consulenza plus"
      @load="setIframeLoaded"
      allowtransparency="true"
      allowfullscreen="true"
      allow="geolocation; microphone; camera"
      src="https://form.jotform.com/210062839149052"
      frameborder="0"
      style="
      min-width: 100%;
      flex: 1;
      border:none;"
      scrolling="no"
    />
  </div>
</template>

<script>
import LoadingScreen from "@/components/LoadingScreen.vue";
export default {
  data() {
    return {
      isIframeLoaded: false,
    };
  },
  methods: {
    setIframeLoaded() {
      this.isIframeLoaded = true;
    },
  },
  components: {
    LoadingScreen,
  },
};
</script>
