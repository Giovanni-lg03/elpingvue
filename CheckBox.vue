<template>
  <div>
    <input
      :id="brand"
      type="checkbox"
      name="brand"
      v-model="isChecked"
      v-on:click="emitOnCheck"
    />
    <label :for="brand" class="mt-2 mr-2">{{ brand }} </label>
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
    brand: {
      type: String,
      required: true,
    },
  },
};
</script>
