---
nav:
  path: /htmlcss/BFC
  title: 前端
group:
  path: /htmlcss
  title: HTML+CSS
---

# BFC

### 什么是 BFC

- BFC（Block Formatting Context）是指一个独立的块级格式化上下文，它决定了块级盒子如何布局，
  并且与它外部的其他内容相互独立。在前端开发中，理解 BFC
  的特点对于解决一些布局问题非常有帮助。

#### BFC 的特点

- **块级盒子独立性**内部的元素与外部的元素相互独立，这意味着 BFC
  内部的布局不受外部元素的影响，也不会影响到外部元素的布局。
- **垂直方向布局**内的元素在垂直方向上一个接一个地放置，因此不会出现浮动元素重叠的情况。这也意味着 BFC
  内部的浮动元素不会影响外部元素的布局，除非发生外部元素与 BFC 之间的重叠。
- **浮动元素包裹性** 会将浮动的子元素包裹在内部，防止浮动元素溢出到
  BFC 外部。
- **清除浮动**会将浮动的子元素包裹在内部，防止浮动元素溢出到 BFC
  外部。
- **阻止外边距合并**会将浮动的子元素包裹在内部，防止浮动元素溢出到
  BFC 外部。

### 如何解决 margin 塌陷问题

- 设置 float
- 设置 overflow 不为 visible
- 设置 position 为 flex 或者 fixed
- 设置行内块 display: inline-bloc

#### 块级盒子独立性

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      .oneStyleFather {
        border: 5px solid red;
      }
      .oneStyleChild {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <div>
      <h1>1.块级盒子独立性</h1>
      <div class="oneStyleFather">
        <div class="oneStyleChild">
          这是内部元素，BFC内部布局独立
        </div>
    </div>
  </body>
</html>
```

#### 垂直方向上的布局

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      .twoStyle {
        width: 400px;
        border: 1px solid;
      }
      .twoStyleFloatLeft {
        width: 100px;
        height: 100px;
        background-color: yellow;
      }
      .twoStyleFloatRight {
        width: 100px;
        height: 100px;
        background-color: blue;
      }
    </style>
  </head>
  <body>
    <div>
      <h1>2.垂直方向上的布局</h1>
      <div class="twoStyle">
        <div class="twoStyleFloatLeft">浮动元素1</div>
        <div class="twoStyleFloatRight">浮动元素2</div>
      </div>
    </div>
  </body>
</html>
```

#### 清除浮动

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      .threeStyle {
        overflow: hidden;
      }
      .threeStyleOne {
        float: left;
        width: 100px;
        height: 100px;
        background-color: yellow;
      }
      .threeStyleTwo {
        background-color: blue;
        clear: both;
      }
    </style>
  </head>
  <body>
    <div>
      <h1>3.清除浮动</h1>
      <div class="threeStyle">
        <div class="threeStyleOne">浮动元素1</div>
        <div class="threeStyleTwo">
          这是一个清除浮动的元素，可以防止父元素的高度塌陷
        </div>
      </div>
    </div>
  </body>
</html>
```

#### 阻止外边距合并

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      .fourStyle {
        border: 1px solid red;
        margin-bottom: 20px;
      }
      .fourStyleChild {
        border: 1px solid blue;
        margin-top: 30px;
      }
    </style>
  </head>
  <body>
    <div>
      <h1>4.阻止外边距合并</h1>
      <div class="fourStyle">
        <div class="fourStyleChild">
          这是内部元素，外边距不会与外部元素的外边距合并
        </div>
      </div>
    </div>
  </body>
</html>
```
