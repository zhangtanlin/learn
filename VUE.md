# VUE
VUE

## 文档
- [更新文档](https://vxhly.github.io/views/vuejs/learning-vue3.html#%E7%9C%8B%E6%96%87%E6%A1%A3%E5%BE%88%E9%87%8D%E8%A6%81)
- [vue3创建公用组件](https://juejin.im/post/6844904169644490766)
- [vue3封装axios](https://my.oschina.net/u/4355040/blog/4288885)
- [Vue3CompositionAPI如何替换VueMixins](https://xie.infoq.cn/article/1348c257d7bb72bc6597f9e25)
- [vue中8种组件通信方式](https://juejin.im/post/6844903887162310669)
- [vue3创建公用组件](https://juejin.im/post/6844904169644490766)
- [vue3创建公用组件](https://juejin.im/post/6844904169644490766)

## vue2和vue3的区别：
```
Vue2	        vue3	
beforeCreate	setup()	        setup() :开始创建组件之前，在beforeCreate和created之前执行。创建的是data和method
created	        setup()	
beforeMount	    onBeforeMount	组件挂载到节点上之前执行的函数。
mounted	        onMounted	    组件挂载完成后执行的函数。
beforeUpdate	onBeforeUpdate	组件更新之前执行的函数。
updated	        onUpdated	    组件更新完成之后执行的函数。
beforeDestroy	onBeforeUnmount	组件卸载之前执行的函数。
destroyed    	onUnmounted	    组件卸载完成后执行的函数
activated    	onActivated  	被包含在<keep-alive>中的组件，会多出两个生命周期钩子函数。被激活时执行。
deactivated	    onDeactivated	比如从 A 组件，切换到 B 组件，A 组件消失时执行。
errorCaptured	onErrorCaptured	当捕获一个来自子孙组件的异常时激活钩子函数。
```
## 国家代码插件
https://github.com/941477276/vue-country-intl

## 文字超出容器最大宽度实现从右向左匀速滚动
https://www.codeleading.com/article/26634615752/

## vue的computed内的值怎么改变
```
computed: {
    ...mapGetters({
        nameFromStore: 'name'
    }),
    name: {
        get(){
            return this.nameFromStore
        },
        set(newName){
            return newName
        } 
    }
}
在您的store中
export const store = new Vuex.Store({
    state:{
        name : "Stackoverflow"
    },
    getters: {
        name: (state) => {
            return state.name;
        }
    }
}

```