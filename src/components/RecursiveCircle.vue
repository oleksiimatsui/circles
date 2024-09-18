<template>
  <hovering-circle
    :circle-width="width"
    :border-radius="borderRadius"
    :color="color"
    @changeColor="
      () => {
        $emit('colorChanged'), (color = '#f4ff5e');
      }
    "
    @returnColor="
      () => {
        $emit('colorReturned'), (color = defaultColor);
      }
    "
  >
    <recursive-circle
      v-if="width > padding"
      :width="width - padding - borderRadius"
      @colorChanged="() => (color = '#fff')"
      @colorReturned="() => (color = defaultColor)"
      :defaultColor="makeLighter(defaultColor, 5)"
      :padding="padding"
      :borderRadius="borderRadius"
    ></recursive-circle>
  </hovering-circle>
</template>
<script>
import HoveringCircle from "./HoveringCircle.vue";
export default {
  components: { HoveringCircle },
  setup() {},

  props: {
    width: { type: Number, default: 500 },
    defaultColor: { type: String, default: "#000" },
    padding: { type: Number, default: 50 },
    borderRadius: { type: Number, default: 10 },
  },
  data() {
    return {
      color: this.defaultColor,
    };
  },
  methods: {
    makeLighter(col, amt) {
      var usePound = false;
      if (col[0] == "#") {
        col = col.slice(1);
        usePound = true;
      }

      var num = parseInt(col, 16);

      var r = (num >> 16) + amt;

      if (r > 255) r = 255;
      else if (r < 0) r = 0;

      var b = ((num >> 8) & 0x00ff) + amt;

      if (b > 255) b = 255;
      else if (b < 0) b = 0;

      var g = (num & 0x0000ff) + amt;

      if (g > 255) g = 255;
      else if (g < 0) g = 0;

      return (usePound ? "#" : "") + (g | (b << 8) | (r << 16)).toString(16);
    },
  },
};
</script>
<style scoped></style>
