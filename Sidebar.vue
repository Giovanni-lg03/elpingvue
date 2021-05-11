<template>
  <div
    class="d-flex align-content-center"
    :class="sidebarLength - 1 !== index && 'mb-2'"
    style="position: relative; width: fit-content;"
    v-on:click="$emit('clicked', index)"
  >
    <div class="circle mr-3" :class="[classOnSelected, showPointer]">
      {{ index + 1 }}
    </div>
    <span
      class="my-auto lead d-none d-lg-block"
      :class="[classOnSelected, showPointer]"
      style="text-transform: capitalize;"
    >
      {{ shortName }}
    </span>
  </div>
</template>

<script>
export default {
  props: ["index", "shortName", "currentQuestion", "sidebarLength"],
  computed: {
    showPointer() {
      return this.index !== 9 && "cursor-pointer";
    },
    classOnSelected() {
      return this.currentQuestion === this.index ? "text-red" : "text-grey";
    },
  },
};
</script>
