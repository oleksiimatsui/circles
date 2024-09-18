<template>
  <div
    class="center-circle"
    :style="{
      width: circleWidth + 'px',
      height: circleWidth + 'px',
      border: radius + 'px solid ' + color,
    }"
    @mouseleave="makeColorDefault"
    @mouseenter="changeColor"
  >
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
      <slot></slot>
    </div>
  </div>
</template>
<script>
export default {
  setup() {},

  props: {
    padding: { type: Number, default: 30 },
    circleWidth: { type: Number, default: 500 },
    radius: { type: Number, default: 5 },
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
