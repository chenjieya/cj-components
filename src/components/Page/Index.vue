<template>
  <div id="page-container" :style="{width: cjContainerWidth+'px'}">
    <div id="cj-page-container" style="width: 100%;">
      <!--
        传参：
          1. cjLimt 每一页有多少条数据    Number
          2. cjIsborder 是否显示边框    Boolean
          3. cjTotal 总数据            Number
          4. cjCurrent 当前的页码       Number
          5. cjPage 页面中显示多少个数字  Number
      -->
      <ul class="cj-page">
        <li
            v-if="this.cjCurrent !== 1"
            @click="cjHandleClickPage(cjCurrent-1)"
            :class="{
            'cj-is-border': cjIsborder,
          }"
        >上一页</li>
        <li
            v-for="(item, index) in cjPageNumber"
            :key="index"
            :class="{
            'cj-current': cjCurrent === item,
            'cj-is-border': cjIsborder,
          }"
            @click="cjHandleClickPage(item)"
        >{{ item }}</li>
        <li
            v-if="this.cjCurrent !== this.cjTotalPage"
            @click="cjHandleClickPage(cjCurrent+1 )"
            :class="{
            'cj-is-border': cjIsborder,
          }"
        >下一页</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    cjCurrent: {
      type: Number,
      required: true,
    },
    cjLimt: {
      type: Number,
      required: true,
    },
    cjPage: {
      type: Number,
      default: 10,
    },
    cjTotal: {
      type: Number,
      required: true,
    },
    cjIsborder: {
      type: Boolean,
      default: true,
    },
    cjContainerWidth: {
      type: Number,
      default: 600,
    }
  },
  data() {
    return {
    }
  },
  computed: {
    /*计算一共有多少页*/
    cjTotalPage() {
      //计算之中可能会产生小数，我们需要向上取整
      return Math.ceil(this.cjTotal / this.cjLimt);
    },
    /*计算页面中页码数的起始值*/
    cjStartPage() {
      let start = this.cjCurrent - this.cjPage/2;
      // 计算完之后的开始页数，小于1的话，重新赋值
      if (start<1){
        start = 1;
      }
      return start;
    },
    /*计算页面中页码数的结束页*/
    cjEndPage() {
      let end = this.cjStartPage + this.cjPage - 1;
      // 如果计算完之后，最后的一页数字大于总页数，重新给最后一页赋值
      if (end>this.cjTotalPage) {
        end = this.cjTotalPage;
      }
      return end;
    },
    /*计算页面中显示的数字*/
    cjPageNumber() {
      //将数字放到数组之中，便于循环（循环是为了在页面中生成li）
      let showPageNumber = [];
      //开始和结束的数值，这些数值就是要显示在页面上面的页数
      let start = this.cjStartPage;
      let end = this.cjEndPage;
      for (let i = start;i <= end; i++){
        showPageNumber.push(i);
      }
      return showPageNumber;
    },
  },
  methods: {
    /*更改页数的方法*/
    cjHandleClickPage(newPage) {
      // 防止多次点击同一页码（如果多次点击同一个页码，则不通知父级changePage事件）
      if (this.cjCurrent === newPage){
        return;
      }
      this.$emit('changePage', newPage);
    }
  }
}
</script>
<style scoped>
@import "~@/assets/css/style.css";
#cj-page-container .cj-page{
  box-sizing: border-box;
  height: 30px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
#cj-page-container .cj-page li{
  height: 100%;
  width: 50px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 5px;
  border-radius: 4px;
  font-size: 12px;
  cursor: pointer;
}
#cj-page-container .cj-page li.cj-is-border{
  border: 1px solid;
}
#cj-page-container .cj-page li.cj-current{
  background-color: #4E6EF2;
  color: #fff;
  border-color: #4E6EF2;
}
</style>
