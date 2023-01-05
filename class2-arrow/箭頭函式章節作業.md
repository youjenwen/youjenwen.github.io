# 箭頭函式章節作業

### 第 1 題

```javascript
var person = {
  // 提款記錄
  withdrawalRecord: [12, 45, 560, 120],
  // 計算扣除的金額
  calculate: () => {
    var total = this.total
    var sum = this.withdrawalRecord.reduce(function(acc, val) {
      return acc + val
    }, 0);
    total = total - sum;
    this.total = total;
  },
  // 剩餘的金額
  total: 1000
}
person.calculate();
console.log(person.total);
// 問題：
// 1. 哪邊出錯了，請嘗試說明
// 2. 修正錯誤，並嘗試縮寫以上程式碼
```
1. `person.calculate` 使用的是箭頭函式
2. this 並不會指向 person 而是 window 只有console.log(person.total) -> 1000
3. 改成`calculate: function(){......}`
4. `var` 改成 `const or let `
```javascript
const person = {
    // 提款記錄
    withdrawalRecord: [12, 45, 560, 120],
    // 計算扣除的金額
    calculate: function () {
      let total = this.total;
      let sum = this.withdrawalRecord.reduce((acc, val) => {
        return acc + val;
      }, 0);
      total = total - sum;
      this.total = total;
    },
    // 剩餘的金額
    total: 1000,
};
person.calculate();
console.log(person.total); //263
```

### 第 2 題
```javascript
Array.prototype.sumData = () => {
    return this.reduce(function (acc, val) {
        return acc + val
    }, 0);
}
var arr = [1, 23, 5, 8, 52, 53, 63];
console.log(arr.sumData());
// 問題：
// 1. 哪邊出錯了，請嘗試說明
// 2. 修正錯誤，並嘗試縮寫以上程式碼
```
1. 可以使用箭頭函式新增陣列方法，可是裡面使用的this卻是指向全域 不是Array 所以無法使用reduce這個方法
2. var 改成 let, 使用箭頭函式
```javascript
Array.prototype.sumData = function(){
    return this.reduce((acc, val) => {
      return acc + val;
    }, 0);
};
let arr = [1, 23, 5, 8, 52, 53, 63];
console.log(arr.sumData());
```