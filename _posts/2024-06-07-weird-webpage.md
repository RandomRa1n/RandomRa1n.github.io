---
layout: post
author: Abhinav Saxena
tags: [网页，动态壁纸, html, css]
---
## 免责声明


我不会html和Jacascript。~~Glory attributes to ChatGPT-4, bugs belong to me.~~


## 这是什么？

自制怪网页，通过Plash实现将网页设为壁纸的功能，使得mac也有动态壁纸用。

目前做了2个网页：
- Hotline Miami 2 Digital Clock
- Lorentz Attractor (Rainbow)

### 关于Plash 

[Plash: Make any website your Mac desktop wallpaper](https://github.com/sindresorhus/Plash) 

一个将网站设为壁纸的app，仅限Mac OS。*可以显示本地网站*，可以将自定义 CSS 和 JavaScript 添加到网站。这就给了我们手搓动态壁纸的机会。

### 那么该怎么用呢？

- 下载我做的网页，或自己做一个！
- 确保“网页”至少是一个包含index.html的文件夹。
- 打开Plash，点顶部菜单的图标，点“Add Website...”，右下角有“Local Website”的选项。点开后选择你希望的网页文件夹。

## 下载须知

### Hotline Miami 2 Digital Clock

#### 说明

仿造Hotline Miami 2的电子钟。为塑造发癫效果加上了晃动效果。设计过程部分参考了Wallpaper Engine的 [Hotline Miami: Clock](https://steamcommunity.com/sharedfiles/filedetails/?id=2445595824)。

位置默认 MIAMI, FLORIDA，可通过修改代码第136行改变。
```html
    <div>MIAMI,  FLORIDA</div> <!-- Replace with your actual location --> 
```

#### 需求

字体：
- DS-Digital，时钟字体
- PixelMix，年月日与位置的字体。无法做到游戏的完全还原，这个是我找到最接近的。

#### 下载与效果预览

[Download](assets/weird-webpage/HLM2_clock.zip)

![HLM](assets/weird-webpage/HLM2_clock.png)


### Lorentz Attractor (Rainbow)

#### 说明

随机生成一个固定视角的洛伦兹吸引子，并展示该洛伦兹系统的轨迹。速度越大，线段的颜色越接近彩虹的红色，反之亦然。

#### 需求

*运行时需要互联网连接*。原因是代码中引用了`three.min.js`的 CDN 链接.

如果想在没有互联网连接的情况下运行，可以下载`three.min.js`并在本地引用它:
- 下载[three.min.js](https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js)文件。
- 将下载的 `three.min.js` 文件放入与 index.html 和 app.js 相同的目录中。
- 更新 index.html 文件以引用本地的 `three.min.js` 文件, 如下所示：
  
```html
<!DOCTYPE html>
<html>
<head>
    <title>Lorentz Attractor</title>
    <style>
        body { margin: 0; }
        canvas { width: 100%; height: 100% }
    </style>
</head>
<body>
    <script src="three.min.js"></script>
    <script src="app.js"></script>
</body>
</html>
  ```


#### 下载与效果预览

[Download](assets/weird-webpage/Lorentz_Attractor_rainbow.zip)

![Lorentz](assets/weird-webpage/Lorentz_Attractor_rainbow.png)



# Sample heading 1
## Sample heading 2
### Sample heading 3
#### Sample heading 4
##### Sample heading 5
###### Sample heading 6


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


[^2]: hey there, don't forget to read all the footnotes!
[^3]: this is another footnote.
[^4]: this is a very very long footnote to test if a very very long footnote brings some problems or not; hope that there are no problems but you know sometimes problems arise from nowhere.
