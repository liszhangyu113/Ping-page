<template>
<!-- ---------------------------------播放页面 -->
	<view class="page">
		<!-- 导航栏 -->
		<view class="nav">
			<image class="fh" src="../../../../static/playing/返回.png"></image>
			<text class="title">探索-认知迭代</text>
			<image class="sq" src="../../../../static/playing/收起.png"></image>
		</view>
		<!-- 图片、控制条 -->
		<view class="content"> 
			<view class="tupian">
				<image class="ren" src="../../../../static/playing/人像.png"></image>
				<!-- 定时播放、快速播放 -->
				<view class="playD">
					<view class="view1">
						<image src="../../../../static/playing/定时播放.png"></image>
						<text>定时播放</text>
					</view>
					<view class="view2">
						<image src="../../../../static/playing/闪电播放.png"></image>
						<text>快速播放</text>
					</view>
				</view>
			</view>
			<!-- 进度条 -->
			<view class="progress">
				<view class="left progress1"><!-- 左图标 -->
					<image src="../../../../static/playing/后退.png"></image>
					<text>15s</text>
				</view>
				<view class="center"><!-- 进度条 -->
					<view class="pro" :style="{'width':time1/time2*100+'%'}"></view>
					<view class="text"><view>{{time1 | secondTime}}/{{time2 | secondTime}}</view></view>
				</view>
				<view class="right progress1"><!-- 右图标 -->
					<image src="../../../../static/playing/后退.png"></image>
					<text>15s</text>
				</view>
			</view>
			<!--播放 -->
			<view class="playIcon">
				<image class="left " src="../../../../static/playing/上一个.png"></image>
				<navigator url="../playing1/palying1">
					<image class="center" src="../../../../static/playing/play.png">
				</navigator>
				</image>
				<image class="right " src="../../../../static/playing/下一个.png"></image>
			</view>
		</view>
		<!-- 分隔条 -->
		<view class="fenge"></view>
		<!-- 文字段落 -->
		<view class="content-text">
			<text>{{duanluo}}</text>
		</view>
		<!-- 底部收藏、点赞 -->
		<view class="bottom">
			<view class="sc">
				<image src="../../../../static/playing/star.png"></image>
				<text>66</text>
			</view>
			<view class="dz">
				<image src="../../../../static/playing/zan.png"></image>
				<text>348</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				time1:212, //已播放时间
				time2:572, //总时间
				percent:0, //进度条
				duanluo:"好的设计师不仅要知道各个元素之间的相似或不同，同 时还要知道各个元素所传达信息的对比，哪些元素传达了 亲密、愤怒或平和的情绪，哪些元素又给你金融的、医疗 的或工业的体验。”本书共分为三个部分：基本设计技 巧， 平面设计元素和设计策略。“设计元素”一节又分 为四个小组：常用图形、色彩理念、文字排版风格和排 版策略。一旦掌握了基本设计技巧及设计元素之后，作者 在“设计策略”一节中展示了如何将这些技巧和元素用在 实际设计项目中。《美国视觉设计学院用书——图形、色 彩、字体、网格参考》是所有平面设计师必备的手头参考 书，它可以为设计师带来设计灵感。素和设计策略。“设 计元素”一小组：常用图形、色彩理念、文字排版风格和排版策略。"  //段落
			}
		},
		filters:{
			secondTime(time){
				var minute = parseInt(time/60);
				minute = minute<10?'0'+minute:minute;
				var second = parseInt(time%60);
				second = second<10?'0'+second:second;
				return minute+':'+second;
			}
		},
	}
</script>

