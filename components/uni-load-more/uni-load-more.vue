<template>
  <view class="uni-load-more" :style="{ background: bgColor }">
    <view
      v-if="iconType==='circle' || iconType==='auto' && platform === 'android'"
      v-show="status === 'loading' && showIcon"
      class="uni-load-more__img"
    >
      <view
        :style="{borderColor : color}"
        class="loader-android" />
    </view>
    <view
      v-else
      v-show="status === 'loading' && showIcon"
      class="uni-load-more__img">
      <view class="load1 load">
        <view
          :style="{ background: color }"
          class="uni-load-view_wrapper" />
        <view
          :style="{ background: color }"
          class="uni-load-view_wrapper" />
        <view
          :style="{ background: color }"
          class="uni-load-view_wrapper" />
        <view
          :style="{ background: color }"
          class="uni-load-view_wrapper" />
      </view>
      <view class="load2 load">
        <view
          :style="{ background: color }"
          class="uni-load-view_wrapper" />
        <view
          :style="{ background: color }"
          class="uni-load-view_wrapper" />
        <view
          :style="{ background: color }"
          class="uni-load-view_wrapper" />
        <view
          :style="{ background: color }"
          class="uni-load-view_wrapper" />
      </view>
      <view class="load3 load">
        <view
          :style="{ background: color }"
          class="uni-load-view_wrapper" />
        <view
          :style="{ background: color }"
          class="uni-load-view_wrapper" />
        <view
          :style="{ background: color }"
          class="uni-load-view_wrapper" />
        <view
          :style="{ background: color }"
          class="uni-load-view_wrapper" />
      </view>
    </view>
    <text
      :style="{ color: color }"
      class="uni-load-more__text">
      {{ status === 'more' ? contentText.contentdown : status === 'loading' ? contentText.contentrefresh : contentText.contentnomore }}
    </text>
  </view>
</template>

<script>
const platform = uni.getSystemInfoSync().platform
export default {
  name: 'UniLoadMore',
  props: {
	bgColor: {
		type: String,
		default: '#fff',
	},
    status: {
      // 上拉的状态：more-loading前；loading-loading中；noMore-没有更多了
      type: String,
      default: 'more'
    },
    showIcon: {
      type: Boolean,
      default: true
    },
		iconType: {
			type: String,
			default: 'auto'
		},
    color: {
      type: String,
      default: '#777777'
    },
    contentText: {
      type: Object,
      default () {
        return {
          contentdown: '上拉显示更多',
          contentrefresh: '正在加载...',
          contentnomore: '没有更多数据了'
        }
      }
    }
  },
  data () {
    return {
      platform: platform
    }
  }
}
</script>

<style lang="scss">
.uni-load-more {
	display: flex;
	flex-direction: row;
	height: 80upx;
	background: red;
	align-items: center;
	justify-content: center;

	&__text {
		font-size: 28upx;
		color: $uni-text-color-grey;
	}

	&__img {
    position: relative;
		height: 24px;
		width: 24px;
		margin-right: 10px;
		& > .load {
			position: absolute;
			.uni-load-view_wrapper {
				width: 6px;
				height: 2px;
				border-top-left-radius: 1px;
				border-bottom-left-radius: 1px;
				background: $uni-text-color-grey;
				position: absolute;
				opacity: 0.2;
				transform-origin: 50%;
				animation: load 0.96s ease infinite;

				&:nth-child(1) {
					transform: rotate(90deg);
					top: 2px;
					left: 9px;
				}

				&:nth-child(2) {
					transform: rotate(180deg);
					top: 11px;
					right: 0px;
				}

				&:nth-child(3) {
					transform: rotate(270deg);
					bottom: 2px;
					left: 9px;
				}

				&:nth-child(4) {
					top: 11px;
					left: 0px;
				}
			}
		}

    & > .loader-android {
      position: absolute;
      left: 0;
      top: 0;
      right: 0;
      bottom: 0;
      box-sizing: border-box;
      border: solid 2px #777777;
      border-radius: 50%;
      border-bottom-color: transparent !important;
      animation: loader-android 1s 0s linear infinite;
    }
	}
}

.load1,
.load2,
.load3 {
	height: 24px;
	width: 24px;
}

.load2 {
	transform: rotate(30deg);
}

.load3 {
	transform: rotate(60deg);
}
.load1 .uni-load-view_wrapper:nth-child(1) {
	animation-delay: 0s;
}

.load2 .uni-load-view_wrapper:nth-child(1) {
	animation-delay: 0.08s;
}

.load3 .uni-load-view_wrapper:nth-child(1) {
	animation-delay: 0.16s;
}

.load1 .uni-load-view_wrapper:nth-child(2) {
	animation-delay: 0.24s;
}

.load2 .uni-load-view_wrapper:nth-child(2) {
	animation-delay: 0.32s;
}

.load3 .uni-load-view_wrapper:nth-child(2) {
	animation-delay: 0.40s;
}

.load1 .uni-load-view_wrapper:nth-child(3) {
	animation-delay: 0.48s;
}

.load2 .uni-load-view_wrapper:nth-child(3) {
	animation-delay: 0.56s;
}

.load3 .uni-load-view_wrapper:nth-child(3) {
	animation-delay: 0.64s;
}

.load1 .uni-load-view_wrapper:nth-child(4) {
	animation-delay: 0.72s;
}

.load2 .uni-load-view_wrapper:nth-child(4) {
	animation-delay: 0.80s;
}

.load3 .uni-load-view_wrapper:nth-child(4) {
	animation-delay: 0.88s;
}

@-webkit-keyframes load {
	0% {
		opacity: 1;
	}

	100% {
		opacity: 0.2;
	}
}

@-webkit-keyframes loader-android {
	0% {
		transform: rotate(0deg);
	}

	100% {
		transform: rotate(360deg);
	}
}
</style>
