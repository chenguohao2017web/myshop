<template>
  <div class="nav">
      <div class="inner">
          <router-link tag="span" to="/" class="home">Home</router-link>
          <span>/</span>
          <span class="active">{{navName}}</span>
      </div>
  </div>
</template>
<script>
export default {
  props: ["navName"]
};
</script>
<style lang="less" scoped>
.nav {
  width: 100%;
  background: #eaeaea;
  height: 50px;
  line-height: 50px;
  box-sizing: border-box;
  padding: 0 20px;
  .inner {
      max-width:1280px;
      margin:0 auto;
  }
  span {
    // margin-right: 5px;
    color:#333;
  }
  .home {
    cursor: pointer;
    transition: color 0.3s;
    &:hover {
      color: #f40;
    }
  }
  .active {
    color: #f40;
  }
}
</style>
