<template>
  <div>
    
    <div style="width:100%; text-align:center; margin: 60rpx 0;"><h2>精选商品</h2></div>
    <div class="goods">
      <div class="goods__item" v-for="item in goodList" :key="item.id">
        <div class="goods__item_right" :style="{backgroundImage: 'url(' + item.url + ')', backgroundSize:'cover'}"></div>
        <div class="goods__item_left">
          <div class="goods__title">{{item.name}}</div>
          <div class="goods__des">{{item.des}}</div>
          <div class="goods__price"><span style="font-size: 28rpx;">¥</span> {{item.price}} /<span style="font-size: 28rpx;">{{item.weight}}g</span></div>
          <div class="goods__buy">
            <i-button @click="buy(item.price)" size="small" type="warning">立即购买</i-button>
          </div>
        </div>
      </div>
    </div>
    
      <div class="car__box" @click="openCar">
        <i-badge :count="count">
          <image style="height: 80rpx; width: 80rpx;" class="car" src="/static/image/car.png" />
        </i-badge>
      </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      count: 0,
      goodList: [
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '鲜花饼',
          des: 'dakjgekwjl',
          price: 80,
          weight: 500
        },
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '鲜花饼',
          des: 'dakjgekwjl',
          price: 80,
          weight: 500
        },
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '鲜花饼',
          des: 'dakjgekwjl',
          price: 80,
          weight: 500
        },
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '鲜花饼',
          des: 'dakjgekwjl',
          price: 80,
          weight: 500
        },
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '鲜花饼',
          des: 'dakjgekwjl',
          price: 80,
          weight: 500
        },
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '鲜花饼',
          des: 'dakjgekwjl',
          price: 80,
          weight: 500
        },
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '鲜花饼',
          des: 'dakjgekwjl',
          price: 80,
          weight: 500
        },
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '鲜花饼',
          des: 'dakjgekwjl',
          price: 80,
          weight: 500
        }
      ]
    }
  },
  methods: {
    buy (price) {
      this.count++
    },
    openCar () {
      let url = '../car/main'
      wx.navigateTo({url})
    }
  }
}
</script>
<style lang="scss">

.goods {
  width: 100%;
  height: auto;
  padding: 20rpx;
  &__item {
    height: 250rpx;
    margin-bottom: 30rpx;
    &_right {
      height: 250rpx;
      width: 45%;
      float: left;
      margin-right: 20rpx;
    }
    &_left {
      height: 250rpx;
      float: left;
      width: 50%;
      line-height: 55rpx;
      .goods__des {
        color: #999;
        font-size: 28rpx;
      }
      .goods__buy {
        width: 200rpx;
      }
    }
  }
}
.car__box {
  width: 80rpx;
  height: 80rpx;
  border-radius: 50%;
  background-color: #06c1ae;
  position: fixed;
  bottom: 40rpx;
  right: 40rpx;
  .car{
    width: 80rpx;
    height: 80rpx;
  }
}
</style>
