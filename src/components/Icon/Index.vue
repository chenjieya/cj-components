<template>
  <div id="icon-container">
    <i class="iconfont" :class="handleIcon" :style="styles"></i>
  </div>
</template>

<script>
const iconObj = {
  "add": "icon-add",
  "add-circle": "icon-add-circle",
  "arrow-up-circle": "icon-arrow-up-circle",
  "arrow-right-circle": "icon-arrow-right-circle",
  "arrow-down": "icon-arrow-down",
  "ashbin": "icon-ashbin",
  "arrow-right": "icon-arrow-right",
  "browse": "icon-browse",
  "down-load": "icon-bottom",
  "back": "icon-back",
  "bad": "icon-bad",
  "arrow-double-left": "icon-arrow-double-left",
  "arrow-double-right": "icon-arrow-double-right",
  "arrow-left-circle": "icon-arrow-left-circle",
  "camera": "icon-camera",
  "chart-bar": "icon-chart-bar",
  "close": "icon-close",
  "calendar": "icon-calendar",
  "comment": "icon-comment",
  "customer-service": "icon-customer-service",
  "direction-down-circle": "icon-direction-down-circle",
  "fabulous": "icon-fabulous",
  "good": "icon-good",
  "home": "icon-home",
  "history": "icon-history",
  "file-open": "icon-file-open",
  "picture": "icon-picture",
  "telephone": "icon-telephone",
};
export default {
  props:{
    type:{
      type: String,
      required: true,
    },
    styles: {
      type: Object
    }
  },
  computed: {
    handleIcon() {
      return iconObj[this.type];
    }
  }
}
</script>

<style scoped>
@import "//at.alicdn.com/t/font_2458702_p7vid5eqri8.css";
</style>
