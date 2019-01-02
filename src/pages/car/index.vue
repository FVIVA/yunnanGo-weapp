<template>
  <div>
    <dl class="ub-box z-padding-all-10-px" style="background:#fff">
      <dd class="ub-box ub-ver">
        <image :src="userInfo.avatarUrl" class="head-img" mode="aspectFill" />
      </dd>
      <dd class="ub-flex-1 z-font-size-18 z-color-333 ub-box ub-ver-v z-padding-h-10-px">
        <button v-if="isLogin===false"
          class="loginBtn"
          lang="zh_CN"
          open-type="getUserInfo"
          @getuserinfo="onGetUserInfo">登录</button>
        <ul v-if="isLogin===true" class="ub-box z-margin-left-10-px ub-col">
          <li class="z-font-size-16 z-color-333 z-margin-bottom-5-px">{{userInfo.nickName}}</li>
          <li class="z-font-size-14 z-color-888">{{userInfo.province}} {{userInfo.city}} {{userInfo.gender}}</li>
        </ul>
      </dd>
      <dd class="z-font-size-18 z-color-333 ub-box ub-ver-v">
        <div v-if="isLogin===true" @click.stop="exitLogin()" class="exitBtn ub-box ub-ver z-font-size-14">退出</div>
      </dd>
    </dl>
    <div class="car" v-if="isLogin===true">
      <div v-if="carList.length === 0" style="width:100%; text-align: center;">购物车空空</div>
      <!-- <div class="car__item" v-for="item in carList" :key="item.id">
        <i-row>
          <i-col span="4" i-class="col-class">
            <div>
              <checkbox-group  >
                <checkbox :value="item.price" @click="checkboxChange"></checkbox>
              </checkbox-group>
            </div>
          </i-col>
          <i-col span="6" i-class="col-class">col-8</i-col>
          <i-col span="14" i-class="col-class">col-8</i-col>
        </i-row>
      </div> -->
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      checked: false,
      allPrice: 0,
      carList: []
    }
  },
  computed: {
    isLogin () {
      return this.$store.state.isLogin
    },
    userInfo () {
      return this.$store.state.userInfo
    }
  },
  methods: {
    onGetUserInfo (e) {
      this.$store.commit('updateIsLogin', true)
      this.$store.commit('updateUser', e.mp.detail.userInfo)
    },
    exitLogin () {
      this.$store.commit('updateIsLogin', false)
      this.$store.commit('cleanUserInfo')
    },
    checkboxChange (e) {
      console.log(e)
      // this.checked = !this.checked
    }
  }
}
</script>
<style lang="scss">
.head-img {
  width: 70px;
  height: 70px;
  border-radius: 50%;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
  background: #eee;
}
.loginBtn {
  font-size: 14px;
  color: #fff;
  padding: 0px 20px;
  margin-left: 10px;
  background: #ff5722;
}
.exitBtn {
  border: 1px solid #06c1ae;
  padding: 7px 15px;
  color: #06c1ae;
  border-radius: 3px;
}
.car {
  padding: 40rpx;
  &__item {
    
  }
}
</style>
