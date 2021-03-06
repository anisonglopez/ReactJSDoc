# Getting Started with Create React App
## Section 2 Javascript Refresher
### 1. Understanding "let" & "const"
- let ใช้ประกาศตัวแปรที่เป็นประเภท Variable
- const ใช้ประกาศตัวแปรเป็น constant value เป็นค่า value คงที่ไม่มีเปลี่ยนแปลง

![alt text](https://miro.medium.com/max/1200/0*mYuuRwjUfUOAdHpo.jpg)


### 2. Arrow function
```JS
function myFunc(name){
    // This old function write
}
//  Arrow function
const myFunc = () => {
    // ... Code here
}
```
Example
```JS
printMyName('Jhon', 35);
const printMyName = (name, age) => {
    console.log(name, age)
    //  output ==Jhon35
}
```
เรายังสามารถเขียนมันให้สั้นลงกว่านี้ได้อีก
```JS
const multiply = (number) => number * 2 ;
console.log(multiply(2));
//  Outout = 4
```
### 3. Exports and Imports (Modules)
Next generation javascript offers is about writing **modular**

![alt text](https://samanthaming.gumlet.io/tidbits/79-module-cheatsheet.jpg.gz)

Import Export ในภาษา JavaScript มีไว้สำหรับนำเข้า Code จากไฟล์อื่น (เราจะทำการเขียนไฟล์แยกตาม Module การใช้งาน และแยกไฟล์ตาม Component ที่เรียกใช้งานบ่อย ๆ) ตัวอย่าง
```JS
import person from './person.js'
```
แต่ก่อนที่จะ Import ได้ ในไฟล์ **person.js** จะต้องมีการ export ด้วย
```JS
const person = {
  name: 'Max'
}
export default person
```

utility.js
```JS
export const clean = () =>{
    //  Code Here
}
export const BaseData = 10;
```

app.js หรือ app.tsx
```JS
import person from './person.js';
//  หรือ person.tsx เขียนแบบนี้
import person from './person';
// person.tsx
// เมื่อมีการ export default แบบนี้จะเป็นการ export ทั้งหมด
// สามารถ import โดยใช้ชื่อตัวแปรอื่นก็ได้ เช่น prs
import prs from './person';
```
การ export เฉพาะบางตัวแปร **utility.js**
```JS
export const a = () => {...}
export const b = 1
```
กรณีของ utility.js แบบนี้ การเขียน Import ต้องเป็นลักษณะนี้
```JS
import { a } from './utility.js'
import { b } from './utility.js'
//  ใส่ปีกกาตามด้วยชื่อ Function
```
ชื่อตัวแปรจะต้องเป็นชื่อเดียวกันกับชื่อตัวแปรที่ export แต่ถ้าอยากเปลี่ยนก็สามารถทำได้
```JS
import { a as c } from './utility.js'
```
หรือจะ import มาทั้งหมดก็ได้
```JS
import * as abc from './utility.js'
//  ตัวอย่าง import * นี้ จะพบตัวอย่างการใน app.tsx
```

### 4. Classes
Classes is a blueprint for javaScript object.  Class เปรียบเสมือนกับ blueprint หรือแบบพิมพ์เขียว ที่สามารถนำไปสร้างเป็นสิ่งของ( object ) ตาม  blueprint นั้น ๆ โดยภายใน class เรานั้น จะมีการตั้งค่าเริ่มต้นหรือ constructor เพื่อให้เป็นการทำงานเริ่มต้นของการสร้าง object หนึ่ง หน้าตาในการเรียกใช้งานจะคล้ายๆกับ การประกาศเรียกใช้ Function 

![alt text](https://samanthaming.gumlet.io/tidbits/39-es6-classes.jpg.gz)

example 1
```JS
class Person {
    constructor() {
        this.name = "Max";
    } 

    printMyName() { // เรียกว่าการสร้าง Method ภายใน Class
        console.log(this.name)
    }
}

const person == new Person();
person.printMyName();
// Output = "Max"
```
example 2
```JS
class Human {
    constructor() {
        $this.gender = 'male';
    }

    printGender() {
        console.log(this.gender);
    }
}
class Person extends Human{
    constructor() {
        super(); //The super keyword is used to access and call functions on an object's parent.
        this.name = "Max";
        // this.gender = 'female';
        //  output.gender = 'female'
    } 

    printMyName() { // เรียกว่าการสร้าง Method ภายใน Class
        console.log(this.name)
    }
}

const person == new Person();
person.printMyName();
person.printGender();
// Output = "Max"
//  "male"
```

### 5. Classes, Properties, Methods

### 6. The Spread & Rest Operator
- Rest parameter คือ การรวบรวม Values ที่เหลือทั้งหมดไปไว้ Array สรุป (values -> array)
- Spread operator คือ การดำเนินแยกค่าใน Arrays ออกเป็น Values สรุป (array -> values)
![alt text](https://i.ytimg.com/vi/qMlReipXP5A/maxresdefault.jpg)
### Rest parameter
```JS
// REST example 1
function abc(a, b, ...z) {
  console.log(a, ' ', b); // hi-ya hi
  console.log(z); // ["hey", "hello", "howdy", "hullo"]
  console.log(z[0]); // hey
  console.log(z.length); // 4
}
abc("hi-ya", "hi", "hey", "hello", "howdy", "hullo");
// REST example 2
const [c, ...m] = [1,2,3,4,5];
console.log(c); // 1
console.log(m); // [2,3,4,5]
```
### Spread operators
```JS
// Spread  example 1
const arr = ["b", "c", "d"];
const arr2 = ["a", ...arr];
console.log(arr2);  // ["a", "b", "c", "d"]
// Spread  example 2
const params = [ "hello", true, 7 ];
const other = [ 1, 2, ...params ]; // [1,2,"hello", true, 7]
// มีค่าเท่ากับ
const other = [1, 2].concat(params); // [1,2,"hello", true, 7]
// Rest Parameter vs. Spread operator (การหาผลรวม)
// For Spread operator
function sum1(x, y, z) {
  return x + y + z;
}
// For Rest Parameter
function sum2(...arr) {
  return arr[0] + arr[1] + arr[2];
  // used reduce for dynamic
  // return a.reduce((value, sum) => sum + value)
}
// input values
const numbers = [1, 2, 3, 4, 5];
// Result of Spread operator
console.log(sum1(...numbers)); // 6
// Result of Rest Parameter
console.log(sum2(1, 2, 3, 4, 5)); // 6
```

### Destructuring
Destructuring allows you to easily extract array elements or object properties and store them in variables. Array destructuring
```JS
const numbers = [1, 2, 3];
[num1, , num3] = numbers;
console.log(num1, num3)
// Output = 1, 3
```

### Reference and Primitive Refresher
```JS
const number = 1;
const num2 = number;
console.log(num2)
//  Output = 1
```
```JS
const person = {
    name: 'Max';
};
const SecondPerson = person;
//  SecondPerson ถูกเก็บลง memmory แล้ว
person.name = 'NewName';
console.log(SecondPerson)
// Output = NewName แทน ทั้ง ๆ ที่ควรจะเป็น Max ตามความเข้าใจ
```
ัดังนั้นเทคนิคการ Copy ตัวแปร และนำมาใช้ใหม่ และไม่ให้ค่าที่เรียกใช้ทับกับตัวแปรเดิม ให้เขียนดังนี้
```JS
const person = {
    name: 'Max';
};
const SecondPerson = person;
//  SecondPerson ถูกเก็บลง memmory แล้ว
person.name = 'NewName';
console.log(SecondPerson)
//  Output = 'Max'
```





