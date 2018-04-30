<template>
  <div class="shopList">
      <div class="listTop">
          <div class="controlWrapper">
              <span class="fillterBtn" @click="handleMiniPriceBtn">FILLTER BY</span>
              <span>sort by:</span>
              <span class="default">Default</span>
              <span class="price">price<i class="priceIcon"></i></span>
          </div>
      </div>
      <div class="listContent">
          <div class="priceWrapper">
              <h4 class="title">PRICE:</h4>
              <ul>
                    <li v-for="(item,index) of priceList" 
                        class="item" 
                        :class="{active:currentIndex===index}"
                        @click="handleSelectPrice(index)"
                    >{{item}}</li>
              </ul>
          </div>
          <div class="shopWrapper">
              <ul>
                  <li class="shopItem" v-for="item of shopList">
                     <div class="imgBox">
                         <img :src="item.imgUrl" alt="">
                     </div>
                     <div class="title">{{item.name}}</div>
                     <div class="price">{{item.price}}</div>
                     <button class="btn">加入购物车</button>
                  </li>
              </ul>
          </div>
      </div>
      <div class="miniWrapper">
        <fade-animate>
          <div class="mask" ref="mask" v-show="mask" @click="handleMaskClick"></div>
        </fade-animate>
        <div class="priceWrapper" ref="priceWrapper">
          <h4 class="title">PRICE:</h4>
          <ul>
            <li v-for="(item,index) of priceList" 
                class="item" 
                :class="{active:currentIndex===index}"
                @click="handleMiniSelectPrice(index)"
            >{{item}}</li>
          </ul>
          </div>
      </div>
      
  </div>
