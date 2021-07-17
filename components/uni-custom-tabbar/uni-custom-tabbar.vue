<template>
    <view>
		<u-gap height="100" bg-color="#f5f5f5"></u-gap>
		<cover-view class="tabbar" :style="{'padding-bottom': paddingBottomHeight + 'rpx'}">
		    <cover-view class="tabbar-item"
		        v-for="(item, index) in list" 
		        :key="index" 
		        @click="tabbarChange(item.pagePath)">
		        <cover-image class="item-img" :src="item.selectedIconPath" v-if="current == index"></cover-image>
		        <cover-image class="item-img" :src="item.iconPath" v-else></cover-image>
		        <cover-view class="item-name" :class="{'tabbarActive': current == index}" v-if="item.text">{{item.text}}</cover-view>
		    </cover-view>
		</cover-view>
	</view>
</template>

<script>
	export default {
		name:"uni-custom-tabbar",
		props: {
			current: String
		},
		data() {
			return {
				paddingBottomHeight: 0,  //苹果X以上手机底部适配高度
				list: [{
						pagePath: "/pages/index/index",
						iconPath: "/static/tabbar/icon_tabbar_check.png",
						selectedIconPath: "/static/tabbar/icon_tabbar_check_active.png",
						text: "首页"
					},
					{
						pagePath: "/pages/about/about",
						iconPath: "/static/tabbar/icon_tabbar_score.png",
						selectedIconPath: "/static/tabbar/icon_tabbar_score_active.png",
						text: "简介"
					}
				]
			}
		},
		created() {
			let that = this;
			
			uni.getSystemInfo({
				success: function (res) {
					let model = ['X', 'XR', 'XS', '11', '12', '13', '14', '15'];
					model.forEach(item => {
						//适配iphoneX以上的底部，给tabbar一定高度的padding-bottom
						if(res.model.indexOf(item) != -1 && res.model.indexOf('iPhone') != -1) {
							that.paddingBottomHeight = 40;
						}
					})
				}
			})
		},
		methods: {
			tabbarChange(pagePath) {
				uni.switchTab({
					url: pagePath
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.tabbarActive{
        color: #2B4260 !important;
    }
    .tabbar{
        position: fixed;
        bottom: 0;
        left: 0;
        right: 0;
        display: flex;
        justify-content: space-around;
        align-items: center;
        width: 100%;
        height: 100rpx;
		background-color: #ffffff;
        .tabbar-item{
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100rpx;
            .item-img{
                margin-bottom: 4rpx;
                width: 46rpx;
                height: 46rpx;
            }
            .item-name{
                font-size: 26rpx;
                color: #A3A3A3;
            }
        }
    }
</style>
