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

### 4.4. 缩写

#### 4.4.1. v-bind 缩写

```vue
<!-- 完整语法 -->
<a v-bind:href="url"></a>
<!-- 缩写 -->
<a :href="url"></a>
```

#### 4.4.2. v-on 缩写

```vue
<!--  完整语法 -->
<a v-on:click="doSomething"></a>
<!-- 缩写 -->
<a @click="doSomething"></a>
```

## 5. Vue 条件语句

​	在 Vue 3 中，可以在模板中使用多种条件语句来控制组件的渲染。

### 5.1. 条件判断

#### 5.1.1. v-if

​	根据表达式的真假条件性的渲染元素。如果表达式为真，则渲染该元素；如果为假，则不渲染（不会在 DOM 中生成该元素）。

​	因为 `v-if` 是一个指令，所以必须将它添加到一个元素上。如果是多个元素，可以包裹在 `<template>` 元素上，并在上面使用 `v-if` 。最终渲染的结果将不包括 `<template>` 元素。

#### 5.1.2. v-else

​	与 `v-if` 搭配使用，表示在前一个 `v-if` 表达式为假时渲染的元素。

#### 5.1.3. v-else-if

​	在 `v-if` 和 `v-else` 之间添加额外的条件判断，可以连续使用多个 `v-else-if` 。

### 5.2. v-show

​	根据表达式的真假条件性地显式或隐藏元素，与 `v-if` 不同的是，`v-show` 始终会在 DOM 中保留元素，只是通过 CSS 的 `display` 属性控制元素的显示和隐藏。

```vue
<h1 v-show="ok">Hello!</h1>
```

## 6. Vue 循环语句

​	在 Vue 中，循环语句主要通过 `v-for` 指令来实现，用于遍历数组或对象，生成对应数量的元素。

### 6.1. 遍历数组

```vue
<li v-for="(item, index) in items"></li>
```

### 6.2. 遍历对象

```vue
<li v-for="(value, key, index) in object"></li>
```

- **key**：使用 `v-for` 渲染列表时，必须为每个项提供一个唯一的 `key` 属性，以便 Vue 能够识别每个项的唯一性，从而进行高效的 DOM 更新；
- **嵌套循环**：可以嵌套使用多个 `v-for` 来渲染多维数组或对象结构。

### 6.3. 迭代整数

​	`v-for` 也可以循环整数。

```vue
<li v-for="n in 10"></li>
```

### 6.4. 在组件上使用 v-for

​	在自定义组件上，可以像在任何普通元素上一样使用 `v-for` 。

```vue
<my-component v-for="item in items" :key="item.id"></my-component>
```

## 7. Vue 组件

​	每个 Vue 组件都是一个独立的 Vue 实例，具有自己的模板、数据、方法和生命周期钩子，使得组件可以自包含地定义和管理自己的功能和样式。

### 7.1. 组件的特性和优势

- **复用性**：组件可以在不同的地方多次使用，提高代码的复用性和可维护性；
- **封装性**：每个组件都是独立的作用域，可以封装自己的状态和逻辑，避免全局污染；
- **组合性**：可以通过组合多个小组件构建复杂的界面；
- **响应式**：组件的数据响应式地绑定到视图，数据更新时自动更新视图；
- **模块化**：支持模块化开发，可以使用现代前端工具链进行构建和管理。

### 7.2. 组件创建

#### 7.2.1. 全局组件

​	可以通过 `component` 全局注册。

```vue
<script>
const app = Vue.createApp({})

app.component('runoob', {
  template: '<h1>Self-define component</h1>'
})
</script>
```

#### 7.2.2. 局部组件

​	全局注册往往是不够理想的，可能会包含不需要的组件在最终的构建结果中，这造成了用户下载的 JavaScript 的无谓的增加。可以通过一个普通的 JavaScript 对象来定义组件。

```vue
<script>
const ComponentA = {
  /* ... */
};
const ComponentB = {
  /* ... */
}
</script>
```

​	然后在 components 选项中定义需要的组件。

```vue
<script>
const app = Vue.createApp({
  components: {
    'component-a': ComponentA,
    'Component-b': ComponentB
  }
})
</script>
```

### 7.3. 单文件组件

​	使用单文件组件（ `.vue` 文件）能够更好地组织和管理 Vue 组件，一个单文件组件通常由三部分组成：模板、脚本和样式。

```vue
<!-- MyComponent.vue -->
<script setup>

</script>

<script>
export default {
  
}
</script>
<template>

</template>

<style scoped>

</style>
```

### 7.4. Prop

#### 7.4.1. 静态 prop

​	`prop` 是子组件用来接受父组件传递过来的数据的一个自定义属性。父组件的数据需要通过 `props` 把数据传给子组件，子组件需要显示地用 `props` 选项声明 `prop` 。

```vue
<div id="app">
  <site-name title="Google"></site-name>
  <site-name title="Runoob"></site-name>
  <site-name title="Taobao"></site-name>
</div>

<script>
const app = Vue.createApp({})

app.component('site-name', {
  props: ['title'],
  template: `<h4>{{ title }}</h4>`
})
  
app.mount('#app')
</script>
```

#### 7.4.2. 动态 prop

​	类似于用 `v-bind` 绑定 HTML 特性到一个表达式，也可以用 `v-bind` 动态绑定 `props` 的值到父组件的数据中。每当父组件的数据变化时，该变化也会传导给子组件。

```vue
<div id="app">
  <site-info
    v-for="site in sites"
    :id="site.id"
    :title="site.title"
  ></site-info>
</div>

<script>
const Site = {
  data() {
    return {
      sites: [
        {id: 1, title: 'Google'},
        {id: 2, title: 'Runoob'},
        {id: 3, title: 'Taobao'}
      ]
    }
  }
}

const app = Vue.createApp(Site)

app.component('site-info', {
	props: ['id', 'title'],
  template: `<h4>{{ id }} - {{ title }}</h4>`
})
  
app.mount('#app')
</script>
```

#### 7.4.3. prop 验证

​	组件可以为 `props` 指定验证要求。为了定制 prop 的验证方式，可以为 `props` 中的值提供了一个带有验证需求的对象，而不是一个字符串数组。

```vue
<script>
Vue.component('my-component', {
	props: {
    // 基础类型检查（null 和 undefined 会通过任何类型验证）
    propA: Number,
    // 多个可能的类型
    propB: [String, Number],
    // 必填的字符串
    propC: {
    	type: String,
    	required: true
  	},
  	// 带有默认值的数字
    propD: {
      type: Nuber,
      default: 100
    },
    // 带有默认值的对象
    propE: {
      type: Object,
      // 对象或数组的默认值必须从一个工厂函数获取
      default: function() {
        return { message: 'Hello' }
      }
    },
    // 自定义验证函数
    propF: {
      validator: function (value) {
        return ['success', 'warning', 'danger'].indexof(value) !== -1
      }
    }
  }
})
</script>
```

**注意**：当 prop 验证失败时，Vue 将会产生一个控制台警告。type 可以是原生构造器，也可以是自定义构造器，使用 `instanceof` 检测。

## 8. Vue 计算属性

​	计算属性用于根据其他数据的变化，动态计算衍生出来的属性值，而且具有缓存机制，只有相关依赖发生变化时，才会重新计算。









