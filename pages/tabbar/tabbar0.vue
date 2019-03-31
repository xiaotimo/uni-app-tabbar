<template>
	<view class="content">
		<view class="">
			这里是第0个tabbar
		</view>
	</view>
</template>

<script>
	var bitmap1=null;
	export default {
		onShow() {
			var icon = plus.nativeObj.View.getViewById("icon");
			if (icon) {
				setTimeout(function(){
					icon.show();
				},100)
			}
		},
		onLoad: function(options) {
			bitmap1 = new plus.nativeObj.Bitmap('bmp1');
			bitmap1.load('static/img/logo.png',function(){
				//console.log('bmp1.png load success!');
			},function(e){
				//console.log('bmp1.png load failed! '+JSON.stringify(e));
			});
			//ios需要将图片转为base64才能显示出来
			this.createtab();
		},
		methods: {
			createtab: function() {
				//console.log('App onLoad');
				// 设置水平居中位置
				var leftPos = Math.ceil((plus.screen.resolutionWidth - 60) / 2);
				var view = new plus.nativeObj.View('icon', {
					bottom: '11px',
					left:  leftPos+'px',
					width: '60px',
					height: '60px'
				});
				view.drawBitmap(bitmap1,
					{
						tag: 'font',
						id: 'icon',
						//text: '\ue510', //此为字体图标Unicode码'\e600'转换为'\ue600'
						src: '../../static/img/logo.png',
						position: {
							top: '0px',
							left: '5px',
							width: '50px',
							height: '100%'
						}
					}
				);
				view.addEventListener("click", function(e) {
// 					uni.navigateTo({
// 						url: '../login/login'  这里是点击中间按钮直接打开新的页面
// 					});
// 					var icon = plus.nativeObj.View.getViewById("icon");
// 					if (icon) {
// 						setTimeout(function(){
// 							icon.hide();
// 						},200)
// 					}
					uni.switchTab({
						url: 'tabbar2'
					})
				}, false);
				view.show();
			}
		}
	}
</script>

<style>
	
</style>
