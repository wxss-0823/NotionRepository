# Lua 教程

## 1. Lua 基本语法

### 1.1. 交互式编程

```shell
lua -i
# 或
lua
```

### 1.2. 脚本式编程

​	编写脚本，并保存为以 `.lua` 结尾的文件，并执行。

```shell
lua script_name.lua
```

### 1.3. 注释

#### 1.3.1. 单行注释

​	当行注释以两个连字符 `--` 开头，后面跟随的内容将被解释器忽略。

```lua
-- 注释
```

#### 1.3.2. 多行注释

​	多行注释以 `--[[` 开始，以 `]]` 结束。

```lua
--[[
	多行注释
]]
```

**注意：**Lua 不支持嵌套注释。

### 1.4. 标识符

​	Lua 标识符用于定义一个变量，标识符以一个字母 `A ~ Z` 或 `a ~ z` 或 `_` 开头后加上字母，下划线，数字。

### 1.5. 关键词

<table>
  <tr>
  	<td>and</td>
    <td>break</td>
    <td>do</td>
    <td>else</td>
  </tr>
  <tr>
  	<td>elseif</td>
    <td>end</td>
    <td>false</td>
    <td>for</td>
  </tr>
  <tr>
  	<td>function</td>
    <td>if</td>
    <td>in</td>
    <td>local</td>
  </tr>
  <tr>
  	<td>nil</td>
    <td>not</td>
    <td>or</td>
    <td>repeat</td>
  </tr>
  <tr>
  	<td>return</td>
    <td>then</td>
    <td>true</td>
    <td>until</td>
  </tr>
  <tr>
  	<td>while</td>
    <td>goto</td>
  </tr>
</table>

**注意：**以下划线开头连接一串大写字母的名字，如： `_VERSION`，被保留用于 Lua 内部全局变量。

### 1.6. 全局变量

​	在默认情况下，变量总是认为是全局的。全局变量不需要声明，给一个变量赋值后即创建了这个全局变量，访问一个没有初始化的变量也不会出错，会得到结果 `nil` 。

​	如果需要删除一个全局变量，只需要将其赋值为 `nil` 。



