# Projects from JavaScript Algorithms and Data Structures Projects course at <a href="https://www.freecodecamp.org/" target="blank">FreeCodeCamp</a>

> This repository has a goal to make public all the projects developed on JavaScript Algorithms and Data Structures Projects course from FreeCodeCamp

## Overview and Goals
FreeCodeCamp is a non-profit organization consisting of an interactive learning web platform, an online community forum, chat rooms, Medium publications and local organizations that want to make the web development learning accessible to anyone.

My goals with this project is to practice and improve my skills in Javascript.

## Screenshot

![](https://i.ibb.co/jJ6GzgW/Captura-de-tela-de-2020-03-27-07-33-45.png)

## Proposed projects

### 1. Palindrome Checker
*done*

Return true if the given string is a palindrome. Otherwise, return false.

A palindrome is a word or sentence that's spelled the same way both forward and backward, ignoring punctuation, case, and spacing.

### 2. Roman Numeral Converter
*done*

Convert the given number into a roman numeral.

All roman numerals answers should be provided in upper-case.

### 3. Caesars Cipher
*pending!*

One of the simplest and most widely known ciphers is a Caesar cipher, also known as a shift cipher. In a shift cipher the meanings of the letters are shifted by some set amount.

A common modern use is the ROT13 cipher, where the values of the letters are shifted by 13 places. Thus 'A' ↔ 'N', 'B' ↔ 'O' and so on.

Write a function which takes a ROT13 encoded string as input and returns a decoded string.

All letters will be uppercase. Do not transform any non-alphabetic character (i.e. spaces, punctuation), but do pass them on.

### 4. Telephone Number Validator
*pending!*

Return true if the passed string looks like a valid US phone number.

The user may fill out the form field any way they choose as long as it has the format of a valid US number. The following are examples of valid formats for US numbers (refer to the tests below for other variants):

555-555-5555

(555)555-5555

(555) 555-5555

555 555 5555

5555555555

1 555 555 5555

For this challenge you will be presented with a string such as 800-692-7753 or 8oo-six427676;laskdjf. Your job is to validate or reject the US phone number based on any combination of the formats provided above. The area code is required. If the country code is provided, you must confirm that the country code is 1. Return true if the string is a valid US phone number; otherwise return false.

### 5. Cash Register
*pending!*

Design a cash register drawer function checkCashRegister() that accepts purchase price as the first argument (price), payment as the second argument (cash), and cash-in-drawer (cid) as the third argument.

cid is a 2D array listing available currency.

The checkCashRegister() function should always return an object with a status key and a change key.

Return {status: "INSUFFICIENT_FUNDS", change: []} if cash-in-drawer is less than the change due, or if you cannot return the exact change.

Return {status: "CLOSED", change: [...]} with cash-in-drawer as the value for the key change if it is equal to the change due.

Otherwise, return {status: "OPEN", change: [...]}, with the change due in coins and bills, sorted in highest to lowest order, as the value of the change key.

Currency Unit | Amount
--------- | ------
Penny | $0.01 (PENNY)
Nickel | $0.05 (NICKEL)
Dime | $0.1 (DIME)
Quarter | $0.25 (QUARTER)
Dollar | $1 (DOLLAR)
Five Dollars | $5 (FIVE)
Ten Dollars | $10 (TEN)
Twenty Dollars | $20 (TWENTY)
One-hundred Dollars | $100 (ONE HUNDRED)

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
]
```

