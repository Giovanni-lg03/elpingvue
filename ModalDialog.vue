<template>
  <div class="banner absolute-center p-4 shadow">
    <div>
      <h3>
        Impossibile trovare dispositivi nell'intervallo di prezzo specificato!
      </h3>
      <p>Scegli un intervallo più ampio.</p>
      <button class="btn bg-red text-light" @click="close">
        Ho capito
      </button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    close() {
      this.$emit("hide");
    },
  },
};
</script>

<style scoped>
.banner {
  margin: auto;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  max-width: 50%;
  height: fit-content;
  background-color: white;
  border-radius: 1rem;
  z-index: 1;
}
.absolute-center {
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}
@media (max-width: 768px) {
  .banner {
    max-width: 80%;
  }
}
</style>
