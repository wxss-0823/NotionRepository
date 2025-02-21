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

### 8.1. 声明计算属性

```vue
<template>
	<div>
    <p>商品名称：{{ productName}}</p>
    <p>商品价格：{{ formattedPrice }}</p>
  </div>
</template>

<script>
import { reactive, computed } from 'vue';
  
export default {
  setup() {
    // 响应式数据
    const state = reactive({
      name: 'phone',
      price: 2000
    });
    
    // 计算属性
    const productName = computed(() => {
      return `优惠 ${state.name}`;
    });
    
    const formattedPrice = computed(() => {
      return `￥${state.price.toFixed(2)}`;
    });
    
    return {
      productName,
      formattedPrice,
      increasePrice
    };
  }
};
</script>
```

### 8.2. computed vs. methods

​	可以使用 `methods` 来替代 `computed` ，效果上两个都是一样的，但是 `computed` 是基于它的依赖缓存，只有相关依赖发生改变时才会重新取值；而使用 `methods` ，在重新渲染时，函数总会重新调用执行。

### 8.3. computed setter

​	上述定义的函数可以理解为 `computed getter` ，`computed` 属性默认只有 `getter` ，不过在需要时也可以提供一个 `setter` 。

```vue
<script>
const app = {
  data() {
    return {
      name: 'Google',
      url: 'https://www.google.com'
    };
  },
  computed: {
    site: {
      get: function () {
        return this.name + ' ' + this.url;
      },
      set: function (newSite) {
        let names = newSite.split(' ');
        this.name = names[0];
        this.url = names[names.length - 1];
      }
    }
  }
}

vm = Vue.createApp(app).mount('#app')
</script>
```

## 9. Vue 监听属性

​	可以通过 `watch` 来响应数据的变化。`watch` 的作用是用于监测响应式属性的变化，并在属性发生变化时执行特定的操作，它是 Vue 的一种响应式机制。

```vue
<div id="app">
  <p>Counter: {{ counter }}</p>
  <button @click = "counter++">Click me</button>
</div>

<script>
const app = {
  data() {
    return {
      counter: 1
    }
  }
}

vm = Vue.createApp(app).mount('#app')
vm.$watch('counter', function(nval, oval) {
  alert("Counter value from" + oval + 'to' + nval)
});
</script>
```

### 9.1. 异步加载

​	异步数据的加载 Vue 通过 `watch` 选项提供了一个更通用的方法，来响应数据的变化。

```vue
<script>
const watchExampleVM = Vue.createApp({
  data() {
    return {
      question: '',
      answer: '每个问题结尾需要输入 ? 号'
    }
  },
  watch: {
  	// 每当 question 改变时，运行此功能
  	question(newQuestion, oldQuestion) {
      if (newQuestion.indexOf('?') > -1 || newQuestion.indexOf('？') > -1) {
        this.getAnswer()
      }
    }
	},
  methods: {
    getAnswer() {
      this.answer = 'Loading...'
      axios
      	.get('try/ajax/json_vuetest.php')
      	.then(response => {
        	this.answer = response.data.answer
      	})
      	.catch(error => {
					this.answer = "Error! Can't access API." + error
      	})
    }
  }
}).mount('#watch-example')
</script>
```

### 9.2. 用法总结

#### 9.2.1. 基本用法

​	在 Vue 3 中，`watch` 函数用于监听响应式属性。当监听的属性值发生变化时，Vue 会触发回调函数执行。

```javascript
import { reactive, watch } from 'vue'

export default {
  setup() {
    const state = reactive({
      count: 0
    });
    
    watch(
    	() => state.count,
      (newVal, OldVal) => {
        console.log(`count changed from ${oldVal} to ${newVal}`);
      }
    );
    
    return { state };
  }
};
```

#### 9.2.2. 监听多个响应式属性

​	如果需要同时监听多个响应式的属性，可以通过一个数组来传递监听的多个属性。

```javascript
watch(
	[() => state.count, () => state.name],
  ([newCount, oldCount], [oldCount, oldName]) => {
    console.log(`count changed from ${oldCount} to ${newCount}`);
    console.log(`name changed from ${oldName} to ${newName}`);
);
```

#### 9.2.3. 深度监听

​	如果需要监听的是一个对象或数组，并希望对齐内部的嵌套属性进行监听，可以使用 `deep: true` 选项，这会监听对象的所有属性变化。

```javascript
watch(
	() => state.user,
  (newVal, oldVal) => {
    console.log('User object changed:', newVal, oldVal);
  },
  { deep: true }
);
```

