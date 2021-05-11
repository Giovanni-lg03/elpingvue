<template>
  <section class="mt-5">
    <div class="container">
      <div class="row">
        <div
          class="col-12 col-lg-6 my-auto"
          :class="orderMd2"
          data-aos="fade-up"
          data-aos-delay="200"
        >
          <slot></slot>
        </div>
        <div
          class="col-12 col-lg-6 my-auto"
          :class="orderMd1 + ' text-' + align"
          :data-aos="'fade-' + align"
        >
          <h2 class="display-5" :class="'text-' + align" v-html="title"></h2>
          <p class="lead" :class="'text-' + align">
            {{ description }}
          </p>
          <slot name="button">
            <button class="btn btn-primary">
              Scegli ora
            </button>
          </slot>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  computed: {
    orderMd1() {
      if (this.align === "left") {
        return "order-lg-1";
      }
      return "order-lg-2";
    },
    orderMd2() {
      if (this.align === "left") {
        return "order-lg-2";
      }
      return "order-lg-1";
    },
  },
  props: ["title", "description", "alignDirection", "index", "align"],
};
</script>
