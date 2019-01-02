<template>
  <div>
    <swiper class="swiper" indicator-dots="true" autoplay="true" interval="5000" duration="1000">
      <block v-for="(item, index) in movies" :index="index" :key="item.id">
          <swiper-item>
            <image style="width: 100%;" :src="item.url" class="slide-image" mode="aspectFill"/>
          </swiper-item>
      </block>
    </swiper>
    <div>
      <i-grid class="grid">
        <i-grid-item>
          <i-grid-icon>
            <image src="/static/image/lx-20.png" />
          </i-grid-icon>
          <i-grid-label>游玩经典</i-grid-label>
        </i-grid-item>
        <i-grid-item>
          <i-grid-icon>
            <image src="/static/image/lx-17.png" />
          </i-grid-icon>
          <i-grid-label>品尝佳肴</i-grid-label>
        </i-grid-item>
        <i-grid-item>
          <i-grid-icon>
            <image src="/static/image/lx-07.png" />
          </i-grid-icon>
          <i-grid-label>购买特产</i-grid-label>
        </i-grid-item>
        <i-grid-item>
          <i-grid-icon>
            <image src="/static/image/lx-16.png" />
          </i-grid-icon>
          <i-grid-label>预订酒店</i-grid-label>
        </i-grid-item>
      </i-grid>
    </div>
    <div class="view">
      <div class="view__title">
        <span>网红最常去的旅游圣地<i-icon type="enterinto_fill" size="20" color="#ccc;"/></span>
        <div>跟着网红去拍照</div>
      </div>
      <div class="view_box" v-for="item in viewList" :key="item.id">
        <div style="margin-right:20px;">
          <image :src="item.one" style="width: 400rpx; height: 300rpx"/>
        </div>
        <div>
          <image :src="item.two" style="width: 400rpx; height: 200rpx"/>
        </div>
      </div>
    </div>
    <div class="view">
      <div class="view__title">
        <span>最适合冬天旅行的目的地<i-icon type="enterinto_fill" size="20" color="#ccc;"/></span>
        <div>拼假也要去旅行</div>
      </div>
      <div class="view_box" v-for="item in moreList" :key="item.id">
        <div style="margin-right:20px;">
          <image :src="item.one" style="width: 400rpx; height: 300rpx"/>
        </div>
        <div>
          <image :src="item.two" style="width: 400rpx; height: 200rpx"/>
        </div>
      </div>
    </div>
    <div class="food">
      <div class="food__title">
          <span>花样吃吃吃<i-icon type="enterinto_fill" size="20" color="#ccc;"/></span>
          <div>丰富你的选择</div>
        </div>
      <div class="food_box">
        <div class="food_box__item" v-for="food in foodList" :key="food.id">
          <image :src="food.src"/>
          <div>{{food.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  components: {
    card
  },

  data () {
    return {
      current: 'homepage',
      viewList: [
        {
          one: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=489591771,1695524585&fm=26&gp=0.jpg',
          two: 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2464109929,3545948268&fm=26&gp=0.jpg'
        },
        {
          one: 'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3611792794,592463012&fm=26&gp=0.jpg',
          two: 'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3274313163,862714568&fm=26&gp=0.jpg'
        }
      ],
      moreList: [
        {
          one: 'https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=427997177,2739600827&fm=26&gp=0.jpg',
          two: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=4238358512,3459763858&fm=200&gp=0.jpg'
        },
        {
          one: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=91275238,2645114128&fm=26&gp=0.jpg',
          two: 'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=3119250423,2065825878&fm=26&gp=0.jpg'
        }
      ],
      movies: [
        {
          url: 'https://img1.qunarzz.com/travel/d9/1802/cf/328549d2f08af5b5.jpg_r_480x360x95_aad24c77.jpg'
        },
        {
          url: 'https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=2416897504,3073698136&fm=11&gp=0.jpg'
        },
        {
          url: 'https://img1.qunarzz.com/travel/d5/1712/ba/172445995331aeb5.jpg_r_480x360x95_b1d5fd05.jpg'
        },
        {
          url: 'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=3245270355,2969010469&fm=26&gp=0.jpg'
        },
        {
          url: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=2411998569,1547714135&fm=11&gp=0.jpg'
        },
        {
          url: 'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=1640349675,2159677460&fm=200&gp=0.jpg'
        }
      ],
      foodList: [
        {
          src: 'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=2948663808,202877815&fm=26&gp=0.jpg',
          name: '大救驾'
        },
        {
          src: 'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=1557958638,1491531336&fm=26&gp=0.jpg',
          name: '鲜花饼'
        },
        {
          src: 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=1032073422,1539628041&fm=15&gp=0.jpg',
          name: '烧豆腐'
        },
        {
          src: 'https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=1288030138,2036452950&fm=26&gp=0.jpg',
          name: '过桥米线'
        },
        {
          src: 'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3834448494,1806541469&fm=26&gp=0.jpg',
          name: '野生菌'
        },
        {
          src: 'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=1323280238,3418588773&fm=26&gp=0.jpg',
          name: '甜石榴'
        }
      ]
    }
  },
  created () {
  },
  method: {
    handleChange (detail) {
      this.current = detail.key
    }
  }
}
</script>

<style lang="scss">>
.log-list {
  display: flex;
  flex-direction: column;
  padding: 40rpx;
}

.log-item {
  margin: 10rpx;
}
.swiper {
  height: 400rpx;
}
.grid {
  margin-bottom: 70rpx;
  image{
    width: 100rpx;
    height: 100rpx;
  }
  i-grid-label{
    font-size: 12px;
    color: #ccc;
  }
}
.view {
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #777;
  font-weight: 300;
  box-shadow: 0 5px 15px #ccc;
  padding-top: 20px;
  &_box {
    display: flex;
    flex-direction: row;
    align-items: center;
    margin-bottom: 20px;
    image {
      border-radius: 6px;
    }
  }
  &__title {
    font-size: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 30px;
    div {
      font-size: 14px;
    }
  }
}
.food {
  color: #777;
  font-weight: 300;
  border-top: 2px solid #eee;
  padding: 20px 10px 10px 10px;
  &_box {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: space-between;
  margin-bottom: 60px;
  &__item {
      margin-bottom: 30px;
      display: flex;
      flex-direction: column;
      align-items: center;
      image {
      border-radius: 6px;
      width: 220rpx;
      height: 220rpx;
      }
      div {
        font-size: 12px;
      }
    }
  }
  &__title {
    font-size: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-bottom: 30px;
    div {
      font-size: 14px;
    }
  }
}
</style>
