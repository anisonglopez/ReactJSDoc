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

4. Classes
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

5. 


