<template>
			<view class="content">
				<view class="list" v-for="(item, index) in itemList" :key="item.id" @click="gopreview(item.id)">
					<image mode="widthFix" :src="item.img"></image>
					<view class="title">{{ item.title }}</view>
					<view class="con">{{ item.synopsis }}</view>
					
					<view class="con_one">
						<view class="con_one_one">￥{{ item.price }}</view>
						<view class="con_one_two">
							<s>￥{{ item.original_price }}</s>
						</view>
					</view>
					
				</view>
			</view>
</template>
			
<script setup>
	import {ref} from 'vue'
	       const itemList=[
	        {
	          img: 'https://file03.16sucai.com/2017/1100/16sucai_p566c071_307.JPG',
	          title: '松仁巧克力',
	          content: '好像是坏越最喜欢的巧克力？听说产生在那个山的那边海的那边的都是省速度市，甜美的青山水和令人陶醉的可可',
			  price:'2',
			  original_price:'6',
			  id:'1',
			  goodinfoimg:'https://img2.baidu.com/it/u=4217825575,3521188604&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=708'
	        },
	        {
	          img: 'https://img1.baidu.com/it/u=4169556851,3455102274&fm=253&fmt=auto&app=138&f=JPEG?w=667&h=500',
	          title: '德芙巧克力',
	          content: '传说中最物美价廉的巧克力，听说产生在那个山的那边海的那边的都是省速度市，甜美的青山水和令人陶醉的可可',
			  price:'1',
			  original_price:'7',
			  id:'2',
			  goodinfoimg:'https://img2.baidu.com/it/u=4217825575,3521188604&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=708'
	        },
	        {
	          img: 'https://img0.baidu.com/it/u=1135608079,1041890161&fm=253&fmt=auto&app=138&f=JPEG?w=800&h=500',
	          title: '白巧克力',
	          content: '这巧克力真白~听说产生在那个山的那边海的那边的都是省速度市，甜美的青山水和令人陶醉的可可',
			  price:'3',
			  original_price:'8',
			  id:'3',
			  goodinfoimg:'https://img2.baidu.com/it/u=4217825575,3521188604&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=708'
	        },
	        {
	          img: 'https://img1.baidu.com/it/u=2795270876,536929854&fm=253&fmt=auto&app=138&f=JPEG?w=603&h=385',
	          title: '快乐巧克力',
	          content: '吃了会很开心。嘻嘻嘻，听说产生在那个山的那边海的那边的都是省速度市，甜美的青山水和令人陶醉的可可',
			  price:'2',
			  original_price:'9',
			  id:'4',
			  goodinfoimg:'https://img2.baidu.com/it/u=4217825575,3521188604&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=708'
	        },
	        {
	          img: 'https://img1.baidu.com/it/u=2795270876,536929854&fm=253&fmt=auto&app=138&f=JPEG?w=603&h=385',
	          title: '悲伤巧克力',
	          content: '吃了会特别想哭，呜呜呜呜',
			  price:'4',
			  original_price:'5',
			  id:'5',
			  goodinfoimg:'https://img2.baidu.com/it/u=4217825575,3521188604&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=708'
	        },
			{
			  img: 'https://img0.baidu.com/it/u=1135608079,1041890161&fm=253&fmt=auto&app=138&f=JPEG?w=800&h=500',
			  title: '德芙巧克力',
			  content: '传说中最物美价廉的巧克力，听说产生在那个山的那边海的那边的都是省速度市，甜美的青山水和令人陶醉的可可',
			  price:'1',
			  original_price:'7',
			  id:'6',
			  goodinfoimg:'https://img2.baidu.com/it/u=4217825575,3521188604&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=708'
			},
			{
			  img: 'https://img0.baidu.com/it/u=1135608079,1041890161&fm=253&fmt=auto&app=138&f=JPEG?w=800&h=500',
			  title: '白巧克力',
			  content: '这巧克力真白~听说产生在那个山的那边海的那边的都是省速度市，甜美的青山水和令人陶醉的可可',
			  price:'3',
			  original_price:'8',
			  id:'7',
			  goodinfoimg:'https://img2.baidu.com/it/u=4217825575,3521188604&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=708'
			},
			{
			  img: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.ivsky.com%2Fimg%2Ftupian%2Fpic%2F201611%2F14%2Fxinxing_qiaokeli-022.jpg%3Fdownload&refer=http%3A%2F%2Fimg.ivsky.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1719467515&t=619593f0dac758fed2cc7502bc4748b5',
			  title: '快乐巧克力',
			  content: '吃了会很开心。嘻嘻嘻，听说产生在那个山的那边海的那边的都是省速度市，甜美的青山水和令人陶醉的可可',
			  price:'2',
			  original_price:'9',
			  id:'8',
			  goodinfoimg:'https://img2.baidu.com/it/u=4217825575,3521188604&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=708'
			},
			{
			  img: 'https://gimg2.baidu.com/image_search/src=http%3A%2F%2Fimg.ivsky.com%2Fimg%2Ftupian%2Fpic%2F201611%2F14%2Fxinxing_qiaokeli-022.jpg%3Fdownload&refer=http%3A%2F%2Fimg.ivsky.com&app=2002&size=f9999,10000&q=a80&n=0&g=0n&fmt=auto?sec=1719467515&t=619593f0dac758fed2cc7502bc4748b5',
			  title: '快乐巧克力',
			  content: '吃了会很开心。嘻嘻嘻，听说产生在那个山的那边海的那边的都是省速度市，甜美的青山水和令人陶醉的可可',
			  price:'2',
			  original_price:'9',
			  id:'9',
			  goodinfoimg:'https://img2.baidu.com/it/u=4217825575,3521188604&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=708'
			}
	      ]
	const gopreview=(id)=>{
		const iteminfo=itemList.filter(item=>item.id==id)
		uni.setStorageSync('storagItemList',iteminfo)
		uni.navigateTo({
			url:"/pages/item/item?id="+id
		})
	}
</script>
<style scoped>
	
	.list {
			break-inside: avoid;
			width: 330rpx;
			border: 1px solid #f4f4f4;
			margin-top: 10px;
			border-radius: 20rpx;
		}
	 
		.con {
			color: #8b8d8c;
			overflow: hidden;
			/*超出部分隐藏*/
			white-space: nowrap;
			/*禁止换行*/
			text-overflow: ellipsis;
			margin-left: 15rpx;
			margin-right: 15rpx;
			font-size: 26rpx;
		}
	 
		.title {
			margin-left: 15rpx;
			margin-right: 15rpx;
			font-size: 26rpx;
			color: #8b8d8c;
			overflow: hidden;
			/*超出部分隐藏*/
			white-space: nowrap;
			/*禁止换行*/
			text-overflow: ellipsis;
		}
	 
		/* 内容区 */
		.content {
			padding: 30rpx;
			box-sizing: border-box;
			column-count: 2;
		}
	 
		image {
			width: 100%;
			border-radius: 6rpx;
		}
</style>
