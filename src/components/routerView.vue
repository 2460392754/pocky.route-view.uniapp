<script>
export default {
    name: 'myRouterView',

    // 抽象组件
    abstract: true,

    /**
     * 渲染函数
     */
    render() {
        // 获取默认插槽下的所有节点
        const children = this.$slots.default;

        // 获取 默认插槽下的第一个节点
        const vnode = children[0];

        // 命名视图的键名
        const name = 'default';

        // 路由信息对象
        const route = this.$route;

        // 获取 视图深度，组件层级
        const depth = 0;

        // 从组件实例中获取缓存对象
        const cache = vnode.context._routerViewCache || (vnode.context._routerViewCache = {});
        const cacheVNode = cache[name];

        if (typeof cacheVNode !== 'undefined') {
            return cacheVNode;
        }

        // 缓存组件
        cache[name] = vnode;

        return vnode;
    }
};
</script>
