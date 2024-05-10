---
layout: section
class: 'bg-yellow-100'
---

# HTML

---
title: strong 與 b 的差異
level: 2
layout: quote
---

# \<strong> vs \<b>

<br/>

```html
<strong>This text is important!</strong>

<b>This text is important!</b>
```

<!--
## ⭐Q：在 html 標籤中 \<strong> 和 \<b> 有何差異？

✅ Ans：  
兩者都能呈現粗體文字，\<b> 標籤是一個物理標記，它所包圍的文字將被設為 bold ，僅代表著讓這個文字看起來粗粗的（ 視覺上的意義 ），而 \<strong> 標籤是一個邏輯標記，作用是加強文字語氣，表示這是很重要的文字，所以我要用一個粗體的樣式來提醒大家（ 語意上的意義 ）。
-->

---
title: 語意化標籤
level: 2
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
## ⭐Q：在切版時應盡量避免只使用 \<div> 標籤，而是要善用 HTML5 所提供的各種語意化標籤，如 \<header>、\<article>、\<section> 等，其原因為何？

✅ Ans：  
有了語意化標籤，搜尋引擎會更理解網頁內容，這樣搜尋結果也會更正確。更直接的說，使用正確的語意標籤，直接影響的就是搜尋結果的最佳化。

1. 可以快速抓到網頁架構和每個區塊的位置
2. 對於 SEO 優化有幫助

語意化標籤的另一個好處是無障礙友善，如 \<strong> 標籤，當視障者在使用螢幕閱讀器時，能夠明顯感受到 \<b> 與 \<strong> 的不同，遇到 \<b> 時與處理一般詞語一樣進行閱讀，但遇到 <strong> 時會加重與停頓。
-->

---
title: meta viewport
level: 2
layout: center
---

```html {3-6}
<head>
  <!-- else -->
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0"
    />
  <!-- else -->
</head>
```

<!-- 
## ⭐⭐Q：請說明在 \<meta> 標籤中設定 viewport 的用途為何？

✅ Ans：  
在 \<meta> 標籤中設定 viewport 主要用於控制網頁在移動設備上的顯示方式。具體而言，透過設定 viewport，可以調整網頁在不同設備上的寬度、縮放、字型大小等屬性，以提供更好的使用者體驗。以下是一些重要的用途：

1. 適應不同設備的屏幕大小： 通過設定 viewport，可以使網頁在不同設備上（如手機、平板、桌面）呈現出適當的寬度，以確保內容不會過於擠壓或過於寬廣。
2. 啟用或禁用縮放： 可以通過 viewport 的屬性設定，控制用戶是否能夠縮放網頁。例如，設定 user-scalable=no 將禁止用戶手動縮放。
3. 確保字型大小可讀性： 透過 viewport 的設定，可以確保在不同設備上字型大小的適當顯示，以保證內容的可讀性。
4. 設定初始縮放級別： 可以通過 initial-scale 屬性設定網頁的初始縮放級別，以確保在載入時網頁呈現出期望的大小。
5. 支持響應式網頁設計： 適當設定 viewport 是實現响應式網頁設計的重要一環，使得網站能夠在各種設備上提供一致的使用者體驗。

👍 請問 viewport 對桌機裝置有用嗎？( 如果未回答viewport 是控制移動裝置的話 )  
Ans：  
viewport tag 的定義只對 mobile device 有用，用來控制 mobile device 顯示網頁內容時的一些設定。

💡 當在設計手機行動版網頁 (mobile web) 或響應式 (RWD, Responsive Web Design) 網頁時，我們需要用 \<meta>viewport 來指定瀏覽器怎麼渲染和縮放網頁畫面的寬高。如果沒有設定 meta viewport，移動設備會以典型的桌面設備螢幕寬度渲染頁面，然後對頁面進行縮放以適合移動設備屏幕，這時候畫面看起來就會擠在一起或內容變很小不好閱讀。通過設置 viewport (視口)，你可以控制螢幕的寬度和縮放比例。常見的 viewport 設定：`<meta name="viewport" content="width=device-width, initial-scale=1.0">` 其中：`width=device-width` 指定瀏覽器頁面的寬度同裝置 (device) 的寬度，`initial-scale=1.0` 指定畫面初始縮放比例為 100%，即不放大也不縮小。如果你想防止使用者用手指做畫面的縮放：`<meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1">` 或這樣子設定也一樣效果：`<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">` 其中：`minimum-scale=1` 設定畫面最小的縮放比例為 1， `maximum-scale=1` 設定畫面最大的縮放比例為 1，都設為 1 的意思其實就是說不能縮放。`user-scalable` 用來設定是否允許使用者改變縮放比例，`user-scalable=no` 就是不允許縮放。
    
![](/assets/imgs/viewport-table.png)
-->

---
title: input inputmode
level: 2
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
## ⭐⭐⭐Q：在移動裝置中點擊文字輸入框後，如何讓瀏覽器顯示不同類型的原生虛擬鍵盤？

✅ Ans：  
使用 inputmode 屬性。

👍 **`type`** 跟 **`inputmode`** 差在哪？  
Ans：  
type 決定 input 的類型，這會關係到瀏覽器預設欄位驗證的部分，且 type 的類型比 inputmode 多太多了（有興趣的話請參考 [whatwg](https://html.spec.whatwg.org/multipage/input.html#attr-input-type)）；而 inputmode 只有單純提供一個參考讓瀏覽器決定顯示哪個鍵盤。當然，兩個是可以一起使用的！

👍 不想要虛擬鍵盤(或想使用自己的客製化鍵盤)時，該怎麼做？  
Ans：  
`inputmode="none"`
-->

---
title: 行內元素及區塊元素的差異
level: 2
layout: center
---

# Block element vs Inline element

<!-- 
## ⭐⭐Q：請說明 CSS 中 行內元素 及 區塊元素 的差異？

✅ Ans：  
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
