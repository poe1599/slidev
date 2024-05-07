---
layout: section
class: 'bg-yellow-100'
---

# Modern Web

---
title: cookie & web storage API
level: 2
layout: center
---

<ul class="flex flex-col gap-12px font-size-32px">
  <li>Cookie</li>
  <li>SessionStorage</li>
  <li>LocalStorage</li>
</ul>

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
title: CORS
level: 2
layout: center
---

<div class="w-80% m-auto">
  <img class="object-contain" src="/assets/imgs/cors.png" />
</div>

<!-- 
## Q：前端網頁在瀏覽器中呼叫第三方 API 時如果出現下列錯誤，請問是什麼原因造成？以及如何解決？
Ans：CORS，Access-Control-Allow-Origin white list。
-->

---
title: Cache
level: 2
layout: center
---

<div class="w-80% m-auto">
  <img class="object-contain" src="/assets/imgs/cache.png" />
</div>

<!-- 
## Q：請舉出至少一種方法防止瀏覽器對靜態資源進行快取的預設行為。
Ans：
1. 副檔名後方加上參數。
2. 設置請求標頭：Cache-Control: no-cache, no-store, must-revalidate。
3. 頁面的 HEAD 中加入 meta 標籤 <meta http-equiv="Cache-Control" content="no-cache, no-store, must-revalidate"/>。
-->

---
title: Clickjacking
level: 2
layout: center
---

## Clickjacking

<!-- 
## Q：請舉出至少一種防止 Clickjacking 的方法。
Ans：X-Frame-Options 或 Content-Security-Polic 的 frame-ancestors 
-->

---
title: CSR、SSR、SSG
level: 2
layout: center
---

<ul class="flex flex-col gap-12px font-size-32px">
  <li>Client Side Rendering (CSR)</li>
  <li>Server Side Rendering (SSR)</li>
  <li>Static Side Generation (SSG)</li>
</ul>

<!-- 
## Q：請說明何謂 Client Side Rendering (CSR)，Server Side Rendering (SSR) 和 Static Side Generation (SSG) ?
Ans：
* SSG 或是靜態生成就是 build 整個專案的時候產生 HTML 檔案，這些 HTML 檔案已經包含所需要顯示的資料。這渲染模式是預渲染 (pre-rendering) 的一種。
* SSG 很適合做內容不會有變化的靜態網站，因為所有資料是 build 時得到的。這些 HTML 檔案可以放在 CDN 上然後被 cache 而提升網站效能，除了這點之外，採用 SSG 渲染模式也利於 SEO。

-->