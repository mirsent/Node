# Vue 实例 

## 创建一个 Vue 实例

每个 Vue 应用都是通过用 `Vue` 函数创建一个新的 **Vue 实例** 开始的：

```javascript
var vm = new Vue({
  // 选项
})
```

## 数据与方法

当一个 Vue 实例被创建时，它将 `data` 对象中的所有的 property 加入到 Vue 的 **响应式系统** 中。当这些 property 的值发生改变时，视图将会“相应”，即匹配为新的值。

```js
// 我们的数据对象
var data = { a: 1 }

// 该对象被加入到一个 Vue 实例中
var vm = new Vue({
  data: data
})

// 获得这个实例上的 property
// 返回源数据中对应的字段
vm.a == data.a // => true

// 设置 property 也会影响到原始数据
vm.a = 2
data.a // => 2

// ……反之亦然
data.a = 3
vm.a // => 3
```

当这些数据改变时，试图会进行重渲染。

> 只有当实例被创建时就已存在于 `data` 中的 property 才是 **响应式** 的。

使用 `Object.freeze()` 阻止修改现有的 property

```js
var obj = {
  foo: 'bar'
}

Object.freeze(obj)

new Vue({
  el: '#app',
  data: obj
})
```

```html
<div id="app">
  <p>{{ foo }}</p>
  <!-- 这里的 `foo` 不会更新！ -->
  <button v-on:click="foo = 'baz'">Change it</button>
</div>
```

## 实例生命周期钩子

每个 Vue 实例在被创建时都要经过一系列的初始化过程。同时在这个过程中会运行一些叫做 **生命周期钩子** 的函数。

生命周期钩子的 `this` 上下文指向调用它的 Vue 实例。

> 不要在选项 property 或回调上使用 <u>箭头函数</u> ，因为箭头函数并没有 `this` ， `this` 会作为变量一直向上级词法作用域查找，直至找到为止。