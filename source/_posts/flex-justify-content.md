---
title: "flex布局: justify-content"
date: 2020-02-06 18:07:58
tags:
  - CSS
categories: Web
---

# flex: justify-content

## 效果

### 效果一： row nowrap

```css
.container {
  position: relative;
  width: 100%;
  margin: 50px auto 0;
  border: 1px solid red;

  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
}
```

![nowrap](/images/flex/justify_content/nowrap.png)

### 效果二：row wrap

```css
.container {
  position: relative;
  width: 100%;
  margin: 50px auto 0;
  border: 1px solid red;

  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
```

![wrap](/images/flex/justify_content/wrap.png)

## 遗留问题

- justify-content: safe/unsafe center 的效果是什么？
- justify-content: left/right 的效果是什么？
- justify-content: start/end 的效果是什么？

## 源代码

> html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>justify-content</title>
    <link rel="stylesheet" href="./index.css" />
  </head>
  <body>
    <div class="app">
      <!-- center -->
      <!-- /* Pack items around the center */ -->
      <div class="container container1">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box4</div>
        <div class="box">box5</div>
      </div>
      <!-- flex-start -->
      <!-- /* Pack flex items from the start */ -->
      <div class="container container2">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box4</div>
        <div class="box">box5</div>
      </div>
      <!-- flex-end -->
      <!-- /* Pack flex items from the end */ -->
      <div class="container container3">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box4</div>
        <div class="box">box5</div>
      </div>

      <!-- /* Distributed alignment */ -->
      <!-- space-around -->
      <!-- /* 在每行上均匀分配弹性元素。相邻元素间距离相同。每行第一个元素到行首的距离和每行最后一个元素到行尾的距离将会是相邻元素之间距离的一半。 */ -->
      <div class="container container4">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box4</div>
        <div class="box">box5</div>
      </div>
      <!-- space-between -->
      <!-- /* 在每行上均匀分配弹性元素。相邻元素间距离相同。每行第一个元素与行首对齐，每行最后一个元素与行尾对齐。 */ -->
      <div class="container container5">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box4</div>
        <div class="box">box5</div>
      </div>
      <!-- space-evenly -->
      <!-- /* flex项都沿着主轴均匀分布在指定的对齐容器中。相邻flex项之间的间距，主轴起始位置到第一个flex项的间距,，主轴结束位置到最后一个flex项的间距，都完全一样。 */ -->
      <div class="container container6">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box4</div>
        <div class="box">box5</div>
      </div>
      <!-- stretch -->
      <!-- /* 均匀排列每个元素 'auto'-sized 的元素会被拉伸以适应容器的大小 */ -->
      <div class="container container7">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box box3">box3</div>
        <div class="box">box4</div>
        <div class="box box5">box5</div>
      </div>
      <!-- /* Distributed alignment */ -->

      <!-- /* Overflow alignment */ -->
      <!-- TODO: 这个地方有点迷糊 什么是safe 什么是unsafe 傻傻分不清楚 -->
      <div class="container container8">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box4</div>
        <div class="box box5">box5</div>
      </div>
      <div class="container container9">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box4</div>
        <div class="box box5">box5</div>
      </div>
      <!-- /* Overflow alignment */ -->

      <!-- TODO: 看不太出来效果的 -->
      <div class="container container10">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box4</div>
        <div class="box box5">box5</div>
      </div>
      <div class="container container11">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box4</div>
        <div class="box box5">box5</div>
      </div>
      <div class="container container12">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box4</div>
        <div class="box box5">box5</div>
      </div>
      <div class="container container13">
        <div class="box">box1</div>
        <div class="box">box2</div>
        <div class="box">box3</div>
        <div class="box">box4</div>
        <div class="box box5">box5</div>
      </div>
    </div>
  </body>
</html>
```

> css

```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.container {
  position: relative;
  width: 100%;
  margin: 50px auto 0;
  display: flex;
  flex-wrap: nowrap;
  border: 1px solid red;
}

.container::before {
  position: absolute;
  left: 0;
  top: 0;
  margin-top: -20px;
  width: 100%;
  text-align: center;
  height: 10px;
  line-height: 10px;
}

.container > .box {
  width: 120px;
  text-align: center;
  height: 120px;
  line-height: 120px;
  text-align: center;
  border: 1px solid green;
}

.container1 {
  justify-content: center;
}

.container1::before {
  content: "container1 center";
}

.container2 {
  justify-content: flex-start;
}

.container2::before {
  content: "container2 flex-start";
}

.container3 {
  justify-content: flex-end;
}

.container3::before {
  content: "container3 flex-end";
}

.container4 {
  justify-content: space-around;
}

.container4::before {
  content: "container4 space-around";
}

.container5 {
  justify-content: space-between;
}

.container5::before {
  content: "container5 space-between";
}

.container6 {
  justify-content: space-evenly;
}

.container6::before {
  content: "container6 space-evenly";
}

.container7 {
  justify-content: stretch;
}

.container7::before {
  content: "container7 stretch";
}

.container7 > .box5 {
  flex: 1 1 auto;
}

.container7 > .box3 {
  flex: 1 1 auto;
}

.container8 {
  justify-content: safe center;
}

.container8::before {
  content: "container8 safe center";
}

.container8 > .box5 {
  width: 200px;
}

.container9 {
  justify-content: unsafe center;
}

.container9::before {
  content: "container9 unsafe center";
}

.container9 > .box5 {
  width: 200px;
}

.container10 {
  justify-content: start;
}

.container10::before {
  content: "container10 start";
}

.container11 {
  justify-content: end;
}

.container11::before {
  content: "container11 end";
}

.container12 {
  justify-content: left;
}

.container12::before {
  content: "container12 left";
}

.container13 {
  justify-content: right;
}

.container13::before {
  content: "container13 right";
}
```

## 参考

- [MDN justify-content](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content)
- [Why doesn't justify-content: stretch work?](https://stackoverflow.com/questions/52106717/why-doesnt-justify-content-stretch-work/52106726)
