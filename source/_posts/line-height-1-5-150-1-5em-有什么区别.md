---
title: line-height(1.5/150%/1.5em)有什么区别
date: 2020-02-06 23:28:08
tags:
  - CSS
categories: Web
---

# line-height 取值 1.5，150%，1，5em 究竟有什么区别

line-height 属性值具有继承性，即父级所设置的属性值会在子级中集成，几个属性的区别：

- 1.5（纯数字）是在子级继承后重新根据自身的字体大小重新计算行高
- 1.5em 和 150%则会在父级计算完行高值后，原封不动的作用于子级元素

## 效果图

![line-height](/images/line_height/lineheight.png)

以上三种情况 父元素的字体都为 16px 子元素的字体都为 40px

> 行高为 150%

子元素的行高 = 父级的字体大小 x 150%,实际计算为 16 x 150% = 24,即子元素继承的行高为 24px.
子元素的字号为 40px, 行高为 24px, 行高小于字体大小,计算两行文字之间的距离为 2x = 24 - 40 = -16px,所以两行文字重叠在了一起

> 行高为 1.5em（也是类似的）

> 行高为 1.5

子元素的行高 = 子级自己的字体大小 x 1.5,实际计算为 40 x 1.5 = 60,即子元素继承的行高为 60px.
子元素的字号为 40px, 行高为 60px, 行高小于字体大小,计算两行文字之间的距离为 2x = 60 - 40 = 20px,所以两行文字不会重叠在一起

**因此，我们在实际使用的过程中，绝大部分场景应该尽量的少用 em 和百分比值作为 line-height 的值，而使用 1.5,2 等不带单位的值替代。**

## 源代码

> html

```html
<div class="container container1">
  <p>
    我是子级元素，我的font-size为40px，继承line-height为150%。我是子级元素，我的font-size为40px，继承line-height为150%。我是子级元素，我的font-size为40px，继承line-height为150%。
  </p>
</div>
<div class="container container2">
  <p>
    我是子级元素，我的font-size为40px，继承line-height为1.5em。我是子级元素，我的font-size为40px，继承line-height为1.5em。我是子级元素，我的font-size为40px，继承line-height为1.5em。
  </p>
</div>
<div class="container container3">
  <p>
    我是子级元素，我的font-size为40px，继承line-height为1.5。我是子级元素，我的font-size为40px，继承line-height为1.5。我是子级元素，我的font-size为40px，继承line-height为1.5。
  </p>
</div>
```

> css

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  position: relative;
  margin: 100px auto;
  width: 100vw;
  font-size: 16px;
  border: 1px solid red;
}

.container::before {
  position: absolute;
  width: 100%;
  height: 50px;
  left: 0;
  top: 0;
  margin-top: -30px;
}

.container > p {
  font-size: 40px;
}

.container1 {
  line-height: 150%;
}

.container1::before {
  content: "我是父级元素，我的font-size为40px，继承line-height为150%";
}

.container2 {
  line-height: 1.5em;
}

.container2::before {
  content: "我是父级元素，我的font-size为40px，继承line-height为1.5em";
}

.container3 {
  line-height: 1.5;
}

.container3::before {
  content: "我是父级元素，我的font-size为40px，继承line-height为1.5";
}
```

### em 的几个需要注意的地方

- em 的值并不是固定的；

- em 会继承父级元素的字体大小（参考物是父元素的 font-size；）

* em 中所有的字体都是相对于父元素的大小决定的；所以如果一个设置了 font-size:1.2em 的元素在另一个设置了 font-size:1.2em 的元素里，而这个元素又在另一个设置了 font-size:1.2em 的元素里，那么最后计算的结果是 1.2X1.2X1.2=1.728em

### 参考

- [css 中 px em rem 的区别](https://zhuanlan.zhihu.com/p/28915418)
- [彻底搞定 vertical-align 垂直居中不起作用疑难杂症](https://juejin.im/post/5a7d6b886fb9a06349129463)
