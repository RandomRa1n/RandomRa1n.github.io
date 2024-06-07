---
layout: post
author: Abhinav Saxena
tags: [overview, moonwalk]
---
## 免责声明

我不会HTML。
Glory attributes to ChatGPT-4, bugs belong to me.

## Screenshot

![HLM](http://www.abhinavsaxena.com/images/abhinav.jpeg)
![Lorentz](http://www.abhinavsaxena.com/images/abhinav.jpeg)

## 代码

### Hotline Miami 2 Digital Clock

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

### Lorentx Attractor


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

[^1]: this is a footnote. You should reach here if you click on the corresponding superscript number.
[^2]: hey there, don't forget to read all the footnotes!
[^3]: this is another footnote.
[^4]: this is a very very long footnote to test if a very very long footnote brings some problems or not; hope that there are no problems but you know sometimes problems arise from nowhere.
