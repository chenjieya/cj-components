<template>
  <div id="test" style="margin: 100px; width: 600px;">
    <!--
    传参：
      1. cjLimt 每一页有多少条数据    Number
      2. cjIsborder 是否显示边框    Boolean
      3. cjTotal 总数据            Number
      4. cjCurrent 当前的页码       Number
      5. cjPage 页面中显示多少个数字  Number
      6.changePage function函数  是由组件提交的方法，当点击分页按钮的时候，将新点击的页数传过来
  -->
    <Page
        :cj-current="cjCurrent"
        :cj-limt="cjLimt"
        :cj-page="cjPage"
        :cj-total="cjTotal"
        :cj-isborder="cjIsborder"
        @changePage="handleChange"
    />
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
     "cjCurrent": 1,
      "cjLimt": 10,
      "cjPage": 10,
      "cjTotal": 1001,
      "cjIsborder": true,
    };
  },
  methods: {
    handleChange(newPage) {
      this.cjCurrent = newPage;
      //可以在这这里加载数据
      console.log(`正在加载第${this.cjCurrent}页的数据`);
    }
  },
};
</script>

<style>
</style>
