<template>
	<my-keep-alive>
		<my-router-view>
			<view class="page-b">
				<u-navbar :is-back="false" title="B" />

				<u-cell-group>
					<u-field v-model="val" label="input" placeholder="请输入值" />
				</u-cell-group>

				<u-button @click="onClickRedirect">uni.reLaunch 跳转到页面A</u-button>
			</view>
		</my-router-view>
	</my-keep-alive>
</template>

<script>
import MyKeepAlive from "../components/keepAlive.vue";
import MyRouterView from "../components/routerView.vue";

export default {
	name: "page-b",

	data() {
		return {
			val: "bbb",
		};
	},

	components: {
		MyKeepAlive,
		MyRouterView,
	},

	methods: {
		onClickRedirect() {
			uni.reLaunch({
				url: "/src/pages/a",
			});
		},
	},
};
</script>

<style lang="scss">
.page-b {
}
</style>
