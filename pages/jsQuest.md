---
layout: section
class: 'bg-lime-200'
---

# Javascript

---
title: this
level: 2
layout: center
---

```js {*|2|3-7|5,10|*}
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
## ⭐⭐Q：請說明該程式的console執行結果為何？

✅ Ans：`undefined`。

原因是在 fn 函數中，setTimeout 函數是使用普通函數的方式定義的，並且沒有指定 this 的值。因此，在 setTimeout 函數內部，this 會指向全局對象（在瀏覽器中是 window 對象，在 Node.js中是 global 對象），而不是 obj 對象。因為全局對象中沒有 color 屬性，所以會打印 undefined。

👍 如何將上方的將 `this` 成功指向 `obj` 使其輸出 `'red'` ？
Ans：  

1. 將匿名函式改為箭頭函式。
    
    普通函數會在調用時動態決定 this 值，這個 this 值會根據函數的調用方式和上下文決定。在 setTimeout 中，因為它是在全局環境中被調用，所以 this 值會指向全局對象。而在嚴格模式下，this 會是 undefined。
    箭頭函數則不同，它的 this 值是在定義時決定的，會繼承其所在上下文的 this 值。在 setTimeout 中，箭頭函數被定義在 fn 函數中，所以它會繼承 fn 函數中的 this 值，也就是 obj 對象，因此可以訪問到 color 屬性的值。
    簡而言之，使用普通函數定義的 setTimeout 函數中的 this 值會指向全局對象，而使用箭頭函數定義的 setTimeout 函數中的 this 值會繼承外層上下文的 this 值。這就是為什麼在這個例子中，普通函數和箭頭函數的表現會有如此大的差異。
    
    ```jsx
    const obj = {
      color: 'red',
      fn() {
        setTimeout(() => {
          console.log(this.color);
        });
      }
    }
    
    obj.fn();
    ```
    
2. **在 `setTimeout` 中使用 `.bind()`：**
    
    使用 **`bind()`** 將 **`this`** 綁定到 **`obj`** 上。
    
    ```jsx
    const obj = {
      color: 'red',
      fn() {
        setTimeout(function() {
          console.log(this.color);
        }.bind(this));
      }
    }
    
    obj.fn();
    ```
-->

---
title: var Hoisting
level: 2
layout: center
---

```js {*|2,6|*}
function foo() {
  console.log(browser)
  var browser = 'Chrome'
}

foo()
```

<!-- 
## ⭐Q：請說明該程式的console執行結果為何？

✅ Ans：`undefined`。
原因為在這個程式中，由於JavaScript的提升（hoisting）特性，**`var browser`** 的聲明會被提升到函數的頂部，但賦值部分並不會。這意味著在 **`console.log(browser)`** 被執行的時候**`browser`** 雖然已經聲明了，但還沒有賦值。

👍 改成`const`後執行結果為何？  
Ans：  
`Uncaught ReferenceError: Cannot access 'browser' before initialization` ，因為 `console.log` 位於暫時性死區(TDZ)。注意! const 和 let 是會有提升(hoist)的作用。

```jsx
function foo() {
	console.log(browser)
	const browser = 'Chrome'
}

foo()
```

> let 與 const 也有 hoisting。但他們不會初始化為 undefined，而且在賦值之前試圖取值會發生錯誤（TDZ error）。
> 
> 1. 使用 var 宣告，在這時候還沒有賦值，我們可以給他一個 undefined（initialize as undefined）。
> 2. 使用 let（const） 宣告，在你 Execution 階段以前，任何人都不能碰它(don't initialize it)，讓他保持 uninitialized (尚未初始化) .
> - 如果一個值被標註是 `uninitialized` (尚未初始化) ，你還是嘗試接觸它，那就會有一個錯誤： TDZ (temporal dead zone)
> 
> ![](/assets/imgs/TDZ.png)
> 
> 學術上，真正開發語言上的原因：1. 其實和 let 沒有任何關係 2. `TDZ error 是為了實作 const`
> 
> 你使用一個 const 在 block scope 內部，如果這時候沒有限制它不能初始化 undefined，你在真正 const 賦予值以前，你可以 console.log 它，他會是 undefined （就像 var 的 hoisting）
> 
> 這就`違背了 const 在學術上（Academically）的想法`， const 只能有一個值。所以為了避免這個問題，所有在真正 assign 以前的接觸都直接給 Error，以保護 const 的學術性。
> 
-->

---
title: 浮點數精度
level: 2
layout: center
---

```js
const num1 = 0.1
const num2 = 0.2

