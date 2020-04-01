### 3. Caesars Cipher

One of the simplest and most widely known ciphers is a Caesar cipher, also known as a shift cipher. In a shift cipher the meanings of the letters are shifted by some set amount.

A common modern use is the ROT13 cipher, where the values of the letters are shifted by 13 places. Thus 'A' ↔ 'N', 'B' ↔ 'O' and so on.

Write a function which takes a ROT13 encoded string as input and returns a decoded string.

All letters will be uppercase. Do not transform any non-alphabetic character (i.e. spaces, punctuation), but do pass them on.

```js

function rot13(str) {
  let unicodeA = 'A'.charCodeAt(0);
  let unicodeZ = 'Z'.charCodeAt(0);
  let arrLetters = [];
  for(let i = unicodeA; i <= unicodeZ; i++){
    arrLetters.push(String.fromCharCode(i));
  }
  let regex = /\W/g;
  let result = str.split(' ').map(item => {
    let word = item.split('').map(letter => {
      if (!regex.test(letter)){
        let pos = arrLetters.indexOf(letter);
        return letter = (pos + 13 <= 25) ? arrLetters[pos+13] : arrLetters[13-(26-pos)];
      } else return letter;
    }).join('');
    return item = word;
  }).join(' ');
  return result;
}

rot13("SERR PBQR PNZC") // should decode to FREE CODE CAMP
rot13("SERR CVMMN!") // should decode to FREE PIZZA!
rot13("SERR YBIR?") // should decode to FREE LOVE?
rot13("GUR DHVPX OEBJA SBK WHZCF BIRE GUR YNML QBT.") // should decode to THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG.

```