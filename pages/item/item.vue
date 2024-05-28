<template>
	<view v-if="goods_info.title">
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<swiper-item><image :src="goods_info.img" mode=""></image></swiper-item>
			<swiper-item><image :src="goods_info.img" mode=""></image></swiper-item>
			<swiper-item><image :src="goods_info.img" mode=""></image></swiper-item>
		</swiper>
	  <!-- 轮播图区域 -->
<!-- 	  <swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" :circular="true">
	    <swiper-item v-for="(item, i) in goods_info.pics" :key="i">
	      <image :src="item.pics_big" @click="preview(i)"></image>
	    </swiper-item>
	  </swiper> -->
	  
	  <!-- 商品信息区域 -->
	  <view class="goods-info-box">
	    <!-- 商品价格 -->
	    <view class="price">￥{{goods_info.price}}</view>
	    <!-- 信息主体区域 -->
	    <view class="goods-info-body">
	      <!-- 商品名称 -->
	      <view class="goods-name">{{goods_info.title}}</view>
	      <!-- 收藏 -->
	      <view class="favi">
	        <uni-icons type="star" size="18" color="gray"></uni-icons>
	        <text>收藏</text>
	      </view>
	    </view>
	    <!-- 运费 -->
	    <view class="yf">快递：免运费</view>
	  </view>
	  
	  <!-- 商品详情信息 -->
	  <rich-text :nodes="goods_info.content"></rich-text>
	  
	  <view class="goodinfoimg">
	  	<image :src="goods_info.goodinfoimg" mode="aspectFill"></image>
		<image :src="goods_info.goodinfoimg" mode="aspectFill"></image>
	  </view>
	  <!-- 商品导航组件 -->
	  <view class="goods_nav">
	    <!-- fill 控制右侧按钮的样式 -->
	    <!-- options 左侧按钮的配置项, 由data定义 -->
	    <!-- buttonGroup 右侧按钮的配置项, 由data定义 -->
	    <!-- click 左侧按钮的点击事件处理函数 -->
	    <!-- buttonClick 右侧按钮的点击事件处理函数 -->
	    <uni-goods-nav :fill="true" :options="options" :buttonGroup="buttonGroup" @click="onClick" @buttonClick="buttonClick" />
	  </view>
	</view>
</template>
<script setup>
	import {ref} from 'vue'
	const goods_info=uni.getStorageSync('storagItemList')[0]||[]
	console.log(goods_info)
	const itemchek=	[{
			  img: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.ivsky.com%2Fimg%2Ftupian%2Fpic%2F201611%2F14%2Fxinxing_qiaokeli-022.jpg%3Fdownload&refer=http%3A%2F%2Fimg.ivsky.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1719467515&t=619593f0dac758fed2cc7502bc4748b5',
			  title: '快乐巧克力',
			  content: '吃了会很开心。嘻嘻嘻',
			  price:'2',
			  original_price:'9',
			  id:'9'
			}]
			
		const options=ref( [{
          icon: 'shop',
          text: '店铺',
          infoBackgroundColor: '#007aff',
          infoColor: "red"
        }, {
          icon: 'cart',
          text: '购物车',
          info: 0
        }])
         const buttonGroup=ref([{
            text: '加入购物车',
            backgroundColor: '#ff0000',
            color: '#fff'
          },
          {
            text: '立即购买',
            backgroundColor: '#ffa200',
            color: '#fff'
          }
        ])
</script>

<style lang="scss">
swiper {
  height: 750rpx;

  image {
    width: 100%;
    height: 100%;
  }
}

// 商品信息区域的样式
.goods-info-box {
  padding: 10px;
  padding-right: 0;

  .price {
    color: #c00000;
    font-size: 18px;
    margin: 10px 0;
  }

  .goods-info-body {
    display: flex;
    justify-content: space-between;

    .goods-name {
      font-size: 13px;
      padding-right: 10px;
    }
    // 收藏区域
    .favi {
      width: 120px;
      font-size: 12px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      border-left: 1px solid #efefef;
      color: gray;
    }
  }

  // 运费
  .yf {
    margin: 10px 0;
    font-size: 12px;
    color: gray;
  }
}

.goods-detail-container {
  // 给页面外层的容器，添加 50px 的内padding，
  // 防止页面内容被底部的商品导航组件遮盖
  padding-bottom: 50px;
}
.goodinfoimg{
	margin-top: 20px;
	width: 100vw;
	flex-wrap: wrap;
	display: flex;
	justify-content: center;
}
.goods_nav {
  // 为商品导航组件添加固定定位
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
}
</style>

