<template>
    <div class="map">
        <image mode="aspectFit" class="head-img" src="../../static/images/t1.png"/>
        <map class="content" id="map" longitude="114.690590" latitude="37.005380" :markers="markers" scale="18" @tap="toNav">
        </map>
        <div class="call">
            <div class="left">
                  <button
                    class="online-seek"
                    :session-from="sobot|userInfo.nickName|userInfo.avatarUrl"
                    open-type="contact">
                    <image src="../../static/images/he.png"/>
                    <div>联系新郎</div>
                  </button>
            </div>
            <div class="left" @tap="linkHe">
                <image src="../../static/images/he.png"/>
                <span>呼叫新郎</span>
            </div>
            <div class="right" @tap="linkShe">
                <image src="../../static/images/she.png"/>
                <span>呼叫新娘</span>
            </div>
        </div>
        <image class="footer" src="../../static/images/grren-flower-line.png"/>
        <div class="copyright">
          <div>made with 💗 by fengxiongwei</div>
          <div>© copyright 2019</div>
        </div>
    </div>
</template>

<script>
// import QQMap from 'common/js/qqmap-wx-jssdk.js'
export default {
  name: 'Map',
  data () {
    return {
      // qqSdk: '',
      // 37.005380,114.690590
      markers: [{
        iconPath: '../../static/images/nav.png',
        id: 0,
        latitude: 37.005380,
        longitude: 114.690590,
        width: 50,
        height: 50
      }]
    }
  },
  onShareAppMessage (res) {
    // const that = this
    // const db = wx.cloud.database()
    // const shareImg = db.collection('shareImg')
    // shareImg.get().then(res => {
    //   that.imgUrl = res.data[0].img
    // })
    return {
      title: '恭候您的光临',
      path: '/pages/index/main',
      imageUrl: '../../static/images/share.jpg'
    }
  },
  methods: {
    toNav () {
      wx.openLocation({
        latitude: 114.697284,
        longitude: 37.011046,
        scale: 18
      })
    },

    linkHe () {
      wx.makePhoneCall({
        phoneNumber: '17611169059'
      })
    },

    linkShe () {
      wx.makePhoneCall({
        phoneNumber: '18713570873'
      })
    }
  }
}
</script>

<style lang="stylus" scoped>
@-webkit-keyframes infoAnimation
  0%
    -webkit-transform scale(1)
  50%
    -webkit-transform scale(.9)
  100%
    -webkit-transform scale(1)
.map
    height 100%
    background #fff
    .head-img
      width 100%
      height 180rpx
      margin-bottom 50rpx
      animation infoAnimation 6s linear infinite
    .content
      width 690rpx
      margin-left 30rpx
      height 600rpx
      margin-bottom 30rpx
      border-radius 16rpx
    .call
      display flex
      justify-content space-around
      align-items center
      width 100%
      margin-bottom 20rpx
      .left, .right
        flex 1
        display flex
        flex-direction column
        justify-content center
        align-items center
        image
          height 64rpx
          width 64rpx
          margin 0 auto
        span
          height 50rpx
          line-height 50rpx
          font-size 24rpx
          color #6B4F4E
        button::after
          border none
        button
          background #ffffff
          color #6B4F4E
          font-size 24rpx
    .footer
      height 80rpx
      width 716rpx
      margin-left 17rpx
    .copyright
      margin-top 20rpx
      width 100%
      display flex
      flex-direction column
      align-items center
      justify-content center
      div
        height 30rpx
        line-height 30rpx
        font-size 20rpx
        color #6B4F4E
</style>
