# REACT
REACT

## 文档
- [React跨平台应用脚手架](https://github.com/electron-react-boilerplate/electron-react-boilerplate)
- [Hooks和react 生命周期](https://blog.csdn.net/lunahaijiao/article/details/99434993)
- [ReactHooks模拟生命周期](https://juejin.im/post/5d5dec7ee51d45620346b8c0)
- [一篇看懂ReactHooks](https://zhuanlan.zhihu.com/p/50597236)
- [基于ReactHook的ReactRouter4路由统一配置管理（v4.0+ ）](https://juejin.im/post/5e001e03518825125f39a3dc)
- [React路由学习](https://reacttraining.com/react-router/web/guides/quick-start)
- [ReactHooks入门教程（阮一峰）](https://www.ruanyifeng.com/blog/2019/09/react-hooks.html)
- [hooks不错的示例](https://www.robinwieruch.de/react-hooks-fetch-data)
- [Hooks视频教程，useEffect 和react中哪些生命周期对应](https://www.youtube.com/watch?v=KmTc7xnNG5E)
- [reactloading 样式集合](https://www.ruanyifeng.com/blog/2019/09/react-hooks.html)
- [react插件网站](https://reactjsexample.com/)
- [React中阻止事件冒泡的问题](https://www.cnblogs.com/Wayou/p/react_event_issue.html)

## useEffect 和react中哪些生命周期对应
```
* 注意1、组件初始化时使用 useEffect (设置空数组，只会初始化一次)【类似componentDidMount()】，示例：
	useEffect(() => {
		getUserInfo(); // 请求接口数据
	}, []);
* 注意2、组件更新时使用 useEffect （在第二个参数里面设置监听，当前值改变时，触发更新）【类似componentDidUpdate()】，示例：
	useEffect(() => {
		getUserInfo(); // 请求接口数据
	}, [‘被监听值’]);
* 注意3、组件重新渲染之前，需要清理一些内容（uesEffect的内部底部使用return(),return里面可以添加清理一些东西）【类似componentwillunmount()】，示例：
	useEffect(() => {
	  	getUserInfo(); // 请求接口数据
		return(‘清理’);
	}, [‘被监听值’]);
```
## Redux
- [Redux中文文档](https://cn.redux.js.org/)
- [Redux学习文档](https://juejin.im/post/5af00705f265da0ba60fb844)
- [react-radux+hook参考文档](https://levelup.gitconnected.com/react-redux-hooks-useselector-and-usedispatch-f7d8c7f75cdd)

## use-global-hook
- [参考文档](https://codesandbox.io/s/several-counters-pdbsy?file=/src/store/index.js:221-228)
