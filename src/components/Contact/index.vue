<template>
  <ul id="contact-container">
    <li>
      <a href="https://github.com/chenjieya">
        <div class="icon">
          <icon type="home"/>
        </div>
        <span>github</span>
      </a>
    </li>
    <li>
      <a href="mailto:2959508594@qq.com">
        <div class="icon">
          <icon type="home"/>
        </div>
        <span>2959508594@qq.com</span>
      </a>
    </li>
    <li>
      <a
          href="tencent://message/?Menu=yes&uin=2929194659&Service=300&sigT=45a1e5847943b64c6ff3990f8a9e644d2b31356cb0b4ac6b24663a3c8dd0f8aa12a595b1714f9d45">
        <div class="icon">
          <icon type="home"/>
        </div>
        <span>2959508594</span>
      </a>
      <div class="mask">
        <img src="http://www.duyiedu.com/source/img/%E5%85%AC%E4%BC%97%E5%8F%B7%E4%BA%8C%E7%BB%B4%E7%A0%81.png">
      </div>
    </li>
  </ul>
</template>

<script>
import Icon from '@/components/Icon/Index.vue';
export default {
  name: "index",
  components: {
    Icon,
  }
}
</script>

<style scoped lang="less">
@import "~@/assets/css/style.css";
#contact-container{
  li {
    position: relative;
    &:hover .mask{
      transform: scaleY(1);
    }
    a{
      display: flex;
      color: #fff;
      padding: 5px 10px;
      cursor: pointer;
      .icon {
        margin-right: 5px;
      }
    }
    .mask{
      width: 120px;
      height: 120px;
      position: absolute;
      left: 10px;
      bottom: 35px;
      background-color: #fff;
      border-radius: 5px;
      transform: scaleY(0);
      transform-origin: bottom;
      transition: 0.3s;
      &::after {
        content: '';
        position: absolute;
        left:50%;
        transform: translateX(-50%) rotate(45deg);
        bottom: -4px;
        width: 8px;
        height: 8px;
        background-color: #fff;
      }
      img{
        width: 100px;
        height: 100px;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
      }
    }
  }
}
</style>
