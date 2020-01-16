# Javascript core

## Basic

```javascript
a = 0;
var a;
console.log(a);
```
---
```javascript

function Foo() {
}
var res1 = (new Foo()).__proto__ === Foo.prototype;
var res2 = (new Foo()).prototype === undefined;
console.log(res1, res2);
```
---
```javascript
var aTemp = {a: 1};
var bTemp = {b: 2};
var b = Object.assign(aTemp, bTemp);
var c = Object.assign({}, aTemp, bTemp);
aTemp.a = 111;
bTemp.b = 222;
console.log(b, c);
```
---
```typescript
class Test {
  constructor(public x: string, private y: string, z: string) {
  }
  doit() {
    console.log(this.x, this.y, this.z);
  }
}
new Test('first', 'second', 'third');
```
---
```javascript
for (var i = 0; i < 3; i++) {
  setTimeout(() => {
    console.log(i);
  }, 100);
}
```
### как фиксить
Самый распространенный, обернуть в замыкание

```javascript
for (var i = 0; i < 10; i++) {
	(function (i) {
		setTimeout(function () {
			console.log(i);
		}, 100);
	})(i)
}
```
Не все обращали внимание, что в i можно передать не только контекст
```javascript
for (var i = 0; i < 10; i++) {
	setTimeout(function (i) {
		console.log(i);
	}.bind(this, i), 100);
}
```
Так же методам setInterval и setTimeout можно передать аргументы, которые будут прокинуты в качестве аргументов калбек-функции
```javascript
for (var i = 0; i < 10; i++) {
	setTimeout(function (i) {
		console.log(i);
	}, 100, i);
}
```
es6
```javascript
for (let i = 0; i < 10; i++) {
	setTimeout(function () {
		console.log(i);
	}, 100);
}
```
---
```typescript

class A {
  constructor(foo?: string) {}
}

class B extends A {
constructor() {}
}
new B();
```
---
```javascript
async function foo() {
  return new Promise((resolve) => resolve(123));
}

(() => {
  const res = await foo();
  console.log(res);
})();
```
---
## Section 1

```javascript
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
console.log(foo.x);
```
---
Напишите функцию сложения вида add(num1)(num2)..
Примечание: Количество слагаемых не ограничено
В оригинале это задача решается таким образом:
```javascript
const add = (a) => {
  let sum = a;
  const func = (b) => {
    if (b) {
      sum += b;
      return func;
    } else {
      return sum;
    }
  };
  return func;
};
add(2)(3)(); // 5;
```
Но потом вам ставят одно условие. Убрать в конце лишние скобки
```javascript
add(2)(3) // 5
add(1)(2)(5) // 8
```
```javascript
const add = (a) => {
  let sum = a;
  const func = (b) => {
    sum += b;
    return func;
  };
  func.valueOf = () => sum;
return func;
};
console.log(add(2)(3)); // 5;
```
---
```javascript
var a={},
    b={key:'b'},
    c={key:'c'};
a[b]=123;
a[c]=456;
console.log(a[b]);
```
---
Напишите простую функцию, чтобы узнать равен ли один из входных параметров 3.
```javascript
function isThreePassed(){
 const args = Array.prototype.slice.call(arguments);
 return args.indexOf(3) != -1;
}

isThreePassed(1,2) //false
isThreePassed(9,3,4,9) //true
```
А вот интересный эксперимент:
```javascript
const o = {
    '0': 'zero',
    '1': 'one'
};
[].slice.call(o); // [];
const oo = {
    '0': 'zero',
    '1': 'one',
    length: 2
};
[].slice.call(oo); // ["zero", "one"];
```
---
Объедините два массива с вложенностью
[1, [1, 2, [3, 4]], [2, 4]] -> [1, 1, 2, 3, 4, 2, 4]
```javascript
const flatten = (arr) => arr.reduce((flat, toFlatten) =>  flat.concat(Array.isArray(toFlatten) ? flatten(toFlatten) : toFlatten), []);
```
## Section 2
```javascript
a(); b();
var b = function () {
  return “b”;
}
function a() {
  return “a”;
}
```
---
```javascript
var a = {};
Object.defineProperties(a, {
    one: {enumerable: true, value: 'one'},
    two: {enumerable: false, value: 'two'},
});
Object.keys(a); // ["one"]
Object.getOwnPropertyNames(a); // ["one", "two"]
```
---
```javascript
var a = 1;
var b = ++a+a;
console.log(b);
```
---
```javascript
console.log(!+{}[0]);
```
Пояснение: {} = object
* `{}[0] = undefined`
* `+{}[0] = NaN`
* `!+{}[0] = true`

