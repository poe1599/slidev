---
layout: section
class: 'bg-yellow-100'
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
## Q：請說明該程式的console執行結果為何？
Ans：undefined。
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
## Q：請說明該程式的console執行結果為何？
Ans：undefined。
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
## Q：請說明該程式的console執行結果為何？
Ans：false。
-->

---
title: Throttle vs Debounce
level: 2
layout: center
---

## **Throttle vs Debounce**

<!-- 
## Q：請說明函數防抖 (debounce) 和函數節流 (throttle) 分別是什麼？
Ans：
* 函數防抖是指當一個事件持續觸發時，延遲一段時間後才執行相應的處理函數。如果在這段時間內事件再次觸發，則重新計時，不執行處理函數。這可以防止在短時間內頻繁觸發的事件引起過多的處理操作。 簡而言之，函數防抖的目的是確保一段時間內只執行一次函數。
* 函數節流是指在一定時間內，不管事件觸發的次數有多少，只執行一次處理函數。不像函數防抖那樣等待一段時間再執行，函數節流在每個指定的時間間隔內確保最多執行一次。
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
## Q：請說明該程式的console執行結果為何？
Ans：fn(foo) 結果 2，console.log(foo) 結果為 {bar: 2}。
-->

---
title: 相等比較
level: 2
layout: center
---

## **== vs ===**

<!-- 
## Q：請說明在 JS 中 == 和 === 有何差異？
Ans：兩個等於（==）會對被判別的變數做轉換型別的動作（coercion又稱為implicit type conversion）。 對於 string、number 等基礎型別而言，不同型別間比較，== 會轉化成同一型別後的 "值" 是否相等。=== 時如果型別不同，其結果就是不相等。同型別比較，直接進行 "值" 比較。
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
## Q：請說明該程式的console執行結果為何？
Ans：
- console.log(a === b) // false
- console.log(a === c) // true
- console.log(a === d) // false
- console.log(a[0] === d[0]) // true
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
## Q：針對 coding style 如何改善巢狀條件語句與多重條件？
Ans：使用 return 盡早回傳，使用 includes 處理多重條件。
-->

---
title: Asynchronous Character Printing
level: 2
layout: center
---

```js
let t = ''
const text = 'cool!'

const waitPrint = () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      console.log(t)
      resolve(t)
    }, 0)
  })
}

text.split('').forEach(async (n) => {
  t = n
  await waitPrint()
})
```

<!-- 
## Q：請問以上這段程式碼最後的執行結果為何？
Ans：打印出5個"!"

這個題目涉及了幾個重要的概念：

* 非同步處理（Asynchronous Processing）：JavaScript 是一種單線程的語言，當執行一段程式碼時，會逐行執行。但是，當需要處理一些需要時間的操作（例如網路請求、檔案讀取等），單純的同步處理方式會造成程式阻塞，因此使用非同步處理可以讓程式在等待時間內執行其他任務，待操作完成後再回來處理結果。
* Promise：Promise 是一個表示非同步操作完成或失敗的物件。它代表了一個值（通常是未來會發生的事件），讓我們可以將程式的行為包裝成一個 Promise 物件，並且可以透過 .then() 和 .catch() 方法來處理操作完成或失敗後的結果。
* async/await：async 函式是用來定義一個返回 Promise 物件的函式，而 await 運算子用來等待一個 Promise 物件解析，並返回解析後的值。async/await 讓非同步程式碼看起來更像同步程式碼，讓開發者更容易理解和編寫。

這個題目中，通過使用 setTimeout 模擬一個非同步操作，在每次迴圈中，將字串 text 分割為單個字元後，使用 async/await 來等待 waitPrint 函式的執行結果。然而，由於 forEach 方法不會等待 await 的 Promise 解析，導致 waitPrint 函式會在所有迴圈完成後才執行，因此只會印出最後一個字元。這強調了在處理非同步操作時，對於事件順序的理解和處理的重要性。
-->
