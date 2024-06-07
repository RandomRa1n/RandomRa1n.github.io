---
layout: post
author: Abhinav Saxena
tags: [html, 动态壁纸, css]
---
## 免责声明

我不会html和Jacascript。

~~Glory attributes to ChatGPT-4, bugs belong to me.~~

## 这是什么？

### 关于Plash

[Plash: Make any website your Mac desktop wallpaper](https://github.com/sindresorhus/Plash) 

一个将网站设为壁纸的app，仅限Mac OS。*可以显示本地网站*，可以将自定义 CSS 和 JavaScript 添加到网站。这就给了我们手搓动态壁纸的机会。

### 那么该怎么用呢？

- 下载我做的网页，或自己做一个！
- 确保“网页”至少是一个包含index.html的文件夹。
- 打开Plash，点顶部菜单的图标，点“Add Website...”，右下角有“Local Website”的选项。点开后选择你希望的网页文件夹。

## 实测截图

### Hotline Miami 2 Digital Clock

仿造Hotline Miami 2的电子钟。为了塑造发癫的效果给时间加上了晃动效果。

设计过程部分参考了Wallpaper Engine的 Hotline Miami: Clock[^1]。

位置（MIAMI, FLORIDA）可通过修改代码改变。

![HLM](http://www.abhinavsaxena.com/images/abhinav.jpeg)

### Lorentz Attractor (Rainbow)

随机生成一个固定视角的洛伦兹吸引子，并展示该洛伦兹系统的轨迹。速度越大，线段的颜色越接近彩虹的红色，反之亦然。

![Lorentz](http://www.abhinavsaxena.com/images/abhinav.jpeg)

## 需求与代码实现

### Hotline Miami 2 Digital Clock

#### Requirements

字体：
- DS-Digital，时钟字体
- PixelMix，年月日与位置的字体。无法做到游戏的完全还原，这个是我找到最接近的。

#### 代码

```html
<!DOCTYPE html>   
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Hotline Miami 2 Digital Clock</title>

<style> 
  body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: black;
    font-family: 'Courier New', monospace;
    overflow: hidden;
  }

  .container {
    text-align: center;
    animation: sway 5s ease-in-out infinite;
  }

  @keyframes sway {
  0% {
    transform: translate(-5px, -5px);
  }
  10% {
    transform: translate(5px, 5px);
  }
  20% {
    transform: translate(-5px, 5px);
  }
  30% {
    transform: translate(5px, -5px);
  }
  40% {
    transform: translate(0px, 5px);
  }
  50% {
    transform: translate(-5px, 0px);
  }
  60% {
    transform: translate(5px, 5px);
  }
  70% {
    transform: translate(-5px, -5px);
  }
  80% {
    transform: translate(5px, 0px);
  }
  90% {
    transform: translate(0px, -5px);
  }
  100% {
    transform: translate(0px, 5px); 
  }
}
.container {
  animation: sway 30s ease-in-out infinite;
}


  .clock {
    font-size: 100px;

    color: red;
    font-family: 'DS-Digital', monospace;
    margin-bottom: -15px;
    text-shadow: 2px 2px 0px darkred;
  }

  .date-location {
    color: white;
    font-family: 'pixelmix', monospace;
    font-size: 20px;
    text-shadow: 2px -2px 0px #999999;
  }
  .date-location div {
  margin-bottom: 5px; /* Adjust the bottom margin as needed */
  }

  .divider {
    position: relative; /* Needed for absolute positioning of the pseudo-element */
    height: 2px;
    background-color: white !important;
    margin: 10px auto;
    width: 200px; /* Initial size, can be adjusted */
    z-index: 2;
  }

  .divider::after {
    content: ''; /* Necessary for the pseudo-element to work */
    position: absolute; /* Position relative to the .divider */
    right: -2px; /* Shifts the grey line to the right */
    bottom: -2px; /* Shifts the grey line to the bottom */
    background-color: #999999; /* Sets the grey line color */
    width: 100%; /* Same width as the white line */
    height: 2px; /* Same height as the white line */
    z-index: 1; /* Ensures the grey line is behind the white line */
  }

  .colon {
    visibility: hidden;
  }
</style>
</head>
<body>
<div class="container">
  <div id="clock" class="clock"></div>
  <div class="divider"></div>
  <div id="date-location" class="date-location"></div>
</div>
<script>
function updateClock() {
  const locale = 'en-US'; // Define the locale
  const now = new Date();
  const hour = now.getHours().toString().padStart(2, '0');
  const minute = now.getMinutes().toString().padStart(2, '0');

  // Formatting the date as "Month abbreviation day, year"
  const dateOptions = { year: 'numeric', month: 'short', day: 'numeric' };
  let formattedDate = now.toLocaleDateString(locale, dateOptions);

  // Convert the month abbreviation to uppercase
  formattedDate = formattedDate.replace(/([a-zA-Z]+)\s(\d{1,2}),\s(\d{4})/, (match, p1, p2, p3) => {
    return `${p1.toUpperCase()} ${p2}, ${p3}`;
  });

  // Toggle colon visibility
  const colonVisibility = now.getSeconds() % 2 === 0 ? 'visible' : 'hidden';

  // Update the HTML content
  document.getElementById('clock').innerHTML = `${hour}<span class="colon" style="visibility:${colonVisibility}">:</span>${minute}`;
  document.getElementById('date-location').innerHTML = `
    <div>${formattedDate}</div>
    <div>TOKYO,  JAPAN</div> <!-- Replace with your actual location -->
  `;
}
 
setInterval(updateClock, 1000); // Update the clock every second
updateClock(); // Initialize clock immediately
 
</script>
</body>
</html>

```




Lorem ipsum[^1] dolor sit amet, consectetur adipiscing elit. Pellentesque vel lacinia neque. Praesent nulla quam, ullamcorper in sollicitudin ac, molestie sed justo. Cras aliquam, sapien id consectetur accumsan, augue magna faucibus ex, ut ultricies turpis tortor vel ante. In at rutrum tellus.

# Sample heading 1
## Sample heading 2
### Sample heading 3
#### Sample heading 4
##### Sample heading 5
###### Sample heading 6

Mauris viverra dictum ultricies. Vestibulum quis ipsum euismod, facilisis metus sed, varius ipsum. Donec scelerisque lacus libero, eu dignissim sem venenatis at. Etiam id nisl ut lorem gravida euismod.

## Lists

Unordered:

- Fusce non velit cursus ligula mattis convallis vel at metus[^2].
- Sed pharetra tellus massa, non elementum eros vulputate non.
- Suspendisse potenti.

Ordered:

1. Quisque arcu felis, laoreet vel accumsan sit amet, fermentum at nunc.
2. Sed massa quam, auctor in eros quis, porttitor tincidunt orci.
3. Nulla convallis id sapien ornare viverra.
4. Nam a est eget ligula pellentesque posuere.

## Blockquote

The following is a blockquote:

> Suspendisse tempus dolor nec risus sodales posuere. Proin dui dui, mollis a consectetur molestie, lobortis vitae tellus.

## Thematic breaks (<hr>)

Mauris viverra dictum ultricies[^3]. Vestibulum quis ipsum euismod, facilisis metus sed, varius ipsum. Donec scelerisque lacus libero, eu dignissim sem venenatis at. Etiam id nisl ut lorem gravida euismod. **You can put some text inside the horizontal rule like so.**

---
{: data-content="hr with text"}

Mauris viverra dictum ultricies. Vestibulum quis ipsum euismod, facilisis metus sed, varius ipsum. Donec scelerisque lacus libero, eu dignissim sem venenatis at. Etiam id nisl ut lorem gravida euismod. **Or you can just have an clean horizontal rule.**

---

Mauris viverra dictum ultricies. Vestibulum quis ipsum euismod, facilisis metus sed, varius ipsum. Donec scelerisque lacus libero, eu dignissim sem venenatis at. Etiam id nisl ut lorem gravida euismod. Or you can just have an clean horizontal rule.

## Code

Now some code:

```
const ultimateTruth = 'follow middlepath';
console.log(ultimateTruth);
```

And here is some `inline code`!

## Tables

Now a table:

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |



---
{: data-content="footnotes"}

[^1]: https://steamcommunity.com/sharedfiles/filedetails/?id=2445595824.
[^2]: hey there, don't forget to read all the footnotes!
[^3]: this is another footnote.
[^4]: this is a very very long footnote to test if a very very long footnote brings some problems or not; hope that there are no problems but you know sometimes problems arise from nowhere.
