# TypeScript 教程

​	TypeScript 是 JacaScript 的一个超级，支持 [ECMAScript 6 标准](https://www.w3school.com.cn/js/js_es6.asp) 。

## 1. TypeScript 特性

​	相对 JavaScript，TypeScript 增加了许多关键功能，特别是围绕类型系统和代码结构的增强功能。

- **静态类型检查**：TypeScript 在编译时会检查代码类型是否匹配，能够发现许多潜在的错误。即使是简单的错误，也可以在编写代码时被捕获；
- **类型推断**：TypeScript 能够自动推断变量的类型，不需要显示声明类型；
- **接口和类型定义**：TypeScript 提供了 `interface` 和 `type` 关键字，允许定义复杂的数据结构，这对于项目中不同部分的代码协作和数据交互来说非常重要；
- **类和模块支持**：TypeScript 支持面向对象编程中的类（class）概念，增加了构造函数、继承、访问控制修饰符，并且支持 ES 模块化规范；
- **工具和编译器支持**：TypeScript 拥有良好的编译器支持；
- **兼容 JavaScript**：TypeScript 是 JavaScript 的超集，这意味着所有合法的 JavaScript 代码都是合法的 TypeScript 代码，这使得 JavaScript 项目可以逐步迁移到 TypeScript，而无需完全重写。

### 1.1. 静态类型

​	TypeScript 最大的特性就是增加了静态类型系统。在 TypeScript 中，开发者可以显示地声明变量、参数、返回值的类型，这样可以在编译时捕获很多潜在的类型错误。常见类型包括：`number`、`string`、`boolean`、`array`、`tuple`、`enum` 等，此外也支持自定义类型。

```typescript
let name: string = "wxss";
let age: number = 25;
```

### 1.2. 类型判断

​	TypeScript 可以自动判断变量类型，即使不显式声明类型，TypeScript 也会根据变量的赋值内容来推断类型，从而在大多数情况下，减少类型注解的书写量。

### 1.3. 接口

​	TypeScript 提供了接口（interface），允许定义复杂的对象结构。接口可以定义属性和方法，还可以通过 `implement` 关键字实现接口，或者通过 `extends` 进行扩展，便于定义复杂的数据类型。

### 1.4. 类型别名

​	类型别名（Type Aliases）可以为复杂的类型定义简短的别名，便于代码复用。

```typescript
type StringOrNumber = string | number;
let value: StringOrNumber = 42;
```

### 1.5. 枚举

​	TypeScript 引入了 `enum` 类型，用于定义一组命名的常量，提高代码的可读性。枚举在 JavaScript 中没有直接的对应。

```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right
}

let dir: Direction = Direction.Up;
```

### 1.6. 元组

​	元组允许定义具有固定数量和类型的数组。它适用于需要固定数据结构的场景。

```typescript
let point: [number, number] = [10, 20];
```

### 1.7. 访问控制修饰符

​	TypeScript 在类中提供了 `public`、`private` 和 `protected` 修饰符，允许控制属性或方法的可见性，支持更好的封装。

```typescript
class Person {
  private name: string;
  protected age: number;
  public constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}
```

### 1.8. 抽象类

​	TypeScript 支持抽象类，抽象类不能直接实例化，需要由子类实现。抽象类适用于定义通用行为和抽象方法的类层次结构。

```typescript
abstract class Animal {
  abstract makeSound(): void
}

class Dog extends Animal {
  makeSound() {
    console.log("Woof!")
  }
}
```

### 1.9. 泛型

​	TypeScript 支持泛型（Generics），允许在类、接口和函数中使用参数化泛型，使得代码可以使用不同类型需求，同时保持类型安全。

```typescript
function identity<T>(value: T): T {
  return value;
}

let num = identity<number>(42);
```

### 1.10. 模块和命名空间

​	TypeScript 提供了基于 ES6 的模块系统，使用 `import` 和 `export` 导入和导出模块。此外，TypeScript 还支持命名空间（Namespace），用于组织代码和避免命名冲突。

```typescript
// math.ts
export function add(a: number, b: number): number {
  return a + b;
}

//main.ts
import { add } from "./math";
console.log(add(2, 3));
```

### 1.11. 类型守卫

​	TypeScript 提供了类型守卫（Type Guards），可以在代码中检查变量类型，帮助编译器推断更加具体的类型。这对于联合类型尤为重要。

```typescript
function printId(id: string | number) {
  if (typeof id === "string") {
    console.log(id.toUpperCase());
  } else {
    console.log(id.toFixed(2))
  }
}
```

### 1.12. 可选链和空值合并运算符

​	TypeScript 增加了 JavaScript 的可选链（`?.`）和空值合并运算符（`??`），简化了代码中对可能为 `null` 或 `undefined` 值的处理。

```typescript
let users = {name: "wxss", address: {city: "YinChuan"}};
console.log(users?.address?.city);	// 如果 address 及 city 存在，则输出对应值，否则返回 undefined

let value = null;
console.log(value ?? "default")			// 如果 value 为 null 或 undefined，则返回 default
```

### 1.13. 类型兼容性和工具选择

​	TypeScript 提供了一些工具类型，如 `partial`、`pick`、`readonly`、`record` 等，这些类型可以帮助生成新的类型，简化类型定义。

```typescript
interface Todo {
	title: string;
  description: string;
}

let partialTdo: Partial<Todo> = { title: "Learn TypeScript" };		// 可选属性
```

### 1.14. 编译器错误检查

​	TypeScript 提供的编译器错误检查可以捕获 JavaScript 中不易发现的错误，如拼写错误、类型不匹配等，帮助提升代码质量。

### 1.15. ES 新特性支持

​	TypeScript 提前支持了一些还未在所有环境中普及的 ES 特性，如装饰器（Decorators）、异步迭代器等，且能够将其编译成兼容 JavaScript 的版本。

















