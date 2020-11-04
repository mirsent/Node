# Class 与 Style 绑定

## 绑定 HTML Class

### 对象语法

传给 `v-bind:class` 一个对象，以动态地切换 calss：

```html
<div v-bind:class="{ active: isActive }"></div>
<div
  class="static"
  v-bind:class="{ active: isActive, 'text-danger': hasError }"
></div>
```

当 `isActive` 或者 `hasError` 变化时，class 列表将相应地更新。

绑定的数据对象不必内联定义在模板里：

```html
<div v-bind:class="classObject"></div>
```

```js
data: {
  classObject: {
    active: true,
    'text-danger': false
  }
}
```

也可以绑定一个返回对象的 **计算属性** 。

```html
<div v-bind:class="classObject"></div>
```

```js
data: {
  isActive: true,
  error: null
},
computed: {
  classObject: function () {
    return {
      active: this.isActive && !this.error,
      'text-danger': this.error && this.error.type === 'fatal'
    }
  }
}
```

### 数组语法

```html
<div v-bind:class="[activeClass, errorClass]"></div>
```

```js
data: {
  activeClass: 'active',
  errorClass: 'text-danger'
}
```

三元表达式：

```html
<div v-bind:class="[isActive ? activeClass : '', errorClass]"></div>
```

使用对象语法：

```html
<div v-bind:class="[{ active: isActive }, errorClass]"></div>
```

## 绑定内联样式

### 对象语法

`v-bind:style` 的对象语法， CSS property 名用驼峰式（camelCase）或短横线分割（kebab-case，引号）来命名：

```html
<div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>
```

```js
data: {
  activeColor: 'red',
  fontSize: 30
}
```

直接绑定到样式对象：

```html
<div v-bind:style="styleObject"></div>
```

```js
data: {
  styleObject: {
    color: 'red',
    fontSize: '13px'
  }
}
```

### 数组语法

```html
<div v-bind:style="[baseStyles, overridingStyles]"></div>
```

### 自动添加前缀

当 `v-bind:style` 使用需要添加 **浏览器引擎前缀** 的 CSS property 时，Vue.js 会自动侦测并添加相应的前缀。 