---
```javascript
var a = 3;
switch (a) {
  default: a += 4;
  case 1:  a += 2; break;
  case 2:  a += 3; break;
}
console.log(a);
```
---
```javascript
function f(x, y, z) {
    x = 5;
    arguments[2] = 10;
    alert(x + y + z);
}
f(-1, 0, 1);
```
---
```javascript
var a = [];
console.log((a == a) + ' ' + (a == !a));
```
В первом выражении все понятно, идет сравнение ссылки с самой собой.
А во втором операнд "!a" преобразовывается к boolean и соответственно порождает преобразование к boolean операнда "a". []==false (пустой массив => false), ![]==false (ссылка на объект (в данном случае на массив) с оператором ! => false) т.е. [] == ![]

---
Что из ниже указанного проверит что элемент arr (var arr = ...) является массивом?
* `if (arr.splice) {...}`
* `Array.isArray(arr);`
* `if (arr.constructor === Array) {...}`
* `typeof arr;`
* `arr instanceof Array;`
* `if (arr) {...}`
Пояснение:

1) typeof arr = "object" - не доказывает что это массив;
2) if (arr) { } - проверка на существование элемента;
3) if (arr.splice) { } - проверка, имеет ли элемент метод splice(), так как он есть только у массивов;
4) if (arr.constructor === Array) - проверка через конструктор;
5) Array.isArray(arr) - проверка через функцию isArray();
6) arr instanceof Array - проверка на экземпляр класса ;
---
```javascript
var a  = 44;
(function() {
   var b = 44;
   a = '55';
   (function() {
     var c = 11;
     console.log((a+b)/c);
   })();
})();
// 504
```
---

Дана функция, она принимает в качестве аргументов строки '*', '1', 'b', '1c', реализуйте ее так, что бы она вернула строку '1*b*1c'

```javascript
function getStr() {
	return [].slice.call(arguments, 1).join(arguments[0])
}
```
---
Дано дерево, надо найти сумму всех вершин.

### рекурсия
```javascript
var sum = 0;

function getSum(obj) {
	sum += obj.valueNode;
	if (obj.next != null) {
		for (var i = 0; i < obj.next.length; i++) {
			getSum(obj.next[i]);
		}
	}

	return sum;
}

var tree1 = {
				valueNode: 1,
				next: [
					{
						valueNode: 3,
						next: null
					},
					{
						valueNode: 2,
						next: null
					}
				]
			}

var tree = {
	valueNode: 3,
	next: [{
				valueNode: 1,
				next: null
			},
			{
				valueNode: 3,
				next: null
			},
			{
				valueNode: 2,
				next: null
			},
			{
				valueNode: 2,
				next: [
					{
						valueNode: 1,
						next: null
					},
					{
						valueNode: 5,
						next: null
					}
				]
			}]
};
console.log(getSum(tree1));
sum = 0;
console.log(getSum(tree));
```
### очередь
```javascript
function getSum(obj) {
	var arr = [obj],
		sum = 0,
		current;

	while(arr.length > 0) {
		current = arr.shift();
		sum += current.valueNode;

		if (current.next != null) {
			for (var i = 0; i < current.next.length; i++) {
				arr.push(current.next[i]);
			}
		}
	}

	return sum;
}

var tree = {
	valueNode: 3,
	next: [{
				valueNode: 1,
				next: null
			},
			{
				valueNode: 3,
				next: null
			},
			{
				valueNode: 2,
				next: null
			},
			{
				valueNode: 2,
				next: [
					{
						valueNode: 1,
						next: null
					},
					{
						valueNode: 5,
						next: null
					}
				]
			}]
};
getSum(tree);
```
---
Есть массив в котором лежат объекты с датами, отсортировать по датам.
```javascript
var arr = [{date: '10.01.2017'}, {date: '05.11.2016'}, {date: '21.13.2002'}];

arr.forEach(function(item) {
	var arrDate = item.date.split('.'),
      date = new Date(Number(arrDate[2]), Number(arrDate[1]), Number(arrDate[0]));
      item.time = date.getTime();
});

arr.sort(function (a, b) {
  if (a.time - b.time < 0) {
        return false;
      } else {
        return true;
      }
});

var res = arr.map(function (item) {
  return {date: item.date};
});

console.log(res);
```
---

