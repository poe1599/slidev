---
theme: seriph
title: 前端面試 QA
info:
class: text-center
highlighter: shiki
lineNumbers: true
drawings:
  persist: false
transition: slide-up
mdc: true
---

# 前端面試 QA

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

---
layout: section
---

# HTML

---
layout: quote
---

# \<strong> vs \<b>

<br/>

```html
<strong>This text is important!</strong>

<b>This text is important!</b>
```

<!--
## Q：在 html 標籤中 \<strong> 和 \<b> 有何差異？
Ans： 兩者都能呈現粗體文字，\<b> 標籤是一個物理標記，它所包圍的文字將被設為 bold ，僅代表著讓這個文字看起來粗粗的（ 視覺上的意義 ），而 \<strong> 標籤是一個邏輯標記，作用是加強文字語氣，表示這是很重要的文字，所以我要用一個粗體的樣式來提醒大家（ 語意上的意義 ）。
-->

---
layout: image-left
image: /assets/imgs/meme-drake.png
backgroundSize: contain
---

<div class="grid h-full row-2 items-center ml-(-24%)">

```html
<div>...</div>

<div>...</div>

<div>
  <div>...</div>
  <div>...</div>
</div>
```

```html
<header>...</header>

<nav>...</nav>

<main>
  <article>...</article>
  <section>...</section>
</main>
```

</div>

<!--
## Q：在切版時應盡量避免只使用 \<div> 標籤，而是要善用 HTML5 所提供的各種語意化標籤，如 \<header>、\<article>、\<section> 等，其原因為何？
Ans： 有了語意化標籤，搜尋引擎會更理解網頁內容，這樣搜尋結果也會更正確。更直接的說，使用正確的語意標籤，直接影響的就是搜尋結果的最佳化。
1. 可以快速抓到網頁架構和每個區塊的位置
2. 對於SEO優化有幫助
語意化標籤的另一個好處是無障礙友善，如 \<strong> 標籤，當視障者在使用螢幕閱讀器時，能夠明顯感受到 \<b> 與 \<strong> 的不同，遇到 \<b> 時與處理一般詞語一樣進行閱讀，但遇到 \<strong> 時會加重與停頓。
-->

---
layout: center
---

```html {3}
<head>
  <!-- else -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0" />
  <!-- else -->
</head>
```

<!-- 
## Q：請說明在 <meta> 標籤中設定 viewport 的用途為何？
Ans：在 \<meta> 標籤中設定 viewport 主要用於控制網頁在移動設備上的顯示方式。具體而言，透過設定 viewport，可以調整網頁在不同設備上的寬度、縮放、字型大小等屬性，以提供更好的使用者體驗。
 -->

---
layout: two-cols
---

<div class='grid h-full items-center text-center'>

# \<input>

</div>

::right::

<div class="grid rows-2 h-full ml-(-60px) p-10px b-rd-8px bg-gray-200 dark:(bg-gray-500)">
  <div>
    <p>Number: Android / iOS</p>
    <img class="w-100%" src="/assets/imgs/keyboard-number.png" />
  </div>
  <div>
    <p>Phone: Android / iOS</p>
    <img class="w-100%" src="/assets/imgs/keyboard-phone.png" />
  </div>
</div>

<!-- 
## Q：在移動裝置中點擊文字輸入框後，如何讓瀏覽器顯示不同類型的原生虛擬鍵盤？
Ans：使用 inputmode 屬性。
 -->

---
layout: center
---

# Block element vs Inline element

<!-- 
## Q：請說明 CSS 中 行內元素 及 區塊元素 的差異？
Ans：
### 塊級元素（Block-level Elements）：
1. 佔據一整行： 塊級元素通常會佔據一整行，從新的一行開始，直到佔滿其父元素的寬度。
2. 自動換行： 塊級元素會自動換行，即在該元素後的內容會顯示在新的一行。
3. 高度、寬度和外邊距（margin）以及內邊距（padding）都是可以控制的。
4. 例如：\<div>、\<p>、\<h1>~\<h6>、\<ul>、\<li> 等。
### 行內元素（Inline Elements）：
1. 僅佔據其內容的空間： 行內元素僅佔據其內容所需的空間，不會強制換行。
2. 不強制換行： 行內元素不會強制換行，多個行內元素可以在同一行上顯示。
3. 高度、寬度、外邊距和內邊距的上、下方向上的設置是無效的。
4. 例如：\<span>、\<a>、\<strong>、\<em>、\<img> 等。
 -->

---
layout: section
---

# CSS

---
layout: center
---

* !important
* \*
* ID
* inline style
* Element
* Class

<!-- 
## Q：請依照 CSS 權重(由高到低)對上述內容依序進行排列。
Ans：!important > inline style 內聯樣式 > ID ID選擇器 > Class 類別選擇器 > Element 元素選擇器 > * 通用選擇器
 -->

---
layout: two-cols
---

<div class="box mt-64px">
  <div>1</div>
  <span>2</span>
  <div>3</div>
  <span>4</span>
  <div>5</div>
</div>

<div class="w-92% mt-32px">
```html
<div class="box">
  <div>1</div>
  <span>2</span>
  <div>3</div>
  <span>4</span>
  <div>5</div>
</div>
```
</div>

<style>
  .box {
    display: flex;
    gap: 16px;
    border: 1px solid #f00;
    padding: 16px;
    max-width: 300px;

    span, div {
      width: 20px;
      height: 20px;
      display: inline-block;
      background-color: #ccc;
    }
  }
</style>

::right::

<div class="mt-64px"></div>

````md magic-move
```html
<style>
  .box {
    display: flex;
    gap: 16px;
    border: 1px solid red;
    padding: 16px;
    max-width: 300px;

    span, div {
      width: 20px;
      height: 20px;
      display: inline-block;
      background-color: gray;
    }
  }
</style>
```

```html{*|16-18}
<style>
  .box {
    display: flex;
    gap: 16px;
    border: 1px solid red;
    padding: 16px;
    max-width: 300px;  

    span, div {
      width: 20px;
      height: 20px;
      display: inline-block;
      background-color: gray;
    }

    span:first-child {
      background-color: red;
    }
  }
</style>
```
````

<!-- 
## Q：該 HTML 結構與 SCSS 1 搭配後將產生如上圖的五個灰色小方塊。請問如果將 SCSS 1 的部分改寫為 SCSS 2 後將會得到什麼效果？
Ans：不會變色。
 -->
 
---
 layout: center
---

<div class="Box">
  <span class="text">Box</span>
  <div class="Item">
    <span class="text">Item</span>
  </div>
</div>

<style>
  .Box {
    @apply w-30vh h-30vh bg-gray-300;
    @apply b-4px b-solid b-gray-400;
    @apply relative;
  }

  .Item {
    @apply w-8vh h-8vh bg-orange-500 ;
    @apply b-4px b-solid b-orange-800;
    @apply absolute top-50% left-50%;
    transform: translate(-50%,-50%);
  }

  .text {
    @apply absolute top-0 left-0;
    @apply inline-block p-12px text-black;
  }
</style>
 
<!-- 
## Q：請舉出至少二種 CSS 實現垂直水平置中的方法。
Ans：1. 使用Flexbox。 2. 使用絕對定位和transform。
-->

---
layout: two-cols
---

<div class="mr-32px">
  <div class="wrap">
    <div class="box">
      <span class="text">Box</span>
      <div class="box__item">
        <span class="text">Item</span>
      </div>
    </div>
  </div>
</div>

<style>
  .wrap {
    @apply w-40vh h-40vh flex justify-center items-center bg-gray-200;
    @apply mb-32px;
  }
  .box {
    @apply w-80% h-80% bg-gray-300;
    @apply b-4px b-solid b-gray-400;
    @apply relative;
  }

  .box__item {
    @apply w-20% h-20% bg-orange-500 ;
    @apply b-4px b-solid b-orange-800;
    @apply absolute top-50% left-50%;
    transform: translate(-50%,-50%);
  }

  .text {
    @apply absolute top-0 left-0;
    @apply inline-block p-4px text-black;
  }
</style>

::right::

```html
<body>
  <div class="box">
    <div class="box__item"></div>
  </div>
</body>
```

<div class="mb-32px"></div>

```scss{*|11-13}
.box {
  width: 400px;
  height: 400px;
  position: relative;
  border: 1px solid gray;

  &__item {
    width: 100px;
    height: 100px;
    position: absolute;
    top: 50%;
    left: 50%
    transform: translate(-50%,-50%);
    border: 1px solid orange;
  }
}
```

<!-- 
## Q：該 HTML 結構與 SCSS 搭配後即可達到將 .box__item 垂直水平置中於 .box 的效果。請問出現在該樣式中的 4 個百分比分別是相對於誰？(題意舉例：top 50% 所表示的百分之 50 是以誰作為 100% 當作參考)
Ans：top 與 left 以父層為 100% 做為參考，transform: translate 則以自身 dom 元素作為參考。
-->

---
layout: two-cols
---
<div class="h-full">
  <div class="flex items-center justify-center h-full">
    <div class="w-50% h-full">
      <img class="w-full h-full object-contain" src="/assets/imgs/css-margin.jpg">
    </div>
    <div class="grid rows-2 font-size-3rem gap-13rem pl-32px">
      <div>A</div>
      <div>B</div>
    </div>
  </div>
</div>

::right::

<div class="grid items-center h-full">

```scss
.box {
  width: 200px;
  height: 200px;
  background-color: cornflowerblue;
  margin-left: 100px;
  margin-top: 100px;

  &__item {
    width: 100px;
    height: 100px;
    background-color: lightgreen;
    margin-left: 50px;
    margin-top: 25px;
  }
}
```

</div>

<!-- 
## Q：該 HTML 結構與 SCSS 搭配 後呈現的效果為和？
Ans：B。
-->

---
layout: section
---

# Javascript

---
layout: center
---

```js{*|2|3-7|5,10|*}
const obj = {
  color: 'red',
  fn() {
    setTimeout(function() {
      console.log(this.color)
    })
  }
}

obj.fn()
```

<!-- 
## Q：請說明該程式的console執行結果為何？
Ans：undefined。
-->

---
layout: center
---

```js{*|2,6|*}
function foo() {
  console.log(browser)
  var browser = 'Chrome'
}

foo()
```

<!-- 
## Q：請說明該程式的console執行結果為何？
Ans：undefined。
-->