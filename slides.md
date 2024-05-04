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
    @apply w-50vh h-50vh bg-gray-300;
    @apply b-4px b-solid b-gray-400;
    @apply relative;
  }

  .Item {
    @apply w-10vh h-10vh bg-orange-500 ;
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
<!-- 
## Q：該 HTML 結構與 SCSS 搭配後即可達到將 .box__item 垂直水平置中於 .box 的效果。請問出現在該樣式中的 4 個百分比分別是相對於誰？(題意舉例：top 50% 所表示的百分之 50 是以誰作為 100% 當作參考)
Ans：top 與 left 以父層為 100% 做為參考，transform: translate 則以自身 dom 元素作為參考。
-->

---
 
<!-- 
## Q：該 HTML 結構與 SCSS 搭配 後呈現的效果為和？
Ans：B。
-->

---
layout: section
---

# Javascript

---

<!-- 
## Q：請說明該程式的console執行結果為何？
Ans：undefined。
-->

---

<!-- 
## Q：請說明該程式的console執行結果為何？
Ans：undefined。
-->

---

<!-- 
## Q：請說明該程式的console執行結果為何？
Ans：false。
-->

---

<!-- 
## Q：請說明函數防抖 (debounce) 和函數節流 (throttle) 分別是什麼？
Ans：
* 函數防抖是指當一個事件持續觸發時，延遲一段時間後才執行相應的處理函數。如果在這段時間內事件再次觸發，則重新計時，不執行處理函數。這可以防止在短時間內頻繁觸發的事件引起過多的處理操作。 簡而言之，函數防抖的目的是確保一段時間內只執行一次函數。
* 函數節流是指在一定時間內，不管事件觸發的次數有多少，只執行一次處理函數。不像函數防抖那樣等待一段時間再執行，函數節流在每個指定的時間間隔內確保最多執行一次。
-->

---

<!-- 
## Q：請說明該程式的console執行結果為何？
Ans：fn(foo) 結果 2，console.log(foo) 結果為 {bar: 2}。
-->

---

<!-- 
## Q：請說明在 JS 中 == 和 === 有何差異？
Ans：兩個等於（==）會對被判別的變數做轉換型別的動作（coercion又稱為implicit type conversion）。 對於 string、number 等基礎型別而言，不同型別間比較，== 會轉化成同一型別後的 "值" 是否相等。=== 時如果型別不同，其結果就是不相等。同型別比較，直接進行 "值" 比較。
-->

---

<!-- 
## Q：請說明該程式的console執行結果為何？
Ans：console.log(foo === bar) 結果 flase，console.log(foo === baz)結果為 true。
-->

---

<!-- 
## Q：針對 coding style 如何改善巢狀條件語句與多重條件？
Ans：使用 return 盡早回傳，使用 includes 處理多重條件。
-->

---
layout: section
---

# Modern Web

---

<!-- 
## Q：請說明Cookie，sessionStorage 和 localStorage 的區別是什麼？
Ans：
* Cookie: 
  存儲期限： 可以設置過期時間，並且除非手動刪除或到期，否則在每次請求中都會被發送。
  大小限制： 通常每個Cookie的大小限制為4 KB。
  用途： 主要用於客戶端和服務器之間的通信，存儲會話信息、用戶首選項等。
* SessionStorage: 
  存儲期限： 數據僅在當前會話（窗口或選項卡）有效，當瀏覽器被關閉時清除。
  大小限制： 通常每個瀏覽器的SessionStorage大小限制為5 MB左右。
  用途： 適合臨時數據存儲，當用戶在同一個瀏覽器窗口或選項卡中進行導航時使用。
* LocalStorage: 
  存儲期限： 數據在瀏覽器關閉後仍然保留，直到被明確刪除。
  大小限制： 通常每個瀏覽器的LocalStorage大小限制為5 MB左右。
  用途： 適合長期存儲，常用於本地數據緩存，例如應用程序配置信息、用戶首選項等。


-->

---

<!-- 
## Q：前端網頁在瀏覽器中呼叫第三方 API 時如果出現下列錯誤，請問是什麼原因造成？以及如何解決？
Ans：CORS，Access-Control-Allow-Origin white list。
-->

---

<!-- 
## Q：請舉出至少一種方法防止瀏覽器對靜態資源進行快取的預設行為。
Ans：
1. 副檔名後方加上參數。
2. 設置請求標頭：Cache-Control: no-cache, no-store, must-revalidate。
3. 頁面的 HEAD 中加入 meta 標籤 <meta http-equiv="Cache-Control" content="no-cache, no-store, must-revalidate"/>。
-->

---

<!-- 
## Q：請舉出至少一種防止 Clickjacking 的方法。
Ans：X-Frame-Options 或 Content-Security-Polic 的 frame-ancestors 
-->

---

<!-- 
## Q：請說明何謂 Client Side Rendering (CSR)，Server Side Rendering (SSR) 和 Static Side Generation (SSG) ?
Ans：
* SSG 或是靜態生成就是 build 整個專案的時候產生 HTML 檔案，這些 HTML 檔案已經包含所需要顯示的資料。這渲染模式是預渲染 (pre-rendering) 的一種。
* SSG 很適合做內容不會有變化的靜態網站，因為所有資料是 build 時得到的。這些 HTML 檔案可以放在 CDN 上然後被 cache 而提升網站效能，除了這點之外，採用 SSG 渲染模式也利於 SEO。

-->

---
layout: section
---

# The End
