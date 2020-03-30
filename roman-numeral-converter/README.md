### 2. Roman Numeral Converter

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
    10: 'X'
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
                result.push(firstLetter <= 3 ? 'X'.repeat(firstLetter) : firstLetter == 5 ? 'L' : 'L'+'X'.repeat(firstLetter-5))
                break;
             case 3:
                    result.push(firstLetter <= 3 ? 'C'.repeat(firstLetter) : firstLetter == 5 ? 'D' : 'D'+'C'.repeat(firstLetter-5)); 
                break;
            case 4:
                result.push('M'.repeat(firstLetter))    
                break;
            default:
                break
         }
     }
 }) 
 return result.join('');
}

convertToRoman(2) // should return "II".
convertToRoman(3) // should return "III"
convertToRoman(4) // should return "IV"
convertToRoman(5) // should return "V"
convertToRoman(9) // should return "IX".
convertToRoman(12) // should return "XII".
convertToRoman(16) // should return "XVI".
convertToRoman(29) // should return "XXIX".
convertToRoman(44) // should return "XLIV".
convertToRoman(45) // should return "XLV"
convertToRoman(68) // should return "LXVIII"
convertToRoman(83) // should return "LXXXIII"
convertToRoman(97) // should return "XCVII"
convertToRoman(99) // should return "XCIX"
convertToRoman(400) // should return "CD"
convertToRoman(500) // should return "D"
convertToRoman(501) // should return "DI"
convertToRoman(649) // should return "DCXLIX"
convertToRoman(798) // should return "DCCXCVIII"
convertToRoman(891) // should return "DCCCXCI"
convertToRoman(1000) // should return "M"
convertToRoman(1004) // should return "MIV"
convertToRoman(1006) // should return "MVI"
convertToRoman(1023) // should return "MXXIII"
convertToRoman(2014) // should return "MMXIV"
convertToRoman(3999) // should return "MMMCMXCIX"

```