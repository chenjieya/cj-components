<template>
  <div id="page-container">
    <!-- 分页组件 -->
    <ul class="page">
      <li
        :class="{ 'page-item': true, disabled: currentPage <= 1 }"
        @click="handlePage(1)"
      >
        <a>|&lt;&lt;</a>
      </li>
      <li
        :class="{ 'page-item': true, disabled: currentPage <= 1 }"
        @click="handlePage(currentPage - 1)"
      >
        <a>|&lt;</a>
      </li>
      <li
        :class="{
          'page-item': true,
          active: currentPage === item,
        }"
        v-for="item in showPage"
        :key="item"
        @click="handlePage(item)"
      >
        <a>{{ item }}</a>
      </li>
      <li
        :class="{ 'page-item': true, disabled: currentPage >= totalPage }"
        @click="handlePage(currentPage + 1)"
      >
        <a>&gt;|</a>
      </li>
      <li
        :class="{ 'page-item': true, disabled: currentPage >= totalPage }"
        @click="handlePage(totalPage)"
      >
        <a>&gt;&gt;|</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    pageInfo: {
      type: Object,
      required: true,
    },
  },
  computed: {
    // limtPage() {
    //   //获得一共显示多少分页按钮
    //   const { limt } = this.pageInfo;
    //   return limt;
    // },
    currentPage() {
      //获得当前页
      const { current } = this.pageInfo;
      return current;
    },
    showPage() {
      // 页面中显示的数字
      const { current, limt, total } = this.pageInfo;
      let startPage = current - Math.floor(limt / 2); //当前开始的数字
      startPage = startPage < 1 ? 1 : startPage;

      let endPage = startPage + limt - 1;
      endPage = endPage > total ? total : endPage;
      let arr = [];
      for (let i = 0; i <= limt; i++) {
          console.log(endPage);
        arr.push(startPage);
        startPage++;
      }
      return arr;
    },
    totalPage() {
      const { total } = this.pageInfo;
      return total;
    },
  },
  methods: {
    handlePage(changpage) {
      this.$emit("changPage", changpage);
    },
  },
};
</script>

<style>
@import "~@/assets/css/style.css";
#page-container .page {
  display: flex;
}
#page-container .page .page-item {
  width: 30px;
  height: 30px;
  border: 1px solid #ccc;
  line-height: 30px;
  text-align: center;
  cursor: pointer;
}
#page-container .page .page-item.active {
  background-color: #f40;
  color: #fff;
}
#page-container .page .disabled {
  background-color: #ccc;
  cursor: no-drop;
}
</style>