Каким образом можно обойтись без промисов?

По старинке, вводили переменную-счетчик и как-только наступало окончание очередного асинхронного действия, сравнивали переменную с общем количеством.

---
У нас есть три запроса к серверу, один возвращает нам имя пользователя, второй его данные, а третий изображение для аватарки, мы для каждого запроса используем по промису, объединяя их в цепочку, что будет если в одном из запросов произойдет ошибка, довыполнится ли цепочка?

Нет
---
Сортировка пузырьком.
```javascript
var m = [1, 7, 5, 13, 8],
      count = m.length - 1,
      max;
for (var i = 0; i < count; i++) {
    for (var j = 0; j < count - i; j++) {
        if (m[j] > m[j + 1]) {
            max = m[j];
            m[j] = m[j + 1];
            m[j + 1] = max;
        }
    }
}
```
---
Есть строка, состоящая из разных скобок, проверить закрыты ли все.  Пример строки: "())({}}{()][]["
```javascript
function validBraces(str) {

	var arrOpenSymbols = [],
		result = false,
		countOpenSymbols;
	if (str.length > 0) {
		for (var i = 0; i < str.length; i++) {
			if (str[i] === '{' || str[i] === '[' || str[i] === '(') {
				arrOpenSymbols.push(str[i]);
			} else {
				countOpenSymbols = arrOpenSymbols.length;
				if ((str[i] === '}' && arrOpenSymbols[(countOpenSymbols-1)] === '{') ||
					(str[i] === ']' && arrOpenSymbols[(countOpenSymbols-1)] === '[') ||
					(str[i] === ')' && arrOpenSymbols[(countOpenSymbols-1)] === '(')
					) {
						arrOpenSymbols.pop();
				}
			}
		}

		if (arrOpenSymbols.length === 0) {
			result = true;
		} else {
			result = false;
		}
	}
	return result;
}
console.log('');
console.log(validBraces('()'));
console.log(validBraces('[)'));
console.log(validBraces('{}[]()'));
console.log(validBraces('([{}])'));
console.log(validBraces('())({}}{()][]['));
```
---
---
Что выведется в результате?
```javascript
var i = 10;
var array = [];

while (i--) {
    (function (i) {
        var i = i;
        array.push(function() {
            return i + i;
        });
    })(i);
}

console.log([
    array[0](),
    array[1](),
])
```
[18, 16], так как за счет функции

`(function (i) {})(i);`

создает замыкание, var i = i — уже принадлежат областям видимости в замыканиях.

`function() { return i + i; }`

в начале поищет в своей области видимости i, не найдя, подымется на уровень выше и там найдет его. Из функции вернется сумма, которая будет положена в массив последним элементом.

---
Что вернет метод?
```javascript
function Book() {
    this.name = 'foo'
}

Book.prototype = {
    getName: function() {
        return this.name;
    }
};

var book = new Book();

Book.prototype.getUpperName = function() {
    return this.getName().toUpperCase();
}

book.getUpperName();
// 'FOO'
```
---
Реализуйте функцию zip для массивов в JS
```javascript
Array.prototype.zip=function ( ...arrays){
   return this.map((val, i) => arrays.reduce((a, array) => [...a, array[i]], [val]));
}
console.log([1, 2, 3].zip([4, 5, 6])) //[[1, 4], [2, 5], [3, 6]]

```
---
Что такое типизированный массив? Где лучше использовать его, чем обычный массив?

Типизированный массив позволяет хранить необработанные двоичные данные для повышения производительности. Как известно, обычные массивы могут хранить любые данные и динамически изменять свой размер, поэтому вычисление большого объема данных требует времени. В последние годы веб-приложения стали более сложными, им нужно работать с видео, аудио данными, обрабатывать соединения WebSocket, поэтому очевидно, что нам нужен какой-то способ для быстрой обработки двоичных данных.

