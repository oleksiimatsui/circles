<template>
  <div
    class="center-circle"
    :style="{
      width: circleWidth + 'px',
      height: circleWidth + 'px',
      border: borderRadius + 'px solid ' + color,
    }"
    @mouseleave="makeColorDefault"
    @mouseenter="changeColor"
  >
    <!-- add inner div for making the color default when mouse is inside the circle -->
    <div
      @mouseleave="changeColor"
      @mouseenter="makeColorDefault"
      class="center-circle"
      style="border-radius: 100%"
      :style="{
        width: '100%',
        height: '100%',
      }"
    >
      <!-- make it possible to add children components -->
      <slot></slot>
    </div>
  </div>
</template>
<script>
export default {
  setup() {},

  props: {
    circleWidth: { type: Number, default: 500 },
    borderRadius: { type: Number, default: 5 },
    color: { type: String, default: "black" },
  },
  data() {},
  methods: {
    changeColor() {
      this.$emit("changeColor");
    },
    makeColorDefault() {
      this.$emit("returnColor");
    },
  },
};
</script>
<style scoped>
.center-circle {
  border-radius: 100%;
  display: flex;
  display: flex;
  align-items: center;
  align-content: center;
  justify-content: center;
  justify-items: center;
}
</style>