</template>
<script>
import FadeAnimate from "@/components/fadeAnimate";
export default {
  data() {
    return {
      priceList: [
        "ALL",
        "0.00 - 100.00",
        "100.00 - 500.00",
        "500.00 - 1000",
        "1000.00 - 2000.00"
      ],
      shopList: [
        {
          imgUrl: require("../../../imgs/dr10.jpg"),
          name: "双刃10LCW",
          price: 39
        },
        {
          imgUrl: require("../../../imgs/dr10.jpg"),
          name: "双刃10LCW",
          price: 39
        },
        {
          imgUrl: require("../../../imgs/dr10.jpg"),
          name: "双刃10LCW",
          price: 39
        },
        {
          imgUrl: require("../../../imgs/dr10.jpg"),
          name: "双刃10LCW",
          price: 39
        },
        {
          imgUrl: require("../../../imgs/dr10.jpg"),
          name: "双刃10LCW",
          price: 39
        }
      ],
      currentIndex: 0,
      mask: false
      // priceWrapper:false
    };
  },
  methods: {
    handleSelectPrice(index) {
      this.currentIndex = index;
    },
    handleMiniPriceBtn() {
      this.mask = true;
      this.$refs.priceWrapper.style.transition = "all 0.5s";
      this.$refs.priceWrapper.style.transform = "translate3d(0,0,0)";
    },
    handleMiniSelectPrice(index) {
      this.currentIndex = index;
      this.mask = false;
      this.$refs.priceWrapper.style.transform = "translate3d(-100%,0,0)";
    },
    handleMaskClick() {
      this.mask = false;
      this.$refs.priceWrapper.style.transform = "translate3d(-100%,0,0)";
    }
  },
  components: {
    FadeAnimate
  }
};
</script>
<style lang="less" scoped>
.shopList {
  max-width: 1280px;
  margin: 0 auto;
  box-sizing: border-box;
  padding: 30px 0;
  @media screen and(max-width:700px) {
    padding: 0;
  }
  .fillterBtn {
    position: fi;
  }
  .listTop {
    width: 100%;
    height: 50px;
    background: #fff;
    position: relative;
    .fillterBtn {
      position: absolute;
      top: 0;
      left: 0;
      display: none;
      cursor: pointer;
      @media screen and(max-width:980px) {
        display: block;
      }
    }
    @media screen and(max-width:700px) {
      background: #eaeaea;
    }
    .controlWrapper {
      float: right;
      margin-right: 20px;
      span {
        color: #333;
        margin-left: 10px;
        line-height: 50px;
        &.default {
          color: #f40;
          cursor: pointer;
        }
        &.price:hover {
          color: #f40;
        }
        &.price {
          cursor: pointer;
          transition: color 0.3s;
        }
      }
    }
  }
  .listContent {
    width: 100%;
    box-sizing: border-box;
    padding: 15px 0;
    display: flex;
    @media screen and (max-width: 700px) {
      padding: 0;
    }
    .priceWrapper {
      width: 250px;
      box-sizing: border-box;
      padding-left: 20px;
      @media screen and(max-width:980px) {
        display: none;
      }
      .title {
        letter-spacing: 4px;
        height: 50px;
        line-height: 50px;
      }
      .item {
        height: 30px;
        line-height: 30px;
        margin-bottom: 20px;
        transition: all 0.3;
        font-size: 14px;
        cursor: pointer;
        transition: all 0.3s;
        &.active {
          color: #f40;
          border-left: 1px solid #f40;
          padding-left: 20px;
          font-weight: 600;
        }
        &:hover {
          color: #f40;
          border-left: 1px solid #f40;
          padding-left: 20px;
          font-weight: 600;
        }
      }
    }
    .shopWrapper {
      flex: 1;
      box-sizing: border-box;
      padding: 15px 0;
      @media screen and(max-width:700px) {
        padding: 0;
      }
      .shopItem {
        width: 23%;
        float: left;
        background: #fff;
        margin-left: 2%;
        box-sizing: border-box;
        padding: 10px;
        border: 1px solid #ccc;
        margin-bottom: 20px;
        transition: all 0.5s;
        &:hover {
          border: 1px solid #f40;
          transform: translateY(-5px);
          box-shadow: 0px 0px 3px 3px rgba(0, 0, 0, 0.1);
        }
        .imgBox {
          width: 100%;
          height: 0;
          padding-bottom: 110%;
          overflow: hidden;
          img {
            width: 100%;
          }
        }
        .title {
          font-weight: 600;
          margin-bottom: 20px;
        }
        .price {
          font-size: 24px;
          color: #f40;
          margin-bottom: 15px;
        }
        .btn {
          display: inline-block;
          width: 100%;
          height: 40px;
          border: 1px solid red;
          background: #fff;
          color: #f40;
          font-weight: 600;
          font-size: 18px;
        }
        @media screen and (max-width: 700px) {
          width: 100%;
          display: flex;
          position: relative;
          margin-left: 0;
          box-sizing: border-box;
          margin-bottom: 10px;
          border: none;
          .imgBox {
            width: 100px;
            height: 0;
            overflow: hidden;
            padding-bottom: 100px;
            border: 1px solid #ccc;
            box-sizing: border-box;
            img {
              width: 100%;
              height: 100px;
              padding: 2px;
              box-sizing: border-box;
            }
          }
          .title {
            padding: 0 10px;
            color: #333;
          }
          .price {
            width: 100px;
            position: absolute;
            top: 56px;
            left: 119px;
          }
          .btn {
            width: 120px;
            height: 30px;
            font-size: 14px;
            position: absolute;
            right: 10px;
            bottom: 10px;
          }
        }
      }
    }
  }
  .miniWrapper {
    .mask {
      position: fixed;
      background: rgba(0, 0, 0, 0.5);
      top: 0;
      width: 100%;
      bottom: 0;
    }
    .priceWrapper {
      position: fixed;
      top: 0;
      left: 0;
      width: 70%;
      background: #fff;
      height: 100%;
      transform: translate3d(-100%, 0, 0);
      .title {
        height: 50px;
        line-height: 50px;
        background: #ccc;
        letter-spacing: 2px;
        padding: 0 10px;
      }
      .item {
        padding: 10px 10px;
        border-bottom: 1px solid #ccc;
        &.active {
          color: #f40;
          border-left: 1px solid #f40;
        }
      }
    }
  }
}
</style>