Существует 4 класса типизированных массивов: ArrayBuffer, Uint32Array,Uint8Array, Float32Array.

---
Что такое класс Proxy в ECMAScript6 ?

Прокси-это объект, который перехватывает попытки доступа к другому объекту и может изменять их. Синтаксис:

`let proxy = new Proxy(target, handler)`

---

```javascript
function() {
   var a = b = 5;
})();

console.log(b);

```

Код выше напишет 5.

Хитрость этого вопроса заключается в том, что в IIFE есть два задания, но переменная a объявляется ключевым словом var. Это означает, что a является переменной функции. b же присвоена глобальной области.

Другой хитростью этого вопроса является то, что он использует строгий режим ('use strict';) в функции. Если был включен строгий режим, код покажет ошибку “Uncaught ReferenceError: b не определён”. Помните, что строгий режим требует, чтобы вы ссылались на глобальные области. Таким образом, вы должны написать:

```javascript
(function() {
   'use strict';
   var a = window.b = 5;
})();

console.log(b);
```

---

```javascript
var fullname = 'John Doe';
var obj = {
   fullname: 'Colin Ihrig',
   prop: {
      fullname: 'Aurelio De Rosa',
      getFullname: function() {
         return this.fullname;
      }
   }
};
console.log(obj.prop.getFullname());
var test = obj.prop.getFullname;
console.log(test());
```

Код выдаст Aurelio De Rosa и John Doe. Причина в том, что контекст функции, вызываемый ключевым this словом, в JavaScript зависит от того, как именно вызывается функция, а не от того, как она определена.
Вызов первых console.log ( ), getFullname ( ) вызывается функцией объекта obj.prop. Таким образом, контекст относится к последнему и возвращает “fullname” как свойство объекта. В противном случае, когда getFullname ( ) присваивается переменной, контекст относится к глобальному объекту. Это происходит потому, что тест устанавливается как свойство глобального объекта (window). По этой причине функция возвращает значение свойства fullnameиз window, которая в данном случае является кодом, устанавливаемым в первой строке фрагмента.

Исправьте предыдущий вопрос так, чтобы последний console.log ( ) стал Aurelio De Rosa.

Вопрос может быть изменен, повлияв на контекст функции, используя функции call ( ) или apply ( ). Если вы не знаете их и их отличия, вам стоит прочесть статью. В коде ниже я буду использовать call ( ), но в этом случае применяется apply ( ), результат будет тот же:

```javascript
console.log(test.call(obj.prop));
```

## see also

* [https://github.com/lydiahallie/javascript-questions](https://github.com/lydiahallie/javascript-questions)
* [https://github.com/FAQGURU/FAQGURU](A list of interview questions)
* [https://github.com/h5bp/Front-end-Developer-Interview-Questions](Front-end Job Interview Questions)
* [https://github.com/khan4019/front-end-Interview-Questions](Front end Interview Questions)
* [https://github.com/yangshun/tech-interview-handbook](Materials to help you rock your next coding interview)
* [https://github.com/loiane/javascript-datastructures-algorithms](https://github.com/loiane/javascript-datastructures-algorithms)
* [https://github.com/trekhleb/javascript-algorithms](https://github.com/trekhleb/javascript-algorithms)
* [https://github.com/ufocoder/javascript.anomaly](not obvious behaviors in JS)
* [https://github.com/denysdovhan/wtfjs](A list of funny and tricky JavaScript examples)
* [https://github.com/mbeaudru/modern-js-cheatsheet](Cheatsheet for the JavaScript knowledge you will frequently encounter in modern projects)
* [https://github.com/rstacruz/cheatsheets](Devhints)
* [https://github.com/goldbergyoni/nodebestpractices](Node.js best practices list)
* [https://github.com/wesbos/JavaScript30](Starter Files + Completed solutions for the JavaScript 30 Day Challenge.)
* [https://github.com/30-seconds/30-seconds-of-code](Short JavaScript code snippets for all your development needs)
* [https://github.com/30-seconds/30-seconds-of-interviews](A curated collection of common interview questions to help you prepare for your next interview)
* [https://github.com/rtivital/jsraccoon](советы по верстке и написанию JavaScript кода)
* [https://github.com/MostlyAdequate/mostly-adequate-guide-ru](Mostly adequate guide to FP (ru)
