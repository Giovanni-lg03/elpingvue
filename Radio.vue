<template>
  <div>
    <input
      :id="option"
      type="radio"
      name="option"
      v-model="isChecked"
      v-on:click="emitOnCheck"
    />
    <label :for="option" class="mt-2 mr-2">{{ option }} </label>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isChecked: false,
    };
  },
  methods: {
    emitOnCheck(e) {
      this.$emit("onChecked", {
        isChecked: e.target.checked,
        brand: this.brand,
      });
    },
  },
  props: {
    option: {
      type: String,
      required: true,
    },
  },
};
</script>
