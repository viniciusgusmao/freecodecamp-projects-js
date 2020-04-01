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
    "PENNY": 0.01,
    "NICKEL": 0.05,
    "DIME": 0.1,
    "QUARTER": 0.25,
    "ONE": 1,
    "FIVE": 5,
    "TEN": 10,
    "TWENTY": 20,
    "ONE HUNDRED": 100 
  };
  let change = cash - price;
  let changes = [];
  let rest, value, notas;
  cid.reverse().forEach(item => {
    let valCoin = coinsConverter[item[0]];
    if (valCoin < change && item[1] > valCoin){
      if (item[1] <= change){
        rest = (change % item[1]).toFixed(2)*1;   
        value = item[1];
      } else if (item[1] > change) {
        let num = Math.floor((change/valCoin))*valCoin;
        rest = (change % num).toFixed(2)*1
        value = num;
      }
      // if (change )
      changes.push([ item[0], value ]);
      change = rest;
    }
  })
  let result;
  if (changes.length == 0) {
    result = { status: "INSUFFICIENT_FUNDS", change: [] };
  } else {
    let status;
    let newCid = cid.filter(item => item[1] != 0).flat(); 
    if (newCid.length == 2){
      if (newCid[1] == (cash - price)){        
        status = "CLOSED";
        changes = cid.reverse();
      }
    } else
      status = "OPEN";
    
    result = { status: status, change: changes };
  }
  return result;
}

checkCashRegister(19.5, 20, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.1], ["QUARTER", 4.25], ["ONE", 90], ["FIVE", 55], ["TEN", 20], ["TWENTY", 60], ["ONE HUNDRED", 100]]) // should return an object.

checkCashRegister(19.5, 20, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.1], ["QUARTER", 4.25], ["ONE", 90], ["FIVE", 55], ["TEN", 20], ["TWENTY", 60], ["ONE HUNDRED", 100]]) // should return {status: "OPEN", change: [["QUARTER", 0.5]]}.

checkCashRegister(3.26, 100, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.1], ["QUARTER", 4.25], ["ONE", 90], ["FIVE", 55], ["TEN", 20], ["TWENTY", 60], ["ONE HUNDRED", 100]]) // should return {status: "OPEN", change: [["TWENTY", 60], ["TEN", 20], ["FIVE", 15], ["ONE", 1], ["QUARTER", 0.5], ["DIME", 0.2], ["PENNY", 0.04]]}.

checkCashRegister(19.5, 20, [["PENNY", 0.01], ["NICKEL", 0], ["DIME", 0], ["QUARTER", 0], ["ONE", 0], ["FIVE", 0], ["TEN", 0], ["TWENTY", 0], ["ONE HUNDRED", 0]]) // should return {status: "INSUFFICIENT_FUNDS", change: []}.

checkCashRegister(19.5, 20, [["PENNY", 0.01], ["NICKEL", 0], ["DIME", 0], ["QUARTER", 0], ["ONE", 1], ["FIVE", 0], ["TEN", 0], ["TWENTY", 0], ["ONE HUNDRED", 0]]) // should return {status: "INSUFFICIENT_FUNDS", change: []}.

checkCashRegister(19.5, 20, [["PENNY", 0.5], ["NICKEL", 0], ["DIME", 0], ["QUARTER", 0], ["ONE", 0], ["FIVE", 0], ["TEN", 0], ["TWENTY", 0], ["ONE HUNDRED", 0]]) // should return {status: "CLOSED", change: [["PENNY", 0.5], ["NICKEL", 0], ["DIME", 0], ["QUARTER", 0], ["ONE", 0], ["FIVE", 0], ["TEN", 0], ["TWENTY", 0], ["ONE HUNDRED", 0]]}.

```
