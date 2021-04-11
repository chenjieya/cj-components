<template>
  <div id="image-load-container">
    <!--图片站位-->
    <img :src="placeholder" class="placeholder-image" v-if="!everyDone">
    <img :src="src" @load="handleLoad" :style="{opacity: opacitytState, transition: `${duration}ms`}">
  </div>
</template>
<script>
export default {
  props: {
    src: {
      type: String,
      required: true
    },
    placeholder:{
      type: String,
      require: true
    },
    duration: {
      type: Number,
      default: 500
    }
  },
  data() {
    return {
      originState: false,  // 原图一开始是默认的false状态，此时设置opacity样式
      everyDone: false, //等到所有事情都做完之后
    }
  },
  methods: {
    handleLoad() {
      console.log('xxx')
      // 原图加载完成的时候执行的事件
      this.originState = true;
      setTimeout(()=>{
        this.everyDone = true;
        this.$emit('load');
      }, this.duration)
    }
  },
  computed: {
    opacitytState() {
      return this.originState?1:0;
    }
  },
}
</script>
<style scoped lang="less">
#image-load-container {
  width: 100%;
  height: 100%;
  position: relative;
  overflow: hidden;
  .placeholder-image {
    filter: blur(2vw);
  }
}
#image-load-container img{
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  object-fit: cover;
}

</style>
