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