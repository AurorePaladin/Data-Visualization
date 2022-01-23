### 1. antV-g2 title 和折线图描述未展示

### 2. antV-g6 绘制拓扑图（托、拉、拽）以后补充这个知识点！！

### 3. antV-L7 size color 等方法的第二个参数对应关系

### 4. 有没有方法选择文件前就限制文件的类型

### 5. echarts 饼图如何选择百分比

### 6. echarts renderItem API.coord 参数含义

### 7. mixins 是什么？
##### 答：混入 (mixin) 提供了一种非常灵活的方式，来分发 Vue 组件中的可复用功能。一个混入对象可以包含任意组件选项。当组件使用混入对象时，所有混入对象的选项将被“混合”进入该组件本身的选项。
```js
    // 定义一个混入对象
var myMixin = {
  created: function () {
    this.hello()
  },
  methods: {
    hello: function () {
      console.log('hello from mixin!')
    }
  }
}

// 定义一个使用混入对象的组件
var Component = Vue.extend({
  mixins: [myMixin]
})

var component = new Component() // => "hello from mixin!"
```
##### 参考来源：https://cn.vuejs.org/v2/guide/mixins.html
### 8. 慕课网 前端主流布局系统进阶与实战

### 9. 学习ESLint忽略规则     .editorconfig
