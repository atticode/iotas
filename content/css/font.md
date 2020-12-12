+++
title = "CSS font 属性"
date = 2020-11-05T23:46:18+08:00
tags = ["CSS"]
+++



## 字体

### font-family 字体种类
1. 五个常用的字体名称：serif, sans-serif, monospace, cursive, fantasy

| 名称       | 定义                                                                     |
|------------|--------------------------------------------------------------------------|
| serif      | 有衬线的字体（衬线一词是指字体笔画尾端的小装饰，存在于某些印刷体字体中） |
| sans-serif | 没有衬线的字体                                                           |
| monospace  | 每个字符具有相同宽度的字体，通常用于代码列表                             |
| cursive    | 用于模拟笔迹的字体，具有流动的连接笔画                                   |
| fantasy    | 用来装饰的字体                                                           |

2. 字体栈(font stack)
设置font-family属性，其值由几个用逗号分离的字体名称组成

``` css
/* 字体名称包含空格的需要用双引号包裹 */
p {
  font-family: "Trebuchet MS", Verdana, sans-serif;
}
```

### font-size 字体大小
1. 常用单位

| 单位 | 说明                                      |
|------|-------------------------------------------|
| px   | 像素: 这是一个绝对单位                    |
| em   | 1em 等于当前元素的父元素上设置的字体大小  |
| rem  | 1rem 等于HTML中的根元素(<html>)的字体大小 |

### font-style 字体样式
用来打开和关闭文本italic(斜体)
1. 取值

| 值      | 说明                                                                                                 |
|---------|------------------------------------------------------------------------------------------------------|
| normal  | 将文本设置为普通字体(将存在的斜体关闭)                                                               |
| italic  | 如果当前字体的斜体版本可用，那么文本设置为斜体版本；如果不可用，那么会利用 oblique 状态来模拟 italic |
| oblique | 将文本设置为斜体字体的模拟版本，也就是将普通文本倾斜的样式应用到文本中                               |

### font-weight 字体粗细
设置文字的粗体大小
1. 取值

| 值      | 说明                                     |
|---------|------------------------------------------|
| normal  | 普通的字体粗细                           |
| bold    | 加粗的字体粗细                           |
| lighter | 将当前元素的粗体设置为比其父元素粗体更细 |
| bolder  | 将当前元素的粗体设置为比其父元素粗体更粗 |
| 100-900 | 数值粗体值                               |

### text-transform 文本转换
设置字体的转换
1. 取值

| 值         | 说明                                                       |
|------------|------------------------------------------------------------|
| none       | 防止任何转换                                               |
| uppercase  | 将所有文本转为大写                                         |
| lowercase  | 将所有文本转为小写                                         |
| capitalize | 转换所有单词让其首字母大写                                 |
| full-width | 将所有字形转换成固定宽度的正方形，类似于等宽字体，允许对齐 |

### text-decoration 文本装饰
设置字体上的文本装饰
1. 取值

| 值           | 说明                       |
|--------------|----------------------------|
| none         | 取消已经存在的任何文本装饰 |
| underline    | 文本下划线                 |
| overline     | 文本上划线                 |
| line-through | 穿过文本的线               |
2. 说明
此属性可以一次接受多个值。
此属性是一个缩写形式，由text-decoration-line, text-decoration-style, text-decoration-color 构成。

### text-shadow 文字阴影
设置文本的阴影，最多需要4个值
1. 属性

| 属性                            | 说明                                                                           |
|---------------------------------|--------------------------------------------------------------------------------|
| 属性1: 阴影与原始文本的水平偏移 | 它向左/右移动阴影，可以使用大多数的CSS单位，但是px是比较合适的，这个值必须指定 |
| 属性2: 阴影与原始文本的垂直偏移 | 效果基本上就像水平偏移，它向上/向下移动阴影，这个值必须指定                    |
| 属性3: 模糊半径                 | 更高的值意味着阴影分散得更广泛。如果不包含此值，则默认为0，这意味着没有模糊    |
| 属性4: 阴影的基础颜色           | 可以使用大多数的CSS颜色单位，如果没有指定，默认为black                         |
2. 注意
正偏移值可以向右移动阴影，但也可以使用负偏移值来左右移动阴影
3. 多种阴影
可以包含以逗号分隔的多个阴影值，将多个阴影应用于同一文本

```css
p {
  text-shadow: -1px -1px 1px #aaa,
               0px 4px 1px rgba(0, 0, 0, 0.5),
               4px 4px 5px rgba(0,0,0,0.7),
               0px 0px 7px rgba(0,0,0,0.4);
}
```

## 文本布局

### text-align 文本对齐
用来控制文本如何和它所在的内容盒子对齐
1. 取值

| 值      | 说明                                                   |
|---------|--------------------------------------------------------|
| left    | 左对齐文本                                             |
| right   | 右对齐文本                                             |
| center  | 居中文字                                               |
| justify | 使文本展开，改变单词之间的差距，使所有文本行的宽度相同 |

### line-height 行高
设置文本每行之间的高，可以接受大多数单位。
也可以设置一个无单位的值，作为乘数，通常这种是比较好的做法。
无单位的值乘以 font-size 来获得 line-height。

### letter-spacing 字母间距
设置文本中的字母与字母之间的间距。

### work-spacing 单词间距
设置文本中的单词与单词之间的间距。

### text-indent 
指定文本内容的第一行前面应该留出多少的水平空间

### text-overflow
定义如何向用户表示存在被隐藏的的溢出内容

### white-space
定义如何处理元素内部的空白和换行


## Font 简写
通过 font 的简写方式来设置, 属性设置顺序: 
```css
font-style, font-variant, font-weight, font-stretch, font-size, line-height, and font-family.
```

这些属性中，只有font-size和font-family是一定要指定的。




## 参考文档
1. [MDN-Font](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/%E4%B8%BA%E6%96%87%E6%9C%AC%E6%B7%BB%E5%8A%A0%E6%A0%B7%E5%BC%8F/Fundamentals)
