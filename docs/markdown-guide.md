<!-- toc -->

# Medup Markdown 语法介绍

Markdown 是一种纯文本格式的标记语言，它使用简单的标记语法来格式化文本。由 **Daring Fireball** 创建，markdown 原始语法在 [这里](https://daringfireball.net/projects/markdown/syntax)；多数 markdown parser 都兼容了标准语法，但也存在一些自定义的扩展语法。**Medup** 希望能够在保证常规标准语法的同时，能够实现掉所有主流的扩展语法。

## 标题

使用 `#` 符号来定义标题。在文本开头添加 `#` 符号，可以将文本转换为标题。数量越多，标题级别越低。

```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

`#` 和文本之间存在至少一个空格。
`#` 前面除了空白字符以外，不能有其他任何字符。
标题上除了普通文本以外，还可以是链接、图片等。

#### 渲染效果

> ### 三级标题
> #### 四级标题
> ##### 五级标题

## 无序列表

使用 `-`, `+` 或 `*` 来创建无序列表；同时，还可以使用两个空格或者 tab 编写嵌套的列表项。

```
- 项目 1
- 项目 2
- 项目 3

* 项目 1
* 项目 2
  * 嵌套项目 1
* 项目 3
```

`-` `+` 和 `*` 都可以用于创建无序列表，根据自己的习惯选择就行。

#### 渲染效果

* 项目 1
  * 嵌套项目 1
* 项目 2
* 项目 3

## 有序列表

使用数字和 `.` 创建有序列表。

#### 方式一
```
1. 项目 1
2. 项目 2
3. 项目 3
```

#### 方式二
```
1. 项目 1
1. 项目 2
1. 项目 3
```

数字后面紧跟 `.` 号，之间不能有空格存在。
`.` 号和文本项之间至少需要一个空白字符。
除了可以用 1 2 3 ... 的数字序列方式一之外，还可以只有用一个数字的方式二；根据自己的习惯选择。

#### 渲染效果

1. 项目 1
2. 项目 2
3. 项目 3

## 强调
使用 `*` 或 `_` 来定义文本强调，包括加粗和斜体。 单个 `*` 或 `_` 包围的文本被斜体表示，两个 `**` 或 `__` 是加粗表示，三个 `***` 或 `___` 是斜体同时加粗表示。

```
*这是斜体*
_这是斜体_

**这是粗体**
__这是粗体__

***这是粗体+斜体***
___这是粗体+斜体___
```

一些 markdown 解析要求 `*`， `_` 和文本之间不能有空白字符存在，比如：`\* 斜体 \*` `\_ 斜体 \_` `\*\* 粗体 \*\*` ，但是 Medup 的实现是允许这种写法的。Medup 是在保证严格语法的同时，尽量提供轻松书写，兼容一些误差。

#### 渲染效果

*这是斜体*
_这是斜体_
**这是粗体**
__这是粗体__
***这是粗体+斜体***
___这是粗体+斜体___

## 删除
使用 `~~` 删除一段文本。注意是两个波浪符号。

```
~~删除这里的文本~~
```

#### 渲染效果

~~删除这里的文本~~

## 链接

使用 `\[]()` 来创建链接。这是比较常用的链接创建方式，除了这种方式以外，还有另外两种方式，下面介绍。

```
[Example](https://example.com)
```

`[ ]` 方括号内是显式文本，`( )` 圆括号内是 URL 地址。
`](` 两个符号之间不能有空白字符存在，比如：`[Example]  (https://example.com)` 就是无效的链接。

#### 渲染效果

这是一个链接：[Example](https://example.com)

## 快速链接

使用 `<>` 快速创建 URL 链接。

```
<https://example.com>
<user@example.com>
```

`<>` 中必须是一个有效的 URL 或者 email 地址。

#### 渲染效果

<https://example.com>
<user@example.com>

## 引用链接

使用 `\[][]` 和 `\[]: ` 的组合语法创建引用式的链接，也有叫它参考链接的。引用链接的优势是可以很方便的在文章的多处内容使用同一个链接地址，链接地址被修改后，所有引用的地方都会保持同步更新。

```
[Example1][example_link]
[Example2][example_link]

[example_link]: https://example.com "title"
```

`\[][]` 处可以称为链接引用，`\[]: ` 处可以称为链接定义，在链接定义中 title 部分是可选的。通常我们可以将链接定义部分放到文章内容的尾部。

#### 渲染效果

[Example1][example_link]
[Example2][example_link]

[example_link]: https://example.com "title"

## 图片

使用 `\!\[]()` 来插入图片。

```
![替代文本](https://example.com/img.jpg)
```

和普通链接的语法不同之处只是在开头多了一个感叹号 `\!`，其他部分都一样。

#### 渲染效果

![这是一个图片](https://markdown.land/wp-content/uploads/2021/06/markdown-512px.png)

## 引用
使用 `>` 来引用文本。比如：本文的 *渲染效果* 部分都是引用。

```
> 这是一个单行引用文本
```
```
> 这是一个多行引用文本
> 这是一个多行引用文本
> 这是一个多行引用文本
```

`>` 和文本之间需要至少一个空白字符，并且 `>` 前面不能有任何其他非空白字符。引用文本中可以再使用所有的 markdown 语法，比如：

```
> 这是一个单行引用文本
>
> * 引用中嵌套项目 1
> * 引用中嵌套项目 2
> * 引用中嵌套项目 3
>
```

#### 渲染效果

> 这是一个多行引用文本
> 这是一个多行引用文本
> 这是一个多行引用文本

> * 引用中嵌套项目 1
> * 引用中嵌套项目 2
> * 引用中嵌套项目 3
>> 嵌套一个引用


## 代码

使用 `\`` 来标记文本中的代码。

```
这是一段文本，里面包含了一段代码: `print("Hello, world!")`。
```

代码标记  `\`` 和斜体，粗体的用法类似。

#### 渲染效果

这是一段文本，里面包含了一段代码: `print("Hello, world!")`。

## 代码块

使用 `\`\`\`` 来标记多行组成的一个代码块。本文 markdown 语法介绍部分都是在代码块中。

\```
这里放你的代码段
\```

#### 渲染效果
```
// This is the main function
fn main() {
    // Print text to the console
    println!("Hello World!");
}
```

## 转义
使用 `\\` 可以转义一些特殊字符，被转义后的字符将不会作为 markdown 语法标记进行解析，而是当做普通字符。可以被转义的字符包含：
* ~
* :
* *
* _
* `
* #
* +
* -
* .
* !
* [
* ]
* (
* )
* <
* >
* \

```
转义掉字符 "`": \`print("Hello, world!")\`。
```

#### 渲染效果
转义掉字符 "`": \`print("Hello, world!")\`。

## TODO 列表
我们可以在无序列表的基础上，通过添加 `[ ]` 或者 `[x]` 来实现 TODO 列表，`[ ]` 表示未完成项，`[x]` 表示完成项。

```
- [ ] 购买食材
    - [ ] 鸡蛋
- [x] 做晚餐
- [ ] 洗碗
```

#### 渲染效果
- [ ] 购买食材
    - [ ] 鸡蛋
- [x] 做晚餐
- [ ] 洗碗