#### 9.2.4. 立即执行

​	默认情况下，`watch` 只会在监听的值发生变化时触发回调，如果希望在组件加载时就立即执行一次回调，可以设置 `immediate: true` 。

```javascript
watch(
	() => state.count,
  (newVal, OldVal) => {
 		console.log(`count changed from ${oldVal} to ${newVal}`);
  },
  { immediate: true }
);
```

#### 9.2.5. 异步操作

​	如果在 `watch` 中需要执行异步操作，可以直接在回调函数中使用 `async` 和 `await` ，这可以处理诸如 API 请求、数据存储等操作。

```javascript
watch(
	() =>state.count,
  async (newVal, OldVal) => {
    console.log(`count changed from ${oldVal} to ${newVal}`);
    await fetch(`https://api.example.com/count/${newVal}`);
  }
);
```

#### 9.2.6. 监听多个属性并使用 handler 函数

​	可以将 `watch` 用作监听多个属性的处理程序。

```javascript
const handler = ([newCount, oldCount], [newName, oldName]) => {
  console.log(`count changed from ${oldCount} to ${newCount}`);
  console.log(`name changed from ${oldName} to ${newName}`);
};

watch(
	[() =>state.count, () =>state.name],
  handler
);
```

#### 9.2.7. watchEffect 简化版的监听

​	Vue 3 还提供了 `watchEffect` API ，它比 `watch` 更加简洁，可以自动地跟踪响应式数据的变化，而不需要指定具体的数据源。

```javascript
watchEffect(() => {
	console.log(`count is: ${state.count}`);
});
```

#### 9.2.8. flush 选项

​	`flush` 选项用于控制 `watch` 的回调执行时机。默认情况下，`watch` 回调会在 DOM 更新后执行，如果需要在更新之前执行回调，可以使用 `flush: 'pre'` 。

```javascript
watch(
	() => state.count,
	(newVal, oldVal) => {
		console.log(`count changed from ${oldVal} to ${newVal}`);
	},
	{ flush: 'pre' }
);
```

## 10. Vue 样式绑定

### 10.1. Vue.js class

​	`class` 和 `style` 是 HTML 元素的属性，用于设置元素的样式，可以用 `v-bind` 来设置样式属性。`v-bind` 在处理 `class` 和 `style` 时，表达式除了可以使用字符串之外，还可以是对象或数组。

#### 10.1.1. class 属性绑定

​	动态的传递 `class` 参数，或者动态使能其中一部分 `class` 。当 `isActive=true` 时，`class` 为 `active` ；否则无 `class` 绑定。

```vue
<div v-bind:class="{ 'active': isActive }"></div>
```

​	同理，也可以传入多个 `class` ，选择性的使能其中部分或者全部。

```vue
<div v-bind:class="{ 'active': isActive, 'text-danger': hasError }"></div>
```

​	`:class` 指令也可以与普通的 `class` 属性共存。

```vue
<div class="static" v-bind:class="{ 'active': isActive }"></div>
```

 	此外，也可以绑定一个返回对象的计算属性。

```vue
<div :class="{classObject}"></div>

<script>
export default {
	data() {
    return {
      isActive: true,
      error: null
    };
  },
  computed: {
    classObject() {
      return {
        active: this.isActive && !this.error,
        'text-danger': this.error && this.error.type == 'fatal'
      };
    }
  }
};
</script>
```

​	也可以把一个数组传给 `v-bind:class` 。

```vue
<div class="static" :class="[activeClass, errorClass]"></div>

<script>
export default {
  data() {
    return {
      activeClass: "active",
      errorClass: "text-danger"
    };
  }
};
</script>
```

​	还可以使用三元表达式来切换列表中的 `class` 。

```vue
<div id="app">
  <div class="static" :class="[isActive ? activeClass : '', errorClass]"></div>
</div>
```

### 10.2. Vue.js style

​	可以在 `v-bind:style` 直接设置样式，简写为 `:style` 。

```vue
<div id="app">
  <div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>
</div>

<script>
export default {
  data() {
    return {
      activeColor: 'red',
      fontSize: 30
    };
  }
};
</script>
```

​	也可以直接绑定到一个样式对象，让模板更清晰。

```vue
<div id="app">
  <div :style="styleObject"></div>
</div>

<script>
export default {
  data() {
    return {
      styleObject: {
        color: 'red',
        fontSize: 30px
      };
    }
  }
};
</script>
```

​	`v-bind:style` 可以使用数组将多个样式对象应用到一个元素上。

```vue
<div id="app">
  <div :style="[baseStyles, overridingStyles]"></div>
