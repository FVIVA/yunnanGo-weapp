<template>
  <div style="background: #ccc; height: auto;">
    <div class="food__top">
      <div class="food__top_box">
        <div class="food__top_content">
          <h3>云南</h3>
          <h3>YUNNAN</h3>
        </div>
      </div>
    </div>
    <div class="food__item">
      <div class="food__item_title">必吃TOP10</div>
      <div class="food__item_img">
        <span @click="openDetail(item)"  v-for="item in mustFoodList" :key="item.id" :style="{backgroundImage: 'url(' + item.url + ')', backgroundSize:'cover'}">
          {{item.name}}
        </span>
      </div>
    </div>
    <div class="food__item">
      <div class="food__item_title">美食老店推荐</div>
      <div @click="toDetail" class="food__item_img" style="background: #ff5a5f; height: 300rpx;">
      </div>
    </div>
    <div class="food__item">
      <div class="food__item_title">更多美食</div>
      <div class="food__item_img" style="margin-bottom: 20rpx; height: 450rpx;" v-for="item in moreFoodList" :key="item.id" :style="{backgroundImage: 'url(' + item + ')', backgroundSize:'cover',marginBottom: '20'+ 'rpx', height: '450' + 'rpx'}">
      </div>
    </div>
    <div class="food_detail">
		  <rule-modal v-model="show" :food="currentFood"></rule-modal>
      <!-- <i-action-sheet :visible="visible1" :actions="actions1" show-cancel @cancel="visible1 = false" /> -->
    </div>
  </div>
</template>
<script>
import RuleModal from '../../components/RuleModal'
export default {
  components: {
    RuleModal
  },
  data () {
    return {
      show: false,
      currentFood: {},
      visible1: false,
      actions1: [
        {
          name: '选项1'
        },
        {
          name: '去分享',
          icon: 'share',
          openType: 'share'
        }
      ],
      mustFoodList: [
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '过桥米线',
          detail: '“过桥米线”是云南滇南地区特有的食品，已有百多年历史，五十多年前传至昆明。过桥米线由四部分组成：一是汤料覆盖有一层滚油；二是佐料，有油辣子、味精、胡椒、盐；三是主料，有生的猪里脊肉片、鸡脯肉片、乌鱼片，以及用水过五成熟的猪腰片、肚头片、水发鱿鱼片；辅料有来过的豌豆尖、韭菜，以及芫荽、葱丝、草芽丝、姜丝、玉兰片、氽过的豆腐皮；四是主食，即用水略烫过的米线。鹅油封面，汤汁滚烫，但不冒热气。'
        },
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '过桥米线'
        },
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '过桥米线'
        },
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '过桥米线'
        },
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '过桥米线'
        },
        {
          url: 'http://temp.im/100x100/ff5a5f',
          name: '过桥米线'
        }
      ],
      moreFoodList: [
        'http://temp.im/400x500/ff5a5f',
        'http://temp.im/400x500/ff5a5f',
        'http://temp.im/400x500/ff5a5f',
        'http://temp.im/400x500/ff5a5f',
        'http://temp.im/400x500/ff5a5f',
        'http://temp.im/400x500/ff5a5f'
      ]
    }
  },
  methods: {
    openDetail (food) {
      this.show = true
      this.currentFood = food
    },
    toDetail () {
      let url = '../goodDetail/main'
      wx.navigateTo({url})
    }
  }
}
</script>
<style lang="scss">
.food__top {
  width: 100%;
  height: 550rpx;
  position: relative;
  background: url('https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1403163503,2517611253&fm=26&gp=0.jpg');
  background-size: cover;
  &_box{
    width: 33%;
    height: 150rpx;
    background: rgba($color: #fff, $alpha: 0.8);
    padding: 20rpx;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%,-50%);
    line-height: 75rpx;
  }
  &_content{
    height: 100%;
    border: 1px solid #444;
    text-align: center;
    vertical-align: middle;
  }
}
.food__item {
  &_title {
    width: 100%;
    height: 60rpx;
    border-left: orange 10rpx solid;
    background: #fff;
    padding-left: 20rpx;
    line-height: 60rpx;
    margin-top: 20rpx;
  }
  &_img {
    white-space: nowrap;
    overflow-x: scroll;
    height: 220rpx;
    width: auto;
    background: #fff;
    span {
      display: inline-block;
      height: 200rpx;
      width: 200rpx;
      text-align: center;
      vertical-align: middle;
      margin-right: 20rpx;
      line-height: 200rpx;
    }
  }
}
.food__detail {
  .i-as-action-item {
    .i-btn-large {
      height: 200rpx;
    }
  }
}
</style>
