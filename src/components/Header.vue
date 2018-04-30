<template>
  <div class="header">
      <div class="inner">
        <div class="logo"></div>
        <div class="right">
            <span class="loginBtn">Login</span>
            <span class="carIcon"></span>
        </div>
      </div>
  </div>
</template>
<script>
export default {};
</script>
<style lang="less" scoped>
.header {
  width: 100%;
  background:#fff;
  .inner {
    max-width: 1280px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    padding: 10px 0;
    box-sizing: border-box;
  }
  .logo {
    width: 100px;
    height: 50px;
    background: url("../imgs/logo.jpg") no-repeat center center;
    background-size: 100%;
  }
  .right {
    width: 120px;
    height: 50px;
    .loginBtn {
      float: left;
      width: 60px;
      line-height: 50px;
      font-size: 18px;
      text-align: center;
      cursor: pointer;
      transition: color .3s;
      &:hover {
        color:#f40;
      }
    }
    .carIcon {
      float: left;
      width: 60px;
      height: 50px;
      background: url("../imgs/shopcar.png") center center no-repeat;
      background-size: 50%;
    }
  }
}
</style>