</div>
```

**注意**：当 `v-bind:style` 使用需要特定前缀的 CSS 属性时，Vue.js 会自动侦测并添加响应的前缀。

​	可以为 `style` 绑定中的 property 提供一个包含多个值的数组，常用于提供多个带前缀的值，这样写只会渲染数组中最后一个被浏览器支持的值。

```vue
<div :style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }"></div>
```

### 10.3. 组件上使用 class 属性

#### 10.3.1. 单个根元素

​	当在带有单个根元素的自定义组件上使用 `class` 属性时，这些 `class` 会被添加到该元素中，现有的 `class` 将不会被覆盖。

```vue
<div id="app">
  <github class="classC classD"></github>
</div>

<script>
const app = Vue.createApp({});
  
app.component('github', {
  template: `<h1 class="classA, classB">I like github!</h1>`
})
</script>
```

​	对于带数据绑定的 `class` 也同样适用。

```vue
<my-component :class="{ active: isActive }"></my-component>
```

#### 10.3.2. 多个根元素

​	如果一个组件具有多个根元素，需要定义哪些部分将会接收这个类。可以使用 `$attrs` 组件的属性执行此操作。

```vue
<div id="app">
  <github class="classA"></github>
</div>

<script>
const app = Vue.createApp({})

app.component('github', {
  template: `
  	<p :class="$attrs.class">I like github!</p>
  	<span>This is a sub-component</span>
  `
})
</script>
```

## 11. Vue 事件处理

​	可以使用 `v-on` 指令来监听 DOM 事件，从而执行 JavaScript 代码。`v-on` 指令可以缩写为 `@` 符号。

### 11.1. 事件绑定

​	通常情况下，需要使用一个方法从事件调用 JavaScript 方法。`v-on` 可以接受一个定义的方法作为调用。

```vue
<div id="app">
  <button @click="greet">
    Click me!
  </button>
</div>

<script>
const app = {
  data() {
    return {
      name: 'wxss'
    };
  },
  methods: {
    greet(event) {
      alert('Hello ' + this.name + '!')
      if (event) {
        alert(event.target.tagName)
      }
    }
  }
};
  
Vue.createApp(app).mount("#app")
</script>
```

​	除了直接绑定到一个方法，还可以用内联的 JavaScript 语句。

```vue
<div id="app">
  <button @click="say(Hello)">
    Say hi
  </button>
</div>

<script>
const app = {
  data() {
    
  },
  methods: {
    say(message) {
      alert(message)
    }
  }
};
  
Vue.createApp(app).mount("#app")
</script>
```

​	事件处理程序中可以有多个方法，这些方法由逗号运算符分隔，方法按照顺序依次执行。

```vue
<div id="app">
  <button @click="one($event), two($event)">Click me!</button>
</div>
```

### 11.2. 事件修饰符

​	Vue.js 为 `v-on` 提供了事件修饰符来处理 DOM 事件细节，通过 `.` 表示的指令后缀来调用修饰符。

| 修饰符     | 功能                   |
| ---------- | ---------------------- |
| `.stop`    | 阻止冒泡               |
| `.prevent` | 阻止默认事件           |
| `.capture` | 阻止捕获               |
| `.self`    | 只监听触发该元素的事件 |
| `.once`    | 只触发一次             |
| `.left`    | 左键事件               |
| `.right`   | 右键事件               |
| `.middle`  | 中间滚轮事件           |

### 11.3. 按键修饰符

​	Vue 允许为 `v-on` 在监听键盘事件时添加按键修饰符。

```vue
<!-- 只有在 keycode 是 13 时调用 vm.submit() -->
<input v-on:keyup.13="submit">
```

​	记住所有的 KeyCode 比较困难，因此 Vue 为最常用的按键提供了别名。

| 按键别名  | 按键名   |
| --------- | -------- |
| `.enter`  | 回车     |
| `.tab`    | 制表     |
| `.delete` | 删除     |
| `.esc`    | 退出     |
| `.space`  | 空格     |
| `.up`     | 上键     |
| `.down`   | 下键     |
| `.left`   | 左键     |
| `.right`  | 右键     |
| `.ctrl`   | 控制     |
| `.alt`    | 可选     |
| `.shift`  | 切换     |
| `.meta`   | 元       |
| `.left`   | 鼠标左键 |
| `.right`  | 鼠标右键 |
| `.middle` | 鼠标中键 |

### 11.4. exact 修饰符

​	`.exact` 修饰符允许控制由精确的系统修饰符组合触发的事件，用于区分单个系统修饰符与组合系统修饰。

```vue
<!-- 即使 Alt 和 Shift 被一同按下，也会触发 -->
<button @click.ctrl="onClick">A</button>

