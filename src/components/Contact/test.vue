<template>
  <div id="test-container">
    <contact />
  </div>
</template>

<script>
import Contact from './index.vue';
export default {
  name: "test",
  components: {
    Contact,
  }
}
</script>

<style scoped lang="less">
#test-container {
  width: 300px;
  height: 600px;
  background-color: #000;
  margin: 0 auto;
  padding-top: 200px;
}
</style>
