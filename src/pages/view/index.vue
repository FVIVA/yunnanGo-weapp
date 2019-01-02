<template>
  <div>
     <i-swipeout v-for="item in viewList" :key="item.id" i-class="i-swipeout-demo-item" :actions="actions">
        <view slot="content">
            <i-cell i-class="i-cell-padding">
              <div class="view"  :style="{backgroundImage: 'url(' + item.url + ')', backgroundSize:'cover'}">
                <div class="view__des">
                  <h2>{{item.name_des}}</h2>
                </div>
                <div class="view__title" @click="openViewDetail(item.id)">{{item.name}}</div>
              </div>
            </i-cell>
        </view>
    </i-swipeout>
    
  </div>
</template>
<script>
export default {
  data () {
    return {
      actions: [
        {
          name: '喜欢',
          color: '#fff',
          fontsize: '20',
          width: 100,
          icon: 'like',
          background: '#ed3f14'
        },
        {
          name: '返回',
          width: 100,
          color: '#80848f',
          fontsize: '20',
          icon: 'undo'
        }
      ],
      viewList: [
        {
          url: 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=3497792468,3803651963&fm=26&gp=0.jpg',
          name: '丽江',
          name_des: '来一次古镇艳遇',
          id: 1
        },
        {
          url: 'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=84801433,4156259513&fm=26&gp=0.jpg',
          name: '大理',
          name_des: '苍山洱海风花雪月'
        },
        {
          url: 'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=1213962358,4030431597&fm=26&gp=0.jpg',
          name: '西双版纳',
          name_des: '骑着大象去旅行'
        },
        {
          url: 'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=114241927,892132782&fm=26&gp=0.jpg',
          name: '元阳梯田',
          name_des: '带上心爱的人看日出'
        },
        {
          url: 'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3277376878,2281131193&fm=26&gp=0.jpg',
          name: '普者黑',
          name_des: '三生三世，十里桃花'
        }
      ]
    }
  },
  methods: {
    openViewDetail (id) {
      let url = `../viewdetail/main?id=${id}`
      // let url = '../viewdetail/main'
      wx.navigateTo({url})
      console.log(url)
    }
  }
}
</script>
<style lang="scss">
.view {
  width: 100%;
  height: 500rpx;
  vertical-align: bottom;
  color: #fff;
  padding: 1rpx;
  &__des {
    height: 70rpx;
    width: 60%;
    text-align: center;
    font-size: 24px;
    margin: 0 auto;
    margin-top: 250rpx;
    font-weight: 200;

  }
  &__title{
    height: 60rpx;
    width: 40%;
    border-radius: 6px;
    margin: 0 auto;
    margin-top: 20rpx;
    background: rgba($color: #000000, $alpha: 0.4);
    text-align: center;
    line-height: 70rpx;
    font-size: 20px;
    font-weight: 300;
  }
}
</style>

