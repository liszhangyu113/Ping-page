<template>
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
					<view class="view1" @click="isplayD =true">
						<image src="../../../../static/playing/定时播放.png"></image>
						<text>定时播放</text>
					</view>
					<view class="view2" @click="isplayF = true">
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
				<image class="center" :class="{'play':isplay,'stop':!isplay}" @click="playorpause()">
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
		<!-- 定时播放 -->
		<view :class="{'pageP':isplayD,'ddss':!isplayD}">
			<view class="dingshi " >
				<view class="changeD" v-for="datads in dingshi">
					<text>{{datads.tname}}</text>
				</view>
				<view class="fg"></view>
				<view class="qx" @click="isplayD =false">取消</view>
			</view>
		</view>
		<!-- 倍数播放切换 -->
		<view :class="{'pageP':isplayF,'ddss':!isplayF}">
			<view class="beishu" >
				<view class="changeF" v-for="dataks in ks">
					<text>{{dataks.kfast}}</text>
				</view>
				<view class="fg"></view>
				<view class="qx" @click="isplayF =false">取消</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default{
		data(){
			return{
				isplay:false, //播放图标的切换
				isplayD:false, //定时播放的切换
				isplayF:false, //快速倍数的切换
				time1:212, //已播放时间
				time2:572, //总时间
				percent:0, //进度条
				duanluo:"好的设计师不仅要知道各个元素之间的相似或不同，同 时还要知道各个元素所传达信息的对比，哪些元素传达了 亲密、愤怒或平和的情绪，哪些元素又给你金融的、医疗 的或工业的体验。”本书共分为三个部分：基本设计技 巧， 平面设计元素和设计策略。“设计元素”一节又分 为四个小组：常用图形、色彩理念、文字排版风格和排 版策略。一旦掌握了基本设计技巧及设计元素之后，作者 在“设计策略”一节中展示了如何将这些技巧和元素用在 实际设计项目中。《美国视觉设计学院用书——图形、色 彩、字体、网格参考》是所有平面设计师必备的手头参考 书，它可以为设计师带来设计灵感。素和设计策略。“设 计元素”一小组：常用图形、色彩理念、文字排版风格和排版策略。",  //段落
				dingshi:[
					{tname:'5分钟后'},
					{tname:'10分钟后'},
					{tname:'15分钟后'},
					{tname:'30分钟后'},
					{tname:'播完当前课程后关闭'},
					{tname:'播完当前课程列表后关闭'},
					{tname:'不开启定时'}
				],
				ks:[
					{kfast:'0.5倍速'},
					{kfast:'0.8倍速'},
					{kfast:'正常倍速'},
					{kfast:'1.2倍速'},
					{kfast:'1.5倍速'},
					{kfast:'2倍速'}
				],
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
		methods:{
			playorpause(){
				if(this.isplay === false){
					this.isplay = true;
					return true;
				}else{
					this.isplay = false;
					return false;
				}
			},
		},
	}
</script>

<style>
	*{
		margin: 0;
		padding: 0;
	}
/* 页面 */
	.page{
		width: 750rpx;
		min-height:100% ;
		display: flex;
		position: relative;
		flex-direction: column;
	}
/* 导航栏 */
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
/* 图片、定时播放、快速播放 */
	.content{
		height: 762rpx;
		width: 750rpx;
		display: flex;
		flex-direction: column;
	}
/* 图片 */
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
/* 定时播放、快速播放 */
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
/* 进度条 */
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
/* 上一首、下一首 播放暂停 */
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
	.play{
		background: url(../../../../static/playing/play.png);
		background-size:100% ;
	}
	.stop{
		background: url(../../../../static/playing/stop.png);
		background-size:100% ;
	}
/* 分割线 */
	.fenge{
		width:750rpx;
		height:19rpx;
		background:rgba(244,244,244,1);
	}
/* 文字内容 */
	.content-text{
		width: 725rpx;
		/* height:432rpx; */
		/* overflow: hidden; */
		margin: 31rpx 0 100rpx 25rpx;
	}
	.content-text>text{
		font-size:28rpx;
		font-family:Source Han Sans CN;
		font-weight:300;
		color:rgba(43,43,43,1);
		line-height:48rpx;
	}
/* 底部收藏 点赞 */
	.bottom{
		width: 750rpx;
		height: 90rpx;
		z-index: 2;
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
/* 定时播放 */
/* 全部背景 */
	.ddss{
		display: none;
	}
	.pageP{
		position: absolute;
		left: 0;
		top: 0;
		width: 750rpx;
		height: 100%;
		z-index: 50;
		background:rgba(65,63,63,.8);
	}
	.dingshi{
		position: fixed;
		bottom: 0;
		left: 0;
		display: flex;
		flex-direction: column;
		text-align: center;
		z-index: 99;
		width:750rpx;
		height:713rpx;
		background:rgba(255,255,255,1);
		border-radius:40rpx 40rpx 0rpx 0rpx;
	}
	.dingshi .changeD{
		/* margin: 0; */
		width: 750rpx;
		height: 87rpx;
		/* padding: 30px 0; */
		border-bottom: 1px solid #F3F3F3;
	}
	.dingshi .changeD>text{
		display: block;
		width:100%;
		height:27rpx;
		margin: 30rpx 0rpx;
		/* font-size:30rpx; */
		font-size:23rpx;
		font-family:Source Han Sans CN;
		font-weight:300;
		color:rgba(43,43,43,1);
		line-height:27rpx;
	}
	.fg{
		position: absolute;
		left: 0;
		bottom: 87rpx;
		width:750rpx;
		height:10rpx;
		background: #F8F8F8;
	}
	.qx{
		width:750rpx;
		height:27rpx;
		padding: 30rpx 0;
		font-size:30rpx;
		font-family:Source Han Sans CN;
		font-weight:300;
		color:rgba(49,128,250,1);
		line-height:36rpx;
	}
/* 快速播放 */	
/* 全部背景 */
	/* .kkss{
		display: none;
	}
	.pageK{
		position: absolute;
		left: 0;
		top: 0;
		width: 750rpx;
		height: 100%;
		z-index: 50;
		background:rgba(65,63,63,.8);
	} */
	.beishu{
		position: fixed;
		bottom: 0;
		left: 0;
		display: flex;
		flex-direction: column;
		text-align: center;
		z-index: 99;
		width:750rpx;
		height:624rpx;
		background:rgba(255,255,255,1);
		border-radius:40rpx 40rpx 0rpx 0rpx;
	}
	.beishu .changeF{
		width: 750rpx;
		height: 87rpx;
		border-bottom: 1px solid #F3F3F3;
	}
	.beishu .changeF>text{
		display: block;
		width:100%;
		height:27rpx;
		margin: 30rpx 0rpx;
		/* font-size:30rpx; */
		font-size:23rpx;
		font-family:Source Han Sans CN;
		font-weight:300;
		color:rgba(43,43,43,1);
		line-height:27rpx;
	}



</style>
