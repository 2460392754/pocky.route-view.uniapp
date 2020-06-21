<template>
    <my-keep-alive>
        <my-router-view>
            <view class="page-a">
                <u-navbar :is-back="false" title="A" />

                <u-cell-group>
                    <u-field v-model="val" label="input" placeholder="请输入值" />
                </u-cell-group>

                <u-button @click="onClickRedirect">uni.reLaunch 跳转到页面B</u-button>
            </view>
        </my-router-view>
    </my-keep-alive>
</template>

<script>
import MyKeepAlive from '../components/keepAlive.vue';
import MyRouterView from '../components/routerView.vue';

export default {
    name: 'page-a',

    data() {
        return {
            val: 'aaa'
        };
    },

    components: {
        MyKeepAlive,
        MyRouterView
    },

    methods: {
        onClickRedirect() {
            uni.reLaunch({
                url: '/src/pages/b'
            });
        }
    }
};
</script>

<style lang="scss">
.page-a {
}
</style>
