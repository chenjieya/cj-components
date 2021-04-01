<template>
  <div id="test-container">
    <Icon type="add" :styles="styles"/>
    <Icon type="add-circle" />
    <Icon type="calendar" />
    <Icon type="direction-down-circle"/>
    <Icon type="home" />
    <Icon type="file-open" />
    <Icon type="picture" />
    <Icon type="telephone" />
    <Icon type="arrow-left-circle"/>
    <Icon type="chart-bar"/>
  </div>
</template>
<script>
/*使用：
*   传一个type特性
*   直接写上名字就好例如：主页 type='home'即可 （主页对应的class是icon-home）
* */
import Icon from './Index';
export default {
  data() {
    return{
      styles: {
        fontSize: '100px',
        color: '#f40',
      }
    }
  },
  components: {
    Icon,
  }
}
</script>
