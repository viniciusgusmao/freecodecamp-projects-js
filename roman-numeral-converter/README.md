### 2. Roman Numeral Converter
*pending!*

Convert the given number into a roman numeral.

All roman numerals answers should be provided in upper-case.

```js

function convertToRoman(num) {
 const numberToRoman = {
    1: 'I',
    2: 'II',
    3: 'III',
    4: 'IV',
    5: 'V',
    6: 'VI',
    7: 'VII',
    8: 'VIII',
    9: 'IX',
    10: 'X',
    50: 'L',
    100: 'C',
    500: 'D',
    1000: 'M'
 } 
 let arrAux = [];
 String(num).split('').forEach((item,idx,arr) => {
     arrAux.push(item+'0'.repeat(arr.length-(idx+1)))
 })
 let result = [];
 arrAux.forEach(item => {
     let firstLetter = item[0];
     if (firstLetter == 4 || firstLetter == 9){
         switch(item.length){
             case 1:
                result.push(numberToRoman[item]);
                break;
             case 2:
                result.push(firstLetter == 4 ? "XL" : "XC");
                break;
             case 3:
                result.push(firstLetter == 4 ? "CD" : "CM");
                break;
            default:
                break
         }
     } else {
         switch(item.length){
             case 1:
                result.push(numberToRoman[item]);
                break;
             case 2:
                result.push('X'.repeat(firstLetter))
                break;
             case 3:
                result.push("C".repeat(firstLetter))
                break;
            case 4:
                result.push("M".repeat(firstLetter))
                break;
            default:
                break
         }
     }
 }) 
 console.log(result.join(''))
 return result.join('');
}

convertToRoman(68);


```