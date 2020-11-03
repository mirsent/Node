# JavaScript 复制文本到剪贴板

## 常用方法

- 第三方库：clipboard.js

- 原生方法：document.execCommand()

  

### clipboard.js

[官网](https://clipboardjs.com/)



### document.execCommand() 方法

[MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/execCommand#%E5%91%BD%E4%BB%A4)

> ```javascript
> bool = document.execCommand(aCommandName, aShowDefaultUI, aValueArgument)
> ```

##### 返回值

一个 [`Boolean`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Boolean) ，如果是 `false` 则表示操作不被支持或未被启用。

##### 参数

```
aCommandName
```

一个 [`DOMString`](https://developer.mozilla.org/zh-CN/docs/Web/API/DOMString) ，命令的名称。可用命令列表请参阅 [命令](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/execCommand#命令) 。

```
aShowDefaultUI
```

一个 [`Boolean`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Boolean)， 是否展示用户界面，一般为 false。

```
aValueArgument
```

一些命令（例如insertImage）需要额外的参数（insertImage需要提供插入image的url），默认为null。

##### 命令

```
copy
```

拷贝当前选中内容到剪贴板。启用这个功能的条件因浏览器不同而不同，而且不同时期，其启用条件也不尽相同。使用之前请检查浏览器兼容表，以确定是否可用。

#### 使用

##### 从输入框复制

```html
<input id="demoInput" value="hello world">
<button id="btn">点我复制</button>
```

```javascript
const btn = document.querySelector('#btn');
btn.addEventListener('click', () => {
	const input = document.querySelector('#demoInput');
	input.select();
	if (document.execCommand('copy')) {
		document.execCommand('copy');
		console.log('复制成功');
	}
})
```

##### 其他地方复制

有的时候页面上并没有 `input` 标签，我们可能需要从一个 `div` 中复制内容，或者直接复制变量。

还记得在 `execCommand()` 方法的定义中提到，它只能操作**可编辑区域**，也就是意味着除了 `input` `textarea` 这样的输入域以外，是无法使用这个方法的。

**解决办法** 在文本标签中，绝对定位一个透明的input（这个input不能用type=hidden或者display、visibility去隐藏，会获取不到文本的），然后点击复制按钮，去获取这个Input的文本

```html
<input id="demoInput" style="position: absolute;opacity: 0;">
<button id="btn">点我复制</button>
```

```javascript
const btn = document.querySelector('#btn');
btn.addEventListener('click', () => {
	const input = document.querySelector('#demoInput');
    input.value = '123'
	input.select();
	if (document.execCommand('copy')) {
		document.execCommand('copy');
		console.log('复制成功');
	}
})
```