<style>
	.page{
		width: 750rpx;
		min-height:100% ;
		display: flex;
		flex-direction: column;
	}
	.nav{
		width: 750rpx;
		height: 90rpx;
		display: flex;
		position: relative;
		background:rgba(255,255,255,1);
		border-bottom: 1px solid #F0F0F0;
	}
	.fh{
		margin:25rpx 0 25rpx 28rpx;
		width: 23rpx;
		height: 40rpx;
	}
	.title{
		position: absolute;
		left: 255rpx;
		top: 27rpx;
		width:240rpx;
		height:35rpx;
		font-size:35rpx;
		font-family:Source Han Sans CN;
		font-weight:400;
		color:rgba(43,43,43,1);
		/* line-height:13rpx; */
	}
	.sq{
		position: absolute;
		top:25rpx;
		right: 24rpx;
		width:40rpx;
		height:40rpx;
	}
	.content{
		height: 762rpx;
		width: 750rpx;
		display: flex;
		flex-direction: column;
	}
	.tupian{
		display: flex;
		flex-direction:column;
		width: 231rpx;
		margin: 39rpx 260px 0 259rpx;
		height: 429rpx;
	}
	.tupian .ren{
		width: 230rpx;
		height: 301rpx;
		margin-bottom: 40rpx;
	}
	.playD{
		display: flex;
		flex-direction: row;
		position: relative;
		width: 230rpx;
		height:88rpx;
	}
	.playD>view{
		width: 79rpx;
		height: 88rpx;
	}
	.view1{
		position: absolute;
		top:0;
		left: 0;
	}
	.view2{
		position: absolute;
		top:0;
		right: 0;
	}
	.view1>image{
		margin: 0rpx 16rpx 15rpx 15rpx;
		width: 48rpx;
		height: 50rpx;
	}
	.view2>image{
		margin: 0rpx 23rpx 15rpx 24rpx;
		width: 33rpx;
		height: 50rpx;
	}
	.playD>view>text{
		position: absolute;
		left: 0;bottom: 0;
		width:79rpx;
		height:19rpx;
		font-size:19rpx;
		font-family:Source Han Sans CN;
		font-weight:300;
		color:rgba(124,124,124,1);
		line-height:19rpx;
	}
	.progress{
		display: flex;
		position: relative;
		width:694rpx;
		height:43rpx;
		margin: 35px 28rpx;
	}
	.progress .left{
		position: absolute;
		left: 0;top: 0;
	}
	.progress1>image{
		width: 44rpx;
		height:43rpx;
	}
	.progress1>text{
		position: absolute;
		left:10rpx ;top:15rpx ;
		width:27rpx;
		height:14rpx;
		font-size:18rpx;
		font-family:Source Han Sans CN;
		font-weight:400;
		color:rgba(99,99,99,1);
		line-height:13rpx;
	}
	.progress .center{
		position: absolute;
		left: 72rpx;top: 5rpx;
		width: 550rpx;
		height: 33rpx;
	}
	.progress .right{
		position: absolute;
		right: 0;top: 0;
	}
	.progress .center .pro{
		position: absolute;
		left: 0;top: 20rpx;
		height: 2rpx;
		border-radius:2rpx;
		width: 60%;
		border-bottom: solid 1px #FF0069;
		background:rgba(255,0,105,1);
	}
	.progress .center .text{
		position: absolute;
		left: 129rpx;
		width:168rpx;
		height:33rpx;
		background:rgba(99,99,99,1);
		border-radius:17rpx;
	}
	.progress .center .text>view{
		margin: 7rpx 21rpx 4rpx 21rpx;
		width:126rpx;
		height:22rpx;
		font-size:22rpx;
		font-family:Source Han Sans CN;
		font-weight:400;
		color:rgba(255,255,255,1);
		line-height:22rpx;
	}
	.playIcon{
		display: flex;
		position: relative;
		margin:20rpx 169rpx 60rpx 169rpx;
		width:412rpx ;
		height: 100rpx;
	}
	.playIcon .left{
		position: absolute;
		top: 30rpx;left: 0;
		width: 36rpx;
		height: 40rpx;
	}
	.playIcon .right{
		position: absolute;
		top: 30rpx;right: 0;
		width: 36rpx;
		height: 40rpx;
	}
	.playIcon .center{
		position: absolute;
		top: 0;left: 156rpx;
		width: 100rpx;
		height: 100rpx;
	}
	.fenge{
		width:750rpx;
		height:19rpx;
		background:rgba(244,244,244,1);
	}
	.content-text{
		width: 723rpx;
		height:432rpx;
		/* overflow: hidden; */
		margin: 31rpx 0 0 25rpx;
	}
	.content-text>text{
		font-size:28rpx;
		font-family:Source Han Sans CN;
		font-weight:300;
		color:rgba(43,43,43,1);
		line-height:48rpx;
	}
	.bottom{
		width: 750rpx;
		height: 90rpx;
		display: flex;
		position: fixed;
		left: 0;
		bottom: 0;
		background: #fff;
	}
	.bottom .sc{
		position: absolute;
		left: 204rpx;
		top: 28rpx;
		height: 35rpx;
	}
	.bottom .dz{
		position: absolute;
		left: 465rpx;
		top: 28rpx;
		height: 35rpx;
	}
	.bottom image{
		width: 35rpx;
		height: 35rpx;
	}
	.bottom text{
		position: absolute;top: 9rpx;left: 46rpx;
		width:100%;
		height:17rpx;
		font-size:22rpx;
		font-family:Source Han Sans CN;
		font-weight:400;
		color:rgba(64,64,65,1);
		/* line-height:48rpx; */
	}

</style>
