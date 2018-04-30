<template>
  <div class="home">
      <my-header></my-header>
      <my-nav navName="Goods"></my-nav>
      <my-shop-list></my-shop-list>
      <my-footer></my-footer>
  </div>
</template>
<script>
import MyHeader from '@/components/Header'
import MyNav from '@/pages/home/components/Nav'
import MyShopList from '@/pages/home/components/ShopList'
import MyFooter from '@/components/Footer'
export default {
    components:{
        MyHeader,
        MyNav,
        MyShopList,
        MyFooter
    }
}
</script>
<style lang="less" scoped>

</style>
