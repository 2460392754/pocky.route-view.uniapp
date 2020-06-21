<script>
// keep-alive组件全局数据
const cacheMap = new Map();

export default {
	name: "myKeepAlive",

	// 抽象组件
	abstract: true,

	data() {
		return {
			cacheMap,
		};
	},

	/**
	 * render渲染
	 */
	render() {
		// 获取默认插槽下的所有节点
		const children = this.$slots.default;

		// 跳过空节点渲染
		if (typeof children === "undefined") {
			return children;
		}

		// 获取 默认插槽下的第一个节点
		const vnode = children[0];
		const { componentOptions, context } = vnode;

		// 节点标识
		const key = context.route;

		// 获取缓存的节点数据
		if (this.cacheMap.has(key)) {
			const data = this.cacheMap.get(key);

			vnode.componentInstance = data.componentInstance;

			// 保存 节点数据
		} else {
			vnode.data || (vnode.data = {});

			this.cacheMap.set(key, vnode);
		}

		// route-view 组件的节点数据替换标识
		vnode.data.keepAlive = true;

		return vnode;
	},
};
</script>