console.log(num1 + num2 === 0.3)
```

<!-- 
## ⭐⭐Q：請說明該程式的console執行結果為何？

✅ Ans： `false`。  
在 JavaScript 中，浮點數運算可能會導致精確度丟失。這是因為 JavaScript 使用的是雙精度浮點數表示法，並且 0.1 和 0.2 都無法準確地表示為有限的二進制小數。

    👍 如何避免 JS 浮點數溢位造成的精度問題？  
    Ans：
    
    1. **使用整數進行運算：** 將浮點數轉換為整數，進行運算，然後再轉回浮點數。
        
        ```jsx
        const num1 = 0.1;
        const num2 = 0.2;
        
        const result = (num1 * 10 + num2 * 10) / 10;
        console.log(result);  // 正確的 0.3
        ```
        
    2. **使用專門的數學庫：** 使用第三方的數學庫，如 BigNumber.js 或 Math.js，這些庫提供了更高精度的數學運算。
        
        ```jsx
        const BigNumber = require('bignumber.js');
        
        const num1 = new BigNumber('0.1');
        const num2 = new BigNumber('0.2');
        
        const result = num1.plus(num2);
        console.log(result.toString());  // 正確的 0.3
        ```
        
    3. **將浮點數轉換為整數進行比較：** 如果僅需比較大小，可以將浮點數轉換為整數進行比較，以避免浮點數精度問題。
        
        ```jsx
        const num1 = 0.1;
        const num2 = 0.2;
        
        const compareResult = Math.round((num1 + num2) * 1e12) === Math.round(0.3 * 1e12);
        console.log(compareResult);  // true
        ```
        
    4. **使用 `toFixed` 方法：** 將浮點數轉換為字串，然後使用 **`toFixed`** 方法控制小數點位數。
        
        ```jsx
        const num1 = 0.1;
        const num2 = 0.2;
        
        const result = (num1 + num2).toFixed(1);
        console.log(result);  // 正確的 "0.3"
        ```
        

    JavaScript 使用的是 IEEE 754 雙精度浮點數表示法（Double-precision floating-point format），這種表示法遵從 IEEE 754 標準，將浮點數表示為二進制數。
    
    在雙精度浮點數中，一個數字佔用 64 位，分為三個部分：
    
    5. **符號位（Sign bit）：** 1 位，用於表示正數（0）或負數（1）。
    6. **指數位（Exponent）：** 11 位，用於表示指數部分，確定數字的指數範圍。
    7. **尾數（Fraction）：** 52 位，用於表示數字的有效位數。
    
    JavaScript 中的 **`Number`** 類型就是使用這種雙精度浮點數表示法。然而，由於浮點數的有限二進制表示，某些十進制小數無法精確轉換為二進制，導致精確度丟失。這就是為什麼在 JavaScript 中進行一些浮點數運算時，可能會得到不精確的結果的原因。
    
    例如，0.1 和 0.2 這兩個數字在二進制中是無窮循環的小數，因此無法完全精確地表示。當這樣的數字參與運算時，可能會產生累積的精確度損失。
    
    ```jsx
    const num1 = 0.1;  // 二進制表示為 0.00011001100110011001100110011001100110011001100110011...
    const num2 = 0.2;  // 二進制表示為 0.0011001100110011001100110011001100110011001100110011...
    
    console.log(num1 + num2);  // 結果為 0.30000000000000004
    ```
-->

---
title: Throttle vs Debounce
level: 2
layout: center
---

## **Throttle vs Debounce**

<!-- 
## ⭐⭐⭐Q：請說明函數防抖 (debounce) 和函數節流 (throttle) 分別是什麼？

✅ Ans：
* 函數防抖是指當一個事件持續觸發時，延遲一段時間後才執行相應的處理函數。如果在這段時間內事件再次觸發，則重新計時，不執行處理函數。這可以防止在短時間內頻繁觸發的事件引起過多的處理操作。 簡而言之，函數防抖的目的是確保一段時間內只執行一次函數。
* 函數節流是指在一定時間內，不管事件觸發的次數有多少，只執行一次處理函數。不像函數防抖那樣等待一段時間再執行，函數節流在每個指定的時間間隔內確保最多執行一次。

    👍 請問它們的用途分別為何？  
    Ans：
    
    1. **函數防抖的用途：**
        - 處理頻繁觸發的事件，如窗口大小變化、輸入框輸入等，以減少過多的處理操作。
        - 實現實時搜索功能，當用戶輸入搜索關鍵字時，延遲一段時間再發送請求，以減少請求的次數。
    2. **函數節流的用途：**
        - 控制事件的觸發頻率，例如在拖動事件中，只在一定的時間間隔內更新相應的操作。
        - 防止過於頻繁的 API 請求，以減輕伺服器的負擔
-->

---
title: By Reference
level: 2
layout: center
---

```js {*|4,7-8|*}
const foo = { bar: 1 }
const fn = obj => {
  obj.bar = 2
  console.log(obj.bar)         
}

