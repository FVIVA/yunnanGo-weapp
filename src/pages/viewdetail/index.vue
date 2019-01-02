<template>
  <div>
    <div class="title_img" >
      <swiper class="swiper" autoplay="true" interval="5000" duration="1000">
        <block v-for="(item, index) in viewInfo.images" :index="index" :key="item.id">
            <swiper-item>
              <image style="width: 100%;" :src="item.url" class="slide-image" mode="aspectFill"/>
            </swiper-item>
        </block>
      </swiper>
    </div>
    <div class="des">
      <span class="des__title"><strong>{{viewInfo.view_name}}</strong></span>
      <span class="des__rate">
        推荐指数：
         <i-cell>
            <i-rate 
                :disabled="true"
                :value="viewInfo.rate">
            </i-rate>
        </i-cell>
      </span>
      <div class="des__detail">{{viewInfo.des_detail}}</div>
    </div>
    <div class="guides">
      <span class="des__title"><strong>攻略</strong></span>
      <i-notice-bar icon="systemprompt" color="#666" background-color="#cccccc" loop>
        {{viewInfo.guides.notice}}
      </i-notice-bar>
      <i-collapse :name="currentCollapse">
        <i-collapse-item
            name="time"
            title="最佳旅游时间"
            i-class-title="guides__title">
          <view slot="content" class="guides__title">
           {{viewInfo.guides.time}}
          </view>
        </i-collapse-item>
        <i-collapse-item
            name="traffic"
            title="交通路线"
            i-class-title="guides__title">
          <view slot="content" class="guides__title">
            <map-route :route-info="routeInfo" style=""></map-route>
          </view>
        </i-collapse-item>
      </i-collapse>
    </div>
    <div class="footer">
      <i-button bind:click="handleClick" type="success" shape="circle">收藏</i-button>
    </div>
  </div>
</template>
<script>
let plugin = requirePlugin('mapPlugin')
export default {
  data () {
    return {
      msg: 'map向你问好！',
      ak: 'AQbnj0CLeEwawuI9Ep6PxcoXgzwPPmMr',
      routeInfo: {},
      currentCollapse: 'time',
      viewInfo: {
        images: [
          {
            url: 'https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=3071936428,416441458&fm=11&gp=0.jpg'
          },
          {
            url: 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=30686527,2552501798&fm=26&gp=0.jpg'
          },
          {
            url: 'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=2191757348,1263564221&fm=26&gp=0.jpg'
          },
          {
            url: 'https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=626573449,3602848114&fm=26&gp=0.jpg'
          },
          {
            url: 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=3144994808,2728675571&fm=26&gp=0.jpg'
          },
          {
            url: 'https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=3680688129,3013275455&fm=26&gp=0.jpg'
          }
        ],
        view_name: '云南丽江',
        rate: 5,
        des_detail: '丽江是一个多民族聚居的地方，除汉族外，共有12个世居少数民族，22种少数民族；丽江是著名的旅游城市，拥有世界文化遗产丽江古城、世界自然遗产三江并流、世界记忆遗产纳西族东巴古籍文献三大世界遗产。 [1]  旅游资源丰富，有旅游风景点104处，有丽江古城、玉龙雪山、虎跳峡、老君山、束河古镇等知名旅游景点。 [4]  先后被评为中国旅游竞争力百强城市 [5]  、中国十大休闲城市 [6]  、中国优秀旅游城市 [7]  、中国十大魅力城市 [8]  、云南省人才特区 [9]  、长江经济带上的绿色明珠 [10]  等荣誉称号。',
        guides: {
          lat: 26.8707467733,
          lng: 100.2367112522,
          notice: '12月21日至12月31日,印象丽江停演11天，对剧场设备设施进行例行维护保养，2019年1月1日恢复正常演出。2019年1月1日起，面向游客收取的丽江古城维护费由每人次80元降为50元。',
          time: ' 每年的5-10月时旅游旺季，这里的夏天不算热，如果下起雨来还会有点凉，气温舒适，是避暑的去处之一。此时丽江周边水草丰茂，草原、森林也都进入了繁盛的季节。不过这时候丽江及周边景点的游人也会非常多。'
        }
      }
    }
  },

  onShow () {
    wx.hideTabBar({
      animation: true
    })
    let routeInfo = {
      startLat: 0,
      startLng: 0,
      startName: '我的位置',
      endLat: this.viewInfo.guides.lat,
      endLng: this.viewInfo.guides.lng,
      endName: this.viewInfo.view_name,
      mode: 'car'
    }
    this.routeInfo = routeInfo
    console.log(plugin)
  }
}
</script>
<style lang="scss">
.title_img {
  .swiper {
    height: 400rpx;
  }
}
.des {
  padding:40rpx;
  color: #4a4a4a;
  span {
    display: block;
  }
  &__title {
    font-size: 40rpx;
  }
  &__rate {
    margin-top: 20rpx;
    font-size: 28rpx;
  }
  &__detail {
    margin-top: 20rpx;
    font-size: 30rpx;
    line-height: 60rpx;
    text-indent: 2em;
    text-align: justify;
  }
}
.guides {
  padding:40rpx;
  margin-bottom: 100rpx;
  color: #4a4a4a;
  &__title {
    font-size: 30rpx;
  }
  &__cotent {
    font-size: 26rpx;
    line-height: 40rpx;
    margin-top: 20rpx;
  }
  .mapRoute--route-map {
    width: 600rpx;
  }
  .mapRoute--multi-page {
    width: 600rpx;
  }
}
.footer {
  width: 100%;
  color: #fff;
  position: fixed;
  bottom: 20rpx;

}
</style>
