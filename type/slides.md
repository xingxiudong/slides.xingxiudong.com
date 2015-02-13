
class: center, middle

# ǿ���� JavaScript �������

2015.01

---

class: middel

# ���ַ���

## - TypeScript

## - FlowCheck

## - Flow

---

# TypeScript

- http://www.typescriptlang.org/

- ΢���Ƴ���JavaScript����

- ��װ

```bash
$ npm install -g typescript
```

---

## ����������

```javascript

// greeter.ts

// ���� person Ԥ������Ϊ�ַ���
function greeter(person: string) {
  console.log("Hello, " + person);
}

// ʵ������Ϊ����
greeter([0, 1, 2]);

```

������

```bash

$ tsc greeter.ts
greet.ts(5,9): error TS2345: 
Argument of type 'number[]' is not assignable 
to parameter of type 'string'.

```

---

## Interface ����

```javascript

interface Person {
  firstname: string;
  lastname: string;
}

function greeter(person : Person) {
  return "Hello, " + person.firstname + " " + person.lastname;
}

greeter({firstname: "Jane", lastname: "User"});

```

---

## Class ����

```javascript

class Point {
  x: number;
  y: number;

  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }

  getDist() { 
    return Math.sqrt(this.x * this.x + 
      this.y * this.y); 
  }
}

var p = new Point(3,4);
var dist = p.getDist();

```

---

# Flowcheck

- http://gcanti.github.io/flowcheck/

- ���������Ͷ���ģ�飬����������ʱ��

- ��װ

```bash

$ npm install -g flowcheck

```

---

## ����������

```javascript

// input.js

function sum(a: number, b: number) {
  return a + b;
}

sum('hello','world')

```

��������

```bash

$ browserify -t flowcheck -t [reactify --strip-types] \
  input.js -o output.js

```

---

## �����Ľ��

```javascript

// outpu.js

var _f = require("flowcheck/assert");

function sum(a, b) {
	_f.check(arguments, _f.arguments([_f.number, _f.number]));
  return a + b;
}

```

���н��

```bash

$ node output.js
// throw new TypeError(message);
            ^
TypeError: 
Expected an instance of number got "hello", 
  context: arguments / [number, number] / 0
Expected an instance of number got "world", 
  context: arguments / [number, number] / 1

```
---

## ����

```javascript

// �ӿڵ�����
type MyType = Array<number>;

// ES6 Class
class Person {
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

```

---

# Flow

- http://flowtype.org/

- Facebook �Ƴ��� JavaScript �������ͼ�鹤������Ҫ���ڼ�� React Դ��

- ��װ

```bash

$ npm install --global flow-bin

```

---

## �����ƶ�

```javascript

// hello.js

/* @flow */

function foo(x) {
  return x*10;
}

foo("Hello, world!");

function bar(x) {
  return x.length;
}

var res = bar("Hello") + bar(42);

```
---

## �����ƶϵĽ��

```bash

$ flow check

hello.js:7:5,19: string
This type is incompatible with
/hello.js:4:10,13: number

hello.js:10:10,17: property length
Property not found in
core.js:59:1,72:1: Number

```

---

## ����������

```javascript

/* @flow */

function foo(x: string, y: number): string {
  return x.length * y;
}

foo("Hello", 42);

```

����

```bash

$ flow check

type_annotations.js:4:10,21: number
This type is incompatible with
type_annotations.js:3:37,42: string


```
---

## null���

```javascript
/* @flow */

function length(x) {
  return x.length;
}

var total = length("Hello") + length(null);
```

����

```bash
$ flow check

nulls.js:4:10,17: property length
Property cannot be accessed on possibly null value
nulls.js:7:38,41: null

```
---

## ����ע��

```javascript
/**
  @param {number} x
  @return {number}
 */
function square(x) {
  return x * x;
}

square(5);
```
ת��ע��

```bash
$ flow port annotation.js

+function square(x: number) : number {
   return x * x;
 }

```

---

## ����

```javascript

// interface ������
declare module 'foo-bar' {
  declare function reverse(s: string): string;
  declare function square(x: number): number;
}

// ES6 Class
/* @flow */
class C<X> {
  x: X;
  foo(x: X) { this.x = x; }
  bar(): X { return this.x; }
}

class D extends C<number> {
  bar(): number {
    this.x = super.bar() + 1;
    return this.x;
  }
  static qux(): D { return new D(); }
}
```

---

class: center, middle

# END