fn(foo)
console.log(foo)
```

<!-- 
## ⭐⭐⭐Q：請說明該程式的console執行結果為何？


✅ Ans：fn(foo) 結果為 `2`，console.log(foo) 結果為 `{bar: 2}`。

    👍 在函式本體直接修改對參數的參考會得到什麼？  

    Ans：`2`、`{bar: 1}`。
    
    當參數為基本資料型態時，函式本體內複製了一份參數值，任何操作都不會影響原參數的實際值。參數為參考類型時，在函式本體內修改參數值的某個屬性值時，將對原來的參數進行修改。另外當參數為參考類型時，如果直接修改這個值的參考位置，則相當於在函數時體內新建了一個參考，任何操作都不會影響原參數。

    ```jsx
    let foo = {bar: 1}
    const func = obj => {
    	obj = 2
    	console.log(obj)
    }
    
    func(foo)
    console.log(foo)
    ```
-->

---
title: 相等比較
level: 2
layout: center
---

## **== vs ===**

<!-- 
## ⭐Q：請說明在 JS 中 == 和 === 有何差異？

✅ Ans：  
兩個等於（==）會對被判別的變數做轉換型別的動作（coercion又稱為implicit type conversion）。 對於 string、number 等基礎型別而言，不同型別間比較，== 會轉化成同一型別後的 "值" 是否相等。=== 時如果型別不同，其結果就是不相等。同型別比較，直接進行 "值" 比較。
-->

---
title: By Reference & Equality Comparisons & shadow copy
level: 2
layout: center
---

```js {*|1-4|6-9|*}
const a = [[1], [2], [3]]
const b = [[1], [2], [3]]
const c = a
const d = [...c]

console.log(a === b)
console.log(a === c)
console.log(a === d)
console.log(a[0] === d[0])
```

<!-- 
## ⭐⭐⭐Q：請說明該程式的console執行結果為何？


✅ Ans：
- console.log(a === b) // false
- console.log(a === c) // true
- console.log(a === d) // false
- console.log(a[0] === d[0]) // true

對於 Array Object 等高級型別而言，物件或陣列比較的是參考 reference。  
基礎型別與高級型別比較時，== 將高級型別轉化為基礎型別，進行 "值" 比較，===則因為型別不同結果為 `false`。
-->

---
title: refactor
level: 2
layout: center
---

```js
function foo(fruit, quantity) {
  // 判定一：fruit 必須有值
  if (fruit) {
    
    // 判定二：fruit 必須是紅色的
    if (fruit === 'apple' || fruit === 'strawberry' || fruit === 'cherry' || fruit === 'cranberries') {
      console.log('red fruit')

      // 判定三：quantity 數量必須大於 10
      if (quantity > 10) {
        console.log('big quantity')
      }
    }
  } else {
    throw new Error('No fruit!')
  }
}
```

<!-- 
## ⭐⭐Q：針對 coding style 如何改善巢狀條件語句與多重條件？


✅ Ans：
1. 使用 return 盡早回傳來減少巢狀條件語句的層數。
2. 使用 includes 來處理多重條件。
-->

---
title: Asynchronous Character Printing
level: 2
layout: center
---

```js
let fruit = ''
const fruits = ['Apple','Orange','Banana']

const waitPrint = () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log(fruit)
      resolve(fruit)
    }, 0)
  })
}

fruits.forEach(async (n) => {
  fruit = n
  await waitPrint()
})
```

<!-- 
## ⭐⭐⭐Q：請問以上這段程式碼最後的執行結果為何？


✅ Ans：打印出3個"Banana"

這個題目涉及了幾個重要的概念：

* 非同步處理（Asynchronous Processing）：JavaScript 是一種單線程的語言，當執行一段程式碼時，會逐行執行。但是，當需要處理一些需要時間的操作（例如網路請求、檔案讀取等），單純的同步處理方式會造成程式阻塞，因此使用非同步處理可以讓程式在等待時間內執行其他任務，待操作完成後再回來處理結果。
* Promise：Promise 是一個表示非同步操作完成或失敗的物件。它代表了一個值（通常是未來會發生的事件），讓我們可以將程式的行為包裝成一個 Promise 物件，並且可以透過 .then() 和 .catch() 方法來處理操作完成或失敗後的結果。
* async/await：async 函式是用來定義一個返回 Promise 物件的函式，而 await 運算子用來等待一個 Promise 物件解析，並返回解析後的值。async/await 讓非同步程式碼看起來更像同步程式碼，讓開發者更容易理解和編寫。

這個題目中，通過使用 setTimeout 模擬一個非同步操作，在每次迴圈中，將字串 text 分割為單個字元後，使用 async/await 來等待 waitPrint 函式的執行結果。然而，由於 forEach 方法不會等待 await 的 Promise 解析，導致 waitPrint 函式會在所有迴圈完成後才執行，因此只會印出最後一個字元。這強調了在處理非同步操作時，對於事件順序的理解和處理的重要性。
-->