<!-- 有且只有 Ctrl 被按下时才触发 -->
<button @click.ctrl.exact="onClick">A</button>

<!-- 没有任何系统修饰符被按下时才触发 -->
<button @click.exact="onClick">A</button>
```

## 12. Vue 表单

​	可以用 `v-model` 指令在表单 `<input>` 、`<textarea>` 、`<select>` 等元素上创建双向数据绑定。`v-model` 会根据控件类型自动选取正确的方法来更新元素，会忽略所有表单元素的 `value` 、`checked` 、`selected` 等属性的初始值，使用由 `data` 选项声明的初始值。

​	`v-model` 在内部为不同的输入元素使用不同的属性，并抛出不同的事件。

- `text` 和 `textarea` 元素使用 `value` 属性和 `input` 事件；
- `checkbox` 和 `radio` 使用 `checked` 属性和 `change` 事件；
- `select` 字段将 `value` 作为属性并将 `change` 作为事件。

### 12.1. 输入框

```vue
<div id="app">
	<input v-model="message" placeholder="Edit me...">
</div>

<script>
const app = {
  data() {
    return {
      message: ""
    };
  }
}
  
Vue.createApp(app).mount("#app")
</script>
```

### 12.2. 文本输入框

```vue
<div id="app">
  <textarea v-model="message" placeholder="Multi lines text..."
</div>
  
<script>
const app = {
  data() {
    return {
      message: 'https://github.com/wxss-0823'
    }
  }
}

Vue.create(app).mount("#app")
</script>
```

### 12.3. 复选框

​	复选框如果没有指定 `value` 的值，默认为逻辑值；如果指定了 `value` 的值，`v-model` 会绑定 `value` 的值。如果有多个复选框，结果可以保存在同一个数组内，即相同名称的 `v-model` 中。

```vue
<div id="app">
  <p>Single checkbox</p>
  <input type="checkbox" id="checkbox" v-model="checked">
  <label for="checkbox">{{ checked }}</label>
  
  <p>Multi checkboxes</p>
  <input type="checkbox" id="google" value="Google" v-model="checkedNames">
  <label for="google">Google</label>
  <input type="checkbox" id="github" value="Github" v-model="checkedNames">
  <label for="github">Github</label>
  <input type="checkbox" id="firefox" value="Firefox" v-model="checkedNames">
  <label for="firefox">Firefox</label>
</div>

<script>
const app = {
  data() {
    return {
      checked: false,
      checkedNames: []
    }
  }
}

Vue.createApp(app).mount("#app")
</script>
```

### 12.4. 单选按钮

```vue
<div id="app">
  <input type="radio" id="google" value="Google" v-model="picked">
  <label for="google">Google</label>
  <input type="radio" id="github" value="Github" v-model="picked">
  <label for="github">Github</label>
  <br>
  <span>Selected value: {{ picked }}</span>
</div>

<script>
const app = {
  data() {
    return {
      picked: ''
    }
  }
}

Vue.createApp(app).mount("#app")
</script>
```

### 12.5. select 列表

​	单选时会绑定选项对应的 `value` ，多选时会绑定到一个数组。也可以使用 `v-for` 循环输出选项，简化代码结构。

```vue
<div id="app">
  <select v-model="selected" name="site">
    <option value="">Please select a site.</option>
    <option value="www.google.com">Google</option>
    <option value="www.github.com">Github</option>
  </select>
</div>

<script>
const app = {
  data() {
    return {
      selected: ""
    }
  }
}

Vue.createApp(app).mount("#app")
</script>
```

### 12.6. 值绑定

​	对于表单元素，`v-model` 绑定的值通常是静态字符串（对于复选框也可能是布尔值），但是有时候需要把值绑定到当前活动实例的一个动态属性上，可以用 `v-bind` 实现。

#### 12.6.1. 复选框

```vue
<input type="checkbox" v-model="toggle" true-value="yes" false-value="no" />
```

​	当选中时，`v-model` 绑定的 `toggle` 的值为 `yes` ，否则，值为 `no` 。

#### 12.6.2. 单选框

```vue
<input type="radio" v-model="pick" v-bind:value="a" />
```

​	当选中时，`v-model` 绑定的值 `pick` 为动态属性 `a` 。

#### 12.6.3. 选择框选项

```vue
<select v-model="selected">
  <option :value="{ number: 13 }">123</option>
