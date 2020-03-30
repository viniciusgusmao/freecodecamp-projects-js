# 1. Palindrome Checker

Return true if the given string is a palindrome. Otherwise, return false.

A palindrome is a word or sentence that's spelled the same way both forward and backward, ignoring punctuation, case, and spacing.

```js

function palindrome(str) {
  const regex = /\s|\W|_/g;
  let strMod = str.replace(regex,'').toLowerCase();
  let strModPalindrome = strMod.split('').reverse().join('');
  return strMod == strModPalindrome;
}

palindrome("eye"); // true
palindrome("_eye"); // true
palindrome("race car"); // true
palindrome("not a palindrome"); // false
palindrome("A man, a plan, a canal. Panama"); // true
palindrome("never odd or even"); // true
palindrome("nope"); // false
palindrome("My age is 0, 0 si ega ym."); // true
palindrome("1 eye for of 1 eye."); // false
palindrome("0_0 (: /-\ :) 0-0"); // true
palindrome("five|\_/|four"); // false

```