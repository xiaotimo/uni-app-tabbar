<template>
	<view class="content">
		<view class="">
			这里是第1个tabbar
		</view>
	</view>
</template>

<script>
    export default {
		onShow() {
			var icon = plus.nativeObj.View.getViewById("icon");
			if (icon) {
				setTimeout(function(){
					icon.show();
				},100)
			}
		}
    }
</script>

<style>

</style>
