<template>
  <div id="actore-container">
    <img :src="url" :style="{width: setActore,height:setActore}" />
  </div>
</template>

<script>
export default {
  props: {
    url: {
      type: String,
      required: true,
    },
    size: {
      //因为最后是一个圆，所以宽高一样
      type: Number,
      default: 150,
    },
  },
  computed: {
    setActore() {
        return this.size + 'px';
    }
  },
};
</script>

<style scoped>
#actore-container img {
    border-radius: 50%;
    overflow: hidden;
}
</style>