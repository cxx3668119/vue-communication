# vue_communication

## 创建一个 Vue 实例（2.6）来梳理自己对 Vue 组件之间的通信（传值）概念

### 首先梳理组件的通信方式

- 父子通信
  - props 父亲传子
  - \$emit 子传父 第一个参数是自定义事件的名字 第二个参数是传值过来的值 （如果传值比较多，都在第二个参数里以对象的方式）
  - vuex 全局
  - \$refs 命名组件
  - $parent $children 父子组件队列
  - 后代组件传值 privide inject
- 兄弟通信
  - vue 原型上定义一个新的实例 采用$bus $emit+\$on 获取
  - vuex
- 隔代通信

  - privide inject
  - vuex

- 还有一些 storage 路由传参的方式 不做参考

**props**
父组件
`<children :count="count" />`
子组件
`props: ["count"],`

**\$emit**
子组件自定义方法，传值在第二个参数里

```
 sayLove() {
      this.$emit("sayLove", "I love you cxx");
    },
```

父组件接收

```
    <children  @sayLove="getLove" />
    getLove(e) {
      console.log(e);
    },
```

**vuex**
作为 vue 的全局管理 看官方文档即可，可用于各类通信。

**\$refs**
在父组件中引入子组件
`<children ref="son" />`
直接拿
`console.log(this.$refs.son.cxx + " =====> refs");`

**$parent $children**

```
console.log(this.$children[0].cxx + " =====> $children");
console.log(this.$parent.count + " =====> parent");
```

**privide inject**
父组件

```
  provide() {
    return {
      father: this, //给后代接收
    };
  },
```

后代

```
 inject: ["father"],
  data() {
    return {
      count: this.father.count,
    };
  },
```

**\$bus**
首先在 main.js 中
`Vue.prototype.$bus = new Vue()`
然后自定义事件传值
`this.$bus.$emit("sayLoveToBro", "I love you cxxBro");`
然后\$on 接收
`this.$bus.$on("sayLoveToBro", this.getlove)`