</select>
```

​	当选中时，`v-model` 绑定的值 `selected` 为对象字面量。

### 12.7. 修饰符

#### 12.7.1. lazy

​	默认情况下，`v-model` 在 `input` 事件中同步输入框的值和数据，可以添加一个修饰符 `lazy` ，从而转变为在 `change` 事件中同步。

```vue
<input v-model.lazy="msg">
```

#### 12.7.2. number

​	如果需要自动将用户的输入值转为 Number 类型，且如果原值的转换结果为 NaN，则返回原值时，可以添加一个修饰符 `number` 。

```vue
<input v-model.number="age" type="number">
```

​	这通常很有用，因为即使在 `type="number"` 时，HTML 中输入的值也总是返回字符串类型。

#### 12.7.3. trim

​	如果需要自动过滤用户输入的首尾空格，可以添加 `trim` 修饰符。

```vue
<input v-model.trim="msg">
```

## 13. Vue 自定义指令

​	除了默认设置的核心指令（`v-model` 和 `v-show`），Vue 也允许注册自定义指令。

### 13.1. 注册指令

#### 13.1.1. 全局指令

```vue
<script>
const app = Vue.createApp({})

app.directive('focus', {
  mounted(el) {
    // 聚焦元素
    el.focus()
  }
})
  
app.mount("#app")
</script>
```

#### 13.1.2. 局部指令

​	也可以使用 `directives` 选项来注册局部指令，这样指令只能在当前实例中使用。

```vue
<script>
const app = {
  data() {
    return {
    }
  },
  directives: {
    focus: {
      mounted(el) {
        el.focus()
      }
    }
  }
}

Vue.createApp(app).mount("#app")
</script>
```

### 13.2. 钩子

#### 13.2.1. 钩子函数

​	指令定义函数提供了几个钩子函数：

- `created`：在绑定元素的属性或事件监听器被应用之前调用；
- `beforeMount`：指令第一次绑定到元素并且在挂在父组件之间调用；
- `mounted`：在绑定元素的父组件被挂载后调用；
- `beforeUpdate`：在更新包含组件的 VNode 之前调用；
- `updated`：在包含组件的 VNode 及其子组件的 VNode 更新后调用；
- `beforeUnmount`：当指令与绑定元素的父组件卸载之前时，只调用一次；
- `unmounted`：当指令与元素接触绑定且父组件已卸载时，只调用一次。

#### 13.2.2. 钩子函数的参数

##### el

​	指令绑定到的元素，可用于直接操作 DOM。

##### binding

​	一个对象，包含以下属性：

- `instance`：使用指令的组件实例；
- `value`：传递给指令的值，例如：`v-my-directive=2`；
- `oldValue`：先前的值，仅在 `beforeUpdate` 和 `updated` 中可用，值是否已更改都可用；
- `arg`：传递给指令的参数，例如：`v-my-directive:foo` ；
- `modifiers`：包含修饰符的对象，例如：`v-my-directive.foo.bar` ，修饰符对象为 `{foo: true, bar: true}` 。

##### vnode

​	在现代前端框架中，虚拟 DOM（Virtual DOM）是一个核心概念，虚拟节点（VNode）是虚拟 DOM 的基础元素，是对真实 DOM 的一个抽象表示，是一个描述 DOM 结构的 JavaScript 对象，而不是实际的 DOM 元素。

##### prevNode

​	上一个虚拟节点，仅在 `beforeUpdate` 和 `updated` 钩子函数中可用。

## 14. Vue 路由

​	Vue 路由允许通过不同的 URL 访问不同的内容，通过 Vue 可以实现多视图的单页 Web 应用（Single Page web Application，SPA）。

​	Vue.js 路由需要载入 [vue-router 库](https://github.com/vuejs/vue-router-next) ，使用文档详见 [中文文档](https://router.vuejs.org/zh/guide/) 。

### 14.1. router-link

​	Vue Router 可以通过自定义组件 `router-link` 来创建链接，在不重新加载页面的情况下更改 URL ，处理 URL 的生成以及编码。

#### 14.1.1. to

​	表示目标路由的链接。当被点击后，内部会立刻把 `to` 的值传到 `router.push()` ，所以这个值可以是一个字符串或是描述目标位置的对象。

```vue
<!-- 字符串 -->
<router-link to="home">Home</router-link>
<!-- 渲染结果 -->
<a href="home">Home</a>

