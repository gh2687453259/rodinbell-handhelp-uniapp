<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>

		<button type="primary" @click="testcreateReader">test-createReader</button>
		<button type="primary" @click="testconnect">test-connnect</button>
		<button type="primary" @click="testfirmware">test-firmware</button>
		<button type="primary" @click="testinventory">test-inventory</button>
		<button type="primary" @click="testdestroyReader">test-destroyReader</button>
	</view>
</template>

<script>
	const uhfModule = uni.requireNativePlugin("rdbe-UHFPlugin-UHFModule");
	console.log(uhfModule);
	
	var nameid = "orca50-rodinbell";

	export default {
		data() {
			return {
				title: nameid
			}
		},
		onLoad() {

		},
		methods: {
			testcreateReader() {
				var ret = uhfModule.createReader(nameid);
				console.log("testcreateReader : " + ret);
			},
			
			testconnect() {
				var ret = uhfModule.callReaderUhf(nameid,JSON.stringify({
					'method': 'connectDevice',
				}));
				console.log(ret);
			},
			
			testfirmware() {
				var ret = uhfModule.callReaderUhf(nameid,JSON.stringify({
					'method': 'getFirmwareVersion',
				}));
				console.log(ret);
			},
			
			testinventory() {
				var ret = uhfModule.callReaderUhf(nameid,JSON.stringify({
					'method': 'customInventory',
				}));
				console.log(ret);
			},

			testdestroyReader() {
				console.log('=====testdestroyReader=====');
				uhfModule.destroyReader(nameid);
			},
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>