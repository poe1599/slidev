---
layout: section
class: 'bg-yellow-100'
---

# CSS

---
title: CSS 權重排列
level: 2
layout: center
---

* !important
* \*
* ID
* inline style
* Element
* Class

<style>
  ul {
    font-size: 32px;
  }
</style>

<!-- 
## ⭐Q：請依照 CSS 權重(由高到低)對上述內容依序進行排列。

✅ Ans：  
!important > inline style 內聯樣式 > ID ID選擇器 > Class 類別選擇器 > Element 元素選擇器 > * 通用選擇器

👍 增加 `attribute`(屬性選擇器 `span[title="test"]` )，`pseudo-class`(偽類`:hover`) 後的排序為何？  
Ans：  
`!important` > `inline style` > `ID` > `Class` = `psuedo-class` 偽類 = `attribute` 屬性選擇器 > `Element` > `*`
-->

---
title: \:first-child 選擇器
level: 2
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

```html {*|16-18}
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
## ⭐⭐Q：該 HTML 結構與 SCSS 1 搭配後將產生如上圖的五個灰色小方塊。請問如果將 SCSS 1 的部分改寫為 SCSS 2 後將會得到什麼效果？

✅ Ans：不會變色。

👍 如何讓 **`<span>2</span>`** 變色？  
Ans：  
改使用 `span:nth-child(2)` 或 `span:first-of-type`。

👍 `:first-child` 與 `:first-of-type` 的差異為何？  
Ans：  
第一種只適用於子層元素皆相同的情況。當子層元素混雜時第一種會失效，僅能使用第二種來對所指定的同一種元素進行選取。
-->
 
---
title: 垂直水平置中
level: 2
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
## ⭐Q：請舉出至少二種 CSS 實現垂直水平置中的方法。

✅ Ans：  
1. 使用Flexbox。 
2. 使用絕對定位和 transform。


👍 還有其他方式嗎？  
答：  
1. **使用`text-align`和`line-height`實現行內元素的垂直置中。**
        
```html
<div class="container">
  <span class="centered-text">Your text goes here</span>
</div>
```

```css
.container {
  text-align: center;
  height: 100vh; /* 使容器占滿整個視窗高度 */
  line-height: 100vh; /* 將行高設置為視窗高度，實現垂直置中 */
}

.centered-text {
  /* 其他樣式，例如顏色、字體大小等 */
}
```
        
1. **使用Grid布局：**
    
```html
<div class="container">
  <div class="centered-box">
    \<!-- Your content goes here --\>
  </div>
</div>
```

```css
.container {
  display: grid;
  place-items: center;
  height: 100vh; /* 使容器占滿整個視窗高度 */
}

.centered-box {
  /* 其他樣式，例如寬度、邊框等 */
}
```
  
👍 還有其他方式嗎？  
答：**使用`text-align`和`line-height`實現行內元素的垂直置中。**
-->

---
title: 百分比參考對象
level: 2
layout: two-cols
---

<div class="mr-32px h-full flex items-center">
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

<div class="mb-16px"></div>

```scss {*|11-13}
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
## ⭐⭐Q：該 HTML 結構與 SCSS 搭配後即可達到將 .box__item 垂直水平置中於 .box 的效果。請問出現在該樣式中的 4 個百分比分別是相對於誰？(題意舉例：top 50% 所表示的百分之 50 是以誰作為 100% 當作參考)

✅ Ans：  
top 與 left 以父層為 100% 做為參考，transform: translate 則以自身 dom 元素作為參考。
-->

---
title: CSS margin collapsing
level: 2
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
## ⭐⭐Q：該 HTML 結構與 SCSS 搭配後呈現的效果為何？

✅ Ans：B。

「Margin 塌陷」（Margin Collapse）是指在網頁排版中，當兩個垂直相鄰的元素具有邊距（margin）時，它們的邊距不是簡單地相加，而是以較大的邊距值為主，較小的邊距值被忽略。這導致元素之間的垂直間距（margin）可能比您預期的要小。
    
Margin 塌陷發生的條件主要包括：
    
1. 父子元素之間：當子元素的上邊距（margin-top）和父元素的上邊距（margin-top）相遇時，邊距塌陷會導致父元素的上邊距取子元素和父元素中較大的邊距值。
2. 兄弟元素之間：當相鄰的兄弟元素的上邊距和下邊距相遇時，邊距塌陷會導致它們之間的邊距取兩個兄弟元素中較大的邊距值。

👍 解決方式如下：

- 將一個或多個元素的邊距值設置為0。
- 使用**`padding`**屬性代替**`margin`**。
- 將元素設置為**`float`**或**`inline-block`**。
- 使用**`overflow: hidden;`**等技巧。
-->

---
title: button display & pseudo-element
level: 2
layout: two-cols
---

```html
<div>
  <button class="Q-button">Q-button</button>
</div>
```

<div class="mb-16px"></div>

```css
.Q-button {
  position: relative;
  display: inline;
  width: 100px;
  height: 50px;
  background: lightblue;
  border: none;
}

.Q-button::before {
  position: absolute;
  top: 0;
  left: 0;
  border-style: solid;
  border-width: 25px 25px 0 0;
  border-color: tomato transparent transparent transparent;   
}
```

::right::

<div class="h-full ml-32px grid cols-2 gap-16px">
  <div class="option">
    <b>A</b>
    <div class="A-option">
      <button class="Q-button">Q-button</button>
    </div>
  </div>
  <div class="option">
    <b>B</b>
    <div class="B-option">
      <span class="Q-button">Q-button</span>
    </div>
  </div>
  <div class="option">
    <b>C</b>
    <div class="C-option">
      <button class="Q-button">Q-button</button>
    </div>
  </div>
  <div class="option">
    <b>D</b>
    <div class="D-option">
      <span class="Q-button">Q-button</span>
    </div>
  </div>
</div>

<style>
  .option {
    @apply w-full;
    @apply flex items-center;
    @apply bg-gray b-rd-16px;
  }

  b {
    padding: 16px;
    font-size: 32px;
  }

  .Q-button {
    position: relative;
    display: inline;
    width: 100px;
    height: 50px;
    background: lightblue;
    border: none;
  }

  .Q-button::before {
    position: absolute;
    top: 0;
    left: 0;
    border-style: solid;
    border-width: 25px 25px 0 0;
    border-color: tomato transparent transparent transparent; 
  }
  
  .A-option,
  .B-option {
    .Q-button::before {
      content: '';
    }
  }
</style>

<!-- 
## ⭐⭐⭐Q：該 HTML 結構與 CSS 搭配後呈現的效果為何？

✅ Ans：C。

* inline 元素設置寬高是無效的，但 button 元素即便設置為 display: inline ，還是會被瀏覽器視為 inline-block，故設置寬高為有效。
* 偽元素必須設置 content 才能顯示。
-->