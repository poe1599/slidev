---
layout: section
class: 'bg-lime-200'
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
## ⭐Q：請說明Cookie，sessionStorage 和 localStorage 的區別是什麼？

✅ Ans：
1. **Cookie:**
    - **存儲期限：** 可以設置過期時間，並且除非手動刪除或到期，否則在每次請求中都會被發送。
    - **大小限制：** 通常每個Cookie的大小限制為4 KB。
    - **用途：** 主要用於客戶端和服務器之間的通信，存儲會話信息、用戶首選項等。
2. **SessionStorage:**
    - **存儲期限：** 數據僅在當前會話（窗口或選項卡）有效，當瀏覽器被關閉時清除。
    - **大小限制：** 通常每個瀏覽器的SessionStorage大小限制為5 MB左右。
    - **用途：** 適合臨時數據存儲，當用戶在同一個瀏覽器窗口或選項卡中進行導航時使用。
3. **LocalStorage:**
    - **存儲期限：** 數據在瀏覽器關閉後仍然保留，直到被明確刪除。
    - **大小限制：** 通常每個瀏覽器的LocalStorage大小限制為5 MB左右。
    - **用途：** 適合長期存儲，常用於本地數據緩存，例如應用程序配置信息、用戶首選項等。

    👍 分頁問題。
        
    👍 分別會在什麼樣情況下選擇其中一種？
    答：
    
    - 如果需要在客戶端和服務器之間進行數據傳輸，並在每次HTTP請求中自動包含，則使用Cookie。
    - 如果僅在當前瀏覽器窗口或選項卡中存儲數據，可以選擇使用SessionStorage。
    - 如果需要在瀏覽器關閉後仍然保留數據，可以選擇使用LocalStorage。
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
## ⭐⭐Q：前端網頁在瀏覽器中呼叫第三方 API 時如果出現下列錯誤，請問是什麼原因造成？以及如何解決？

✅ Ans：同源政策問題。在 http header 中補上 Access-Control-Allow-Origin 設定白名單。

    👍 請說明什麼是同源政策？
    Ans：
    
    瀏覽器的同源政策（Same-Origin Policy）是一種安全機制，用於限制來自不同源（域名、協議或端口）的網頁之間的互動。具體而言，同源政策要求在執行某些操作（例如讀取數據、發送請求）時，網頁只能與它自身的來源進行交互，而不能與其他來源進行交互。
    
    同源政策的目的是保護使用者的數據安全，防止惡意網站從其他網站中獲取敏感信息。如果同源政策不存在，一個惡意網站可能會利用來自其他網站的資源和數據，對使用者造成安全風險。
    
    同源政策通常包含以下限制：
    
    1. **JavaScript的限制：** 一個網頁中的JavaScript只能訪問與該網頁相同源的內容，無法訪問其他源的數據。
    2. **Cookie和LocalStorage的限制：** Cookie和LocalStorage等本地存儲機制只能與相同源的網頁進行交互，不能被其他源的網頁訪問。
    3. **AJAX請求的限制：** 使用XMLHttpRequest或Fetch API發送的AJAX請求受到同源政策的約束，只能向相同源的網址發送請求。
    
    這些限制有助於確保在瀏覽網頁時，使用者的數據不受到來自其他不受信任源的威脅。當開發者需要進行跨源的數據交互時，可以使用跨源請求技術，例如JSONP、CORS（Cross-Origin Resource Sharing）等，以獲得必要的授權。
    
    👍 為什麼在 Postman 沒有這個問題？
    
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
## ⭐⭐Q：請舉出至少一種方法防止瀏覽器對靜態資源進行快取的預設行為。

✅ Ans：
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
## ⭐⭐⭐Q：請舉出至少一種防止 Clickjacking 的方法。

✅ Ans：

    網站可以利用設定 `X-Frame-Options` 或 `Content-Security-Polic` 的 `frame-ancestors`  來確保本身內容不會遭惡意嵌入到其他網站，避免 [clickjacking (en-US)](https://developer.mozilla.org/en-US/docs/Web/Security/Types_of_attacks) 攻擊。
    
    1. 禁止任何網站內嵌 `X-Frame-Options: DENY` 或 `Content-Security-Policy: frame-ancestors 'none';`。
    2. 限定只能被同網站內嵌(Scheme、Host、Port 都要相同) `X-Frame-Options: SAMEORIGIN` 或 `Content-Security-Policy: frame-ancestors 'self';`。
    3. 只允許特定網站內嵌 `X-Frame-Options: ALLOW-FROM uri` 只能被特定網站內嵌，但這個規格只有 IE8+ 跟 Firefox for Android 支援，只限單一 Uri。CSP 寫法的彈性很多，可以包含 `'self'`、列舉多個 Url、甚至支援萬用字元 (可用於 Host 及 Port)：`Content-Security-Policy: frame-ancestors 'self' [https://www.example.org](https://www.example.org/) [http://\*.another-web.ne](http://%2A.another-web.net/) [http://www.all-port-ok.net](http://www.all-port-ok.net/);` 但是 IE11 不支援 CSP。
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
## ⭐Q：請說明何謂 Client Side Rendering (CSR)，Server Side Rendering (SSR) 和 Static Side Generation (SSG) ?

✅ Ans：
* SSG 或是靜態生成就是 build 整個專案的時候產生 HTML 檔案，這些 HTML 檔案已經包含所需要顯示的資料。這渲染模式是預渲染 (pre-rendering) 的一種。
* SSG 很適合做內容不會有變化的靜態網站，因為所有資料是 build 時得到的。這些 HTML 檔案可以放在 CDN 上然後被 cache 而提升網站效能，除了這點之外，採用 SSG 渲染模式也利於 SEO。

-->