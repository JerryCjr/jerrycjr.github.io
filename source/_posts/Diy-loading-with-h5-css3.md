---
title: Diy loading with h5 + css3
date: 2019-07-07 20:06:47
tags: 
  - CSS
  - HTML
categories: Web
---

> html

```html
  <div id='j_page-loading' class='m-actloading' style='background-color:rgba(4, 18, 34, 1)'>
    <div class='loading' style='color:rgba(255, 255, 255, 1)'>
      <div class='bars'>
          <span class='loading-bar b1' style='background-color:rgba(255, 255, 255, 1)'></span>
          <span class='loading-bar b2' style='background-color:rgba(255, 255, 255, 1)'></span>
          <span class='loading-bar b3' style='background-color:rgba(255, 255, 255, 1)'></span>
          <span class='loading-bar b4' style='background-color:rgba(255, 255, 255, 1)'></span>
          <span class='loading-bar b5' style='background-color:rgba(255, 255, 255, 1)'></span>
          <span class='loading-bar b6' style='background-color:rgba(255, 255, 255, 1)'></span>
          <span class='loading-bar b7' style='background-color:rgba(255, 255, 255, 1)'></span>
      </div>
      <span class='loading-tip'>loading<i class='dots d1'>.</i><i class='dots d2'>.</i><i class='dots d3'>.</i></span>
    </div>
  </div>
```

> css

```css
  /* loading */
  .m-actloading {
    position: fixed;
    z-index: 10000;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: hsla(0, 0%, 86%, .95);
    font-size: 16px;
    font-weight: 700;
    color: #d43c33;
    touch-action: none;
    -webkit-transition: all .6s ease-in;
    transition: all .6s ease-in;
    display: block;
  }

  .m-actloading .loading {
    position: absolute;
    top: 45%;
    left: 50%;
    margin-left: -22px;
    height: 28px;
    font-size: 0;
    text-align: center;
    white-space: nowrap
  }

  .m-actloading .loading .bars {
    width: 100%;
    height: 100%;
    overflow: hidden
  }

  .m-actloading .loading .loading-bar {
    display: inline-block;
    width: 2px;
    height: 100%;
    background-color: #d43c33;
    border-radius: 2px;
    -webkit-animation-name: loadingUpanddown;
    animation-name: loadingUpanddown;
    -webkit-animation-duration: .3s;
    animation-duration: .3s;
    -webkit-animation-timing-function: linear;
    animation-timing-function: linear;
    -webkit-animation-iteration-count: infinite;
    animation-iteration-count: infinite;
    -webkit-animation-direction: alternate;
    animation-direction: alternate;
    margin-right: 5px
  }

  .m-actloading .loading .loading-bar:last-child {
    margin-right: 0
  }

  .m-actloading .loading .loading-bar.b1 {
    -webkit-animation-delay: -.1s;
    animation-delay: -.1s
  }

  .m-actloading .loading .loading-bar.b2 {
    -webkit-animation-delay: -.2s;
    animation-delay: -.2s
  }

  .m-actloading .loading .loading-bar.b3 {
    -webkit-animation-delay: -.3s;
    animation-delay: -.3s
  }

  .m-actloading .loading .loading-bar.b4 {
    -webkit-animation-delay: -.4s;
    animation-delay: -.4s
  }

  .m-actloading .loading .loading-bar.b5 {
    -webkit-animation-delay: -.5s;
    animation-delay: -.5s
  }

  .m-actloading .loading .loading-bar.b6 {
    -webkit-animation-delay: -.6s;
    animation-delay: -.6s
  }

  .m-actloading .loading .loading-bar.b7 {
    -webkit-animation-delay: -.7s;
    animation-delay: -.7s
  }

  .m-actloading .loading .loading-tip {
    position: absolute;
    top: 41px;
    left: 50%;
    margin-left: -50%;
    font-size: 12px;
    opacity: .8
  }

  .m-actloading .loading .loading-tip .dots {
    -webkit-animation: 1s ease 0s infinite alternate loadingDots;
    animation: 1s ease 0s infinite alternate loadingDots
  }

  .m-actloading .loading .loading-tip .dots.d2 {
    -webkit-animation: 1s ease -.1s infinite alternate loadingDots;
    animation: 1s ease -.1s infinite alternate loadingDots
  }

  .m-actloading .loading .loading-tip .dots.d3 {
    -webkit-animation: 1s ease -.2s infinite alternate loadingDots;
    animation: 1s ease -.2s infinite alternate loadingDots
  }

  @-webkit-keyframes loadingUpanddown {
    to {
      -webkit-transform: translateY(100%);
      transform: translateY(100%)
    }
  }

  @keyframes loadingUpanddown {
    to {
      -webkit-transform: translateY(100%);
      transform: translateY(100%)
    }
  }

  @-webkit-keyframes loadingDots {
    to {
      opacity: 0
    }
  }

  @keyframes loadingDots {
    to {
      opacity: 0
    }
  }
```