<!-- 使用 v-bind 的 JS 表达式 -->
<router-link v-bind:to="'home'">Home</router-link>

<!-- 简写形式 -->
<router-link :to="'home'">Home</router-link>

<!-- 描述目标位置的对象 -->
<router-link :to="{ path: 'home' }">Home</router-link>

<!-- 命名的路由 -->
<router-link :to="{ name:  'user', params: { userId: 123 } }">User</router-link>

<!-- 带查询参数 -->
<router-link :to="{ path: 'register', query: { plan: 'private' } }">Home</router-link>
```

#### 14.1.2. replace

​	设置 `replace` 属性的话，当点击时，会调用 `router.replace()` ，而不是 `router.push()` ，导航后不会留下 `history` 记录。

```vue
<router-link :to="{ path: '/abc' }" replace></router-link>
```

#### 14.1.3. append

​	设置 `append` 属性后，则在当前路径后追加其路径，即相对路径。

```vue
<router-link :to="{ path: 'relative/path' }" append></router-link>
```

#### 14.1.4. tag

​	当需要将 `router-link` 渲染成某种标签时，可以使用 `tag` 属性类指定何种标签。同样它还是会监听点击，触发导航。

```vue
<router-link :to="/foo" tag="li">foo</router-link>
```

#### 14.1.5. active-class

​	可以设置链接激活后使用的 CSS 类名，通过 `active-class` 属性指定。

```vue
<style>
  ._active{
    background-color: red;
  }
</style>

<router-link :to="{ path: '/route' }" active-class="_active">Router Link</router-link>
```

#### 14.1.6. exact-active-class

​	配置当链接被精确匹配时，应该激活的 `class` 。

```vue
<router-link :to="{ path: '/route' }" exact-active-class="_active">Router Link</router-link>
```

#### 14.1.7. event

​	声明可以用来触发导航的事件，可以是一个字符串或是一个包含字符串的数组。

```vue
<router-link :to="{ path: '/path' }" event="mouseover">Router Link</router-link>
```

### 14.2. router-view

​	`router-view` 将显示与 URL 对应的组件，可以把它放在任何地方，以适应布局。

## 15. Vue 混入

​	混入（Mixins）定义了一部分可复用的方法或者计算属性。混入对象可以包含任意组件选项。当组件使用混入对象时，所有混入对象的选项将被混入该组件本身的选项。

### 15.1. 选项合并

#### 15.1.1. 数据合并

​	当组件和混入对象含有同名选项时，这些选项将以恰当的方式混合。数据对象在内部会进行浅合并（一层属性深度），在和组件的数据发生冲突时，以组件数据优先。

```vue
<script>
const myMixin = {
  data() {
    return {
      message: "hello",
      foo: "google"
    }
  }
}

const app = Vue.createApp({
  data() {
    return {
      message: "goodbye",
      bar: "def"
    }
  },
	mixins: [myMixin]
})
</script>
```

#### 15.1.2. 钩子函数合并	

​	同名钩子函数将合并为一个数组，因此都将被调用。`mixin` 对象的钩子函数将在组件自身钩子函数之前调用。

```vue
<script>
const myMixin = {
  created() {
    console.log('mixin 对象的钩子被调用')
  }
}

const app = Vue.createApp({
  mixins: [myMixin],
  created() {
    console.log('组件钩子被调用')
  }
})
</script>
```

#### 15.1.3. 选项对象的合并

​	某些选项，例如：`method` 、`components` 、`directives` 等选项的值是一个对象，引入 `mixin` 对象后，这些值将被按键名合并为同一个对象。两个对象键名冲突时，取组件对象的键值对。

```vue
<script>
const myMixin = {
  methods: {
    foo() {
      console.log('foo')
    },
    conficting() {
      console.log('from mixin')
    }
  }
}

const app = Vue.createApp({
  mixins: [myMixin],
  methods: {
    bat() {
      console.log('bar')
    },
    conflicting() {
      console.log('from self')
    }
  }
})

app.mount("#app")
</script>
```

### 15.2. 全局混入

​	也可以全局注册混入对象，一旦使用全局混入对象，将会影响到所有之后创建的 Vue 实例。

```vue
<script>
const app = Vue.createApp({
  myOption: "hello"
})

app.mixin({
  created() {
    const myOption = this.$options.myOption
    if (myOption) {
      document.write(myOption)
    }
  }
})
  
app.mount("#app")
</script>
```



















