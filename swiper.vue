<template>
  <view class="company_banner">
    <swiper
      :circular="circular?true:false"
      :autoplay="autoplay?true:false"
      :interval="interval?interval:3000"
      :duration="duration?duration:1000"
      :indicator-dots="dots?true:false"
      previous-margin="20"
      next-margin="20"
      style="margin-top:20rpx;height:300rpx"
      @change="change"
    >
      <swiper-item
        style="top:0;bottom:0;left:0;right:0;margin:auto;"
        class="swiper_item"
        v-for="(item,index) in swiperList"
        :key="index"
      >
        <view
          :class="index==tap+1?'active_left':index==swiperList.length?'active_right':index==tap?'':tap==swiperList.length-1&&index==0?'active_left':'active_right'"
          class="img_box"
          style="background: rgba(255, 255, 255, 1);;height:100%"
        >
          <image class="image" :src="item" mode />
          <!-- <view class="company_name">{{item.title}}</view> -->
          <!-- <view class="company_verb">{{item.subtitle}}</view> -->
        </view>
      </swiper-item>
    </swiper>
  </view>
</template>

<script>
export default {
  props: {
    dots: Boolean,
    circular: Boolean,
    autoplay: Boolean,
    interval: String,
    duration: String,
    swiperList: Array,
  },

  data() {
    return {
      tap: 0,
    };
  },
  mounted() {
    let t = this;
  },
  methods: {
    change(e) {
      let t = this;
      t.tap = e.detail.current;
    },
    togo() {
      console.log(1);
    },
  },
};
</script>

<style  lang="scss" scoped>
/* 合作伙伴轮播 */
.company_banner {
  margin-top: 10rpx;
  padding-bottom: 20rpx;
  width: 100%;
  // height: 445rpx;
  box-sizing: border-box;
  background-color: var(--moduleBgc);
  .swiper_item {
    padding: 0rpx 10rpx;
    box-sizing: border-box;
    .img_box {
      position: relative;
      height: 100%;
      border-radius: 20px;
      overflow: hidden;
      background: rgba(255, 255, 255, 1);
      transition: all 1s;
      .image {
        width: 100%;
        height: 100%;
      }
      .company_name {
        position: absolute;
        top: 100rpx;
        left: 235rpx;
        color: #fff;
        font-size: var(--companyNameSize);
        font-family: PingFang SC;
      }
      .company_verb {
        position: absolute;
        margin: 0 auto;
        left: 0;
        right: 0;
        bottom: 30rpx;
        width: 530rpx;
        color: #d9d9d9;
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-line-clamp: 2;
        -webkit-box-orient: vertical;
        font-size: var(--companyVerpSize);
        font-family: PingFang SC;
        line-height: 32rpx;
        color: #d6d6d6;
      }
    }
  }
  .active_left {
    transform: scale(0.8);
    transform-origin: left;
    transition: all 1s;
  }
  .active_right {
    transform: scale(0.8);
    transform-origin: right;
    transition: all 1s;
  }
}
</style>