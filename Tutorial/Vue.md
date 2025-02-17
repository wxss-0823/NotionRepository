# Vue 教程

## 1. Vue 基础语法

​	Vue.js 是一个渐进式 JavaScript 框架，主要用于构建用户界面。其基于组件化和响应式数据的理念，提供了一种简单高效的方式来构建用户界面。

​	Vue 单文件组件（Single File Component，简称 SFC）是 Vue.js 框架的文件格式，它允许开发者将 HTML、JavaScript 和 CSS 代码放在一个文件中，通常以 `.vue` 为文件后缀。

## 2. Vue 声明式渲染

​	声明式渲染（Declarative Rendering）是指通过数据驱动视图的更新，而不是直接操作 DOM。只需要声明 UI 应该如何呈现，Vue 会根据数据的变化自动更新视图，当改变数据时，视图会自动响应。

### 2.1. 数据绑定

​	数据绑定是声明式渲染的核心。通过绑定数据，Vue 可以自动更新 DOM 元素的内容，避免了传统的手动 DOM 操作。

#### 2.1.1. 插值表达式

​	通过双花括号 `{{ }}` 将组件的数据插入到 HTML 模板中。

```vue
<template>
	<div>
    <h1>{{ message }}</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "Hello, Vue3!"
    };
  }
};
</script>
```

​	双花括号中的内容并不只限于标识符或路径，可以使用任何有效的 JavaScript 表达式。

```vue
<h1>{{ message.split('').reverse().join('') }}</h1>
```

### 2.2. 属性绑定

​	通过 `v-bind` 指令，可以绑定 HTML 属性到组件的数据，这样可以使得 DOM 元素的属性可以根据组件的状态动态更新。

```vue
<template>
	<div>
    <a v-bind:href="url">Click me!</a>
  </div>
</template>

<script>
export default {
  data() {
    return {
      url: 'https://github.com/wxss-0823'
    };
  }
};
</script>
```

### 2.3. 条件渲染

​	Vue 通过 `v-if` 、`v-else` 和 `v-else` 指令实现条件渲染，根据某个数据条件来决定是否渲染某个 DOM 元素。

```vue
<template>
	<div>
    <p v-if="isVisible">This text is visible</p>
    <button @click="toggleVisibility">Toggle visibility</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isVisible: true
    };
  },
  methods: {
    toggleVisibility() {
      this.isVisible = !this.isVisible;
    }
  }
};
</script>
```

### 2.4. 列表渲染

​	使用 `v-for` 指令可以渲染一个列表。Vue 会根据数组的每一项渲染对应的 DOM 元素，并且在数组数据变化时，自动更新视图。

```vue
<template>
  <div>
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { id: 1, name: 'Vue 3' },
        { id: 2, name: 'JavaScript' },
        { id: 3, name: 'HTML' }
      ]
    };
  }
};
</script>
```

### 2.5. 双向数据绑定

​	Vue 提供了 `v-mode` 指令来实现表单元素和组件数据之间的双向绑定。这样，表单元素值与数据模型保持同步，用户输入时会自动更新数据，数据变化时会自动更新视图。

```vue
<tempalte>
	<div>
    <input v-model="message" placeholder="Input some text" />
    <p>You input: {{ message }}</p>
  </div>
</tempalte>

<script>
export default {
  data() {
		return {
      message: ''
    };
  }
};
</script>
```

### 2.6. 事件处理

​	Vue 提供了 `v-on` 指令来监听 DOM 事件并在事件触发时执行方法，这种方式能够声明式地处理用户输入、点击等事件。

```vue
<template>
	<div>
    <button v-on:click="increment">click me!</button>
    <p>Click times: {{ count }}</p> 
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0
    };
  },
  methods: {
		increment() {
      this.count += 1
    }
  }
};
</script>
```

### 2.7. 计算属性

​	计算属性是 Vue 提供地一种声明式计算值的方式。计算属性基于响应式数据，且只有在依赖的数据发生变化时才会重新计算。

```vue
<template>
	<div>
    <p>Origin amount: {{ amount }}</p>
    <p>After tax amount: {{ afterTaxAmount }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      amount: 11000
    };
  },
  computed {
  	afterTaxAmount() {
      return this.amount * 0.8;
    }
	}
};
</script>
```

## 3. Vue 指令

​	Vue 指令（Directives）是 Vue.js 的一项核心功能，它们可以在 HTML 模板中以 `V-` 开头的特殊属性形式使用，用于将响应式数据绑定到 DOM 元素上或在 DOM 元素上进行一些操作。

| 指令      | 描述                                                         |
| --------- | ------------------------------------------------------------ |
| `v-bind`  | 用于将 Vue 实例的数据绑定到 HTML 元素的属性上                |
| `v-if`    | 用于根据表达式的值来条件性地渲染元素或组件                   |
| `v-show`  | 用于根据表达式的值来条件性地显示或隐藏元素                   |
| `v-for`   | 用于根据数组或对象的属性值来循环渲染元素或组件               |
| `v-on`    | 用于在 HTML 元素上绑定事件监听器，使其能够触发 Vue 实例中的方法和函数 |
| `v-model` | 用于在表单控件和 Vue 实例的数据之间创建双向数据绑定          |

## 4. Vue 模板语法

​	Vue 使用了基于 HTML 的模板语法，允许开发者声明式地将 DOM 绑定至底层的 Vue 实例的数据。结合响应系统，在应用状态改变时，Vue 能够只能地计算出重新渲染组件的最小代价并应用到 DOM 操作上。

### 4.1. 插值

#### 4.1.1. 文本

​	数据绑定最常见的形式就是使用 `{{ }}` 的文本插值。

```vue
<div>
	{{ message }}
</div>
```

​	`{{ }}` 标签内的内容将会被替代为对应组件实例中 `message` 的值，如果 `message` 属性的值发生了改变，`{{ }}` 标签内容也会更新。也可以使用 `v-once` 指令，执行一次性地插值，当数据改变时，插值处的内容不会更新。

#### 4.1.2. HTML

​	使用 `v-html` 指令用于输出 HTML 代码。

```vue
<div>
  <span v-html="rawHTML"></span>
</div>

<script>
export default {
  data() {
    return {
      rawHTML: "<span style='color:red'>This is red</span>"
    };
  }
};
</script>
```

#### 4.1.3. 属性

​	HTML 属性中的值应使用 `v-bind` 指令。

```vue
<div v-bind:id="dynamicId"></div>
```

 	对于 Boolean 属性，常规值为 true 或 false，如果属性值为 null 或 undefined，则该属性不会显示出来。

```vue
<button v-bind:disabled="isButtonDisabled">Button</button>
```

#### 4.1.4. 表达式

​	Vue.js 提供了完全的 JavaScript 表达式支持。

```vue
<div>
  {{ message.split('').reverse().join('') }}
</div>
```

​	表达式会在当前活动实例的数据作用于下作为 JavaScript 被解析。

**注意**：每个绑定都只能包含单个表达式，语句和控制流都不会生效。

### 4.2. 指令

​	指令是带有 `v-` 前缀的特殊属性，用于在表达式的值改变时，将某些行为应用到 DOM 上。

#### 4.2.1. 参数

​	参数在指令后以冒号指明。

```vue
<div>
  <p><a v-bind:href='url'>Home page</a></p>
</div>

<script>
export default {
  data() {
    return {
      url: "https://github.com/wxss-0823"
    };
  }
};
</script>
```

#### 4.2.2. 修饰符

​	修饰符是以半角句号 `.` 指明的特殊后缀，用于指出一个指令应该以特殊的方式绑定。

```vue
<form v-on:submit.prevent="onSubmit"></form>
```

### 4.3. 用户输入

​	在 input 输入框中，可以使用 `v-model` 指令来实现双向数据绑定。

