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















