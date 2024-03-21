---
nav:
  title: Html+Css
---

# Css 溢出如何处理？overflow 值的不同区别

### 文本溢出处理

- 设置容器宽度： width:: [value]
- 强制文本一行显示：white-space: nowrap

  - normal：默认值，空白会被浏览器忽略
  - nowwrap：文本不会换行，文本会在同一行上继续，直到遇到标签为止
  - pre：空白会被浏览器保留，其行为方式类似 HTML 中的 pre 标签；
  - pre-wrap：保留空白序列，但是保留换行符
  - inherit：规定应该从父元素继承 white-space 属性值；（ie 浏览器不支持此属性）

- 溢出内容隐藏： overflow: hidden
  - visible: 默认值，内容不会修剪
  - hidden: 内容被修剪，并且其余内容是不可见的
  - scroll: 内容被修剪，但是会有滚动条
  - auto: 如果内容被修剪，则浏览器会显示滚动条，以便查看其它的内容；（超出会显示，不超出不显示，只显示 y 方向的）
  - inherit：规定应该从父元素继承 overflow 属性值
- 溢出省略： text-overflow: ellipsis
  - clip：不显示省略号（...），而是简单的裁切
  - ellipsis：当对象文本溢出时，显示省略标记
