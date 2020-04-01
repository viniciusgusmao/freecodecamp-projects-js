### 5. Cash Register

Design a cash register drawer function checkCashRegister() that accepts purchase price as the first argument (price), payment as the second argument (cash), and cash-in-drawer (cid) as the third argument.

cid is a 2D array listing available currency.

The checkCashRegister() function should always return an object with a status key and a change key.

Return {status: "INSUFFICIENT_FUNDS", change: []} if cash-in-drawer is less than the change due, or if you cannot return the exact change.

Return {status: "CLOSED", change: [...]} with cash-in-drawer as the value for the key change if it is equal to the change due.

Otherwise, return {status: "OPEN", change: [...]}, with the change due in coins and bills, sorted in highest to lowest order, as the value of the change key.

| Currency Unit       | Amount              |
| ------------------- | ------------------- |
| Penny               | \$0.01 (PENNY)      |
| Nickel              | \$0.05 (NICKEL)     |
| Dime                | \$0.1 (DIME)        |
| Quarter             | \$0.25 (QUARTER)    |
| Dollar              | \$1 (DOLLAR)        |
| Five Dollars        | \$5 (FIVE)          |
| Ten Dollars         | \$10 (TEN)          |
| Twenty Dollars      | \$20 (TWENTY)       |
| One-hundred Dollars | \$100 (ONE HUNDRED) |

See below for an example of a cash-in-drawer array:

```javascript
[
  ["PENNY", 1.01],
  ["NICKEL", 2.05],
  ["DIME", 3.1],
  ["QUARTER", 4.25],
  ["ONE", 90],
  ["FIVE", 55],
  ["TEN", 20],
  ["TWENTY", 60],
  ["ONE HUNDRED", 100]
];
```

Resultado:

```js
function checkCashRegister(price, cash, cid) {
  const coinsConverter = {
    0.01: "PENNY",
    0.05: "NICKEL",
    0.1: "DIME",
    0.25: "QUARTER",
    1: "DOLLAR",
    5: "FIVE",
    10: "TEN",
    20: "TWENTY"
  };
  var change = cash - price;
  let arr = Object.keys(coinsConverter)
    .filter(item => change >= item)
    .sort();
  let changes = [];
  while (arr.length > 0) {
    let ch = arr.pop();
    let rest = (change % ch).toFixed(1);
    let quo = Math.floor(change / ch);
    let tr = quo * ch;
    let arrf = cid.filter(item => {
      return item[0] == coinsConverter[ch] && item[1] >= tr;
    });
    console.log(arrf);
    if (arrf.length > 0) {
      changes.push([coinsConverter[ch], tr]);
      change = rest;
    }
  }
  let result;
  if (changes.length == 0) {
    result = { status: "INSUFFICIENT_FUNDS", change: [] };
  } else {
    result = { status: "OPEN", change: changes };
  }
  console.log(result);
  return result;
}

checkCashRegister(3.26, 100, [
  ["PENNY", 1.01],
  ["NICKEL", 2.05],
  ["DIME", 3.1],
  ["QUARTER", 4.25],
  ["ONE", 90],
  ["FIVE", 55],
  ["TEN", 20],
  ["TWENTY", 60],
  ["ONE HUNDRED", 100]
]);
```
