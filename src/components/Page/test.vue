<template>
  <div id="test" style="margin: 100px">
    <Page :pageInfo="pageInfo" @changPage="handleChange" />
  </div>
</template>

<script>
import Page from "./Index.vue";
export default {
  components: {
    Page,
  },
  data() {
    return {
      pageInfo: {
        current: 1,
        total: 100,
        limt: 10,
      },
    };
  },
  methods: {
    handleChange(newPage) {
      if(newPage<=1){
        this.pageInfo.current = 1;
        return;
      }
      this.pageInfo.current = newPage;
    },
  },
};
</script>

<style>
</style>