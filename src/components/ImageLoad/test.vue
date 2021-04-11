<template>
  <div id="test-container">
<!--
  src:原图地址
  placeholder: 站位图地址
  duration: 原图加载完之后1000毫秒显示出来
  事件
  load加载完成之后触发事件
-->
    <ImageLoad
        src="https://images.pexels.com/photos/33109/fall-autumn-red-season.jpg?fit=crop&crop=entropy&w=3456&h=2304"
        placeholder="https://images.pexels.com/photos/33109/fall-autumn-red-season.jpg?w=100"
        :duration="100"
        @load="handleLoad"
     />
  </div>
</template>
<script>
import ImageLoad from '@/components/ImageLoad/Index.vue';
export default {
  components: {
    ImageLoad,
  },
  methods: {
    handleLoad() {
      console.log('图片加载完成了')
    }
  }
}
</script>

<style scoped>
#test-container{
  width: 500px;
  height: 400px;
  border: 2px solid;
  margin: 100px auto;
}
</style>
