# Angular

## What is component decorators

The main objectives of decorators is to add some metadata to the class that will tell Angular 4 how to process a class. Or in another words, Decorators are functions that modify JavaScript classes. Angular has many decorators that attach metadata to classes so that it knows what those classes mean and how they should work.
If we consider Component in Angular 4, we will have following options to configure.

* `selector`: — define the name of the HTML element in which our component will live.
* `template` or `templateUrl`: — It can be inline string or link an external html file. It allows us to tie logic from our component directly to a view.
* `styles`: — the styles array for our specific component. We can also link external CSS by styleUrls.
* `directives`: — another component directives we want to use inside our components.
* `providers`: — This is the place we are passing the services that we need insider our components.

## What is compilation in Angular? And what are the types of compilation in Angular?

An Angular application consists largely of components and their HTML templates. Before the browser can render the application, the components and templates must be converted to executable JavaScript by the Angular compiler.

There is actually only one Angular compiler. The difference between AOT and JIT is a matter of timing and tooling. There are two types of compilation Angular 4 provides.

* `Just-in-time (JIT) compilation`: This is a standard development approach which compiles our Typescript and html files in the browser at runtime, as the application loads. It is great but has disadvantages. Views take longer to render because of the in-browser compilation step. App size increases as it contains angular compiler and other library code that won’t actually need.
* `Ahead-of-time (AOT) compilation`: With AOT, the compiler runs at the build time and the browser downloads only the pre compiled version of the application. The browser loads executable code so it can render the application immediately, without waiting to compile the app first. This compilation is better than JIT because of Fast rendering, smaller application size, security and detect template errors earlier.

## What is @NgModule?

An `NgModule` class describes how the application parts fit together. Every application has at least one NgModule, the root module that we bootstrap to launch the application.

Here the AppComponent is the root module of our application that Angular creates and inserts it into the index.html page.

## What are all the metadata properties of NgModule? And what are they used for?

@NgModule accepts a metadata object that tells Angular how to compile and launch the application. The properties are:

`imports` – Modules that the application needs or depends on to run like, the BrowserModule that every application needs to run in a browser.

`declarations` – the application's components, which belongs to the NgModuleclass. We must declare every component in an NgModule class. If we use a component without declaring it, we'll see a clear error message in the browser console.

`bootstrap` – the root component that Angular creates and inserts into the index.html host web page. The application will be launched by creating the components listed in this array.

## What is Template reference variables?

A template reference variable (#var) is a reference to a DOM element within a template. We use hash symbol (#) to declare a reference variable in a template.

```html
<input #name placeholder="Your name">
{{name.value}}
```

In the above code the #name declares a variable on the input element. Here the name refers to the input element. Now we can access any property of the inputDOM, using this reference variable. For example, we can get the value of the inputelement as name.value and the value of the placeholder property by name.placeholder anywhere in the template.
Finally, a Template reference variable refers to its attached element, component or directive. It can be accessed anywhere in the entire template. We can also use ref- instead of #. Thus we can also write the above code as ref-name.

## What are structural directives?

Structural directives are responsible for HTML layout. They shape or reshape the DOM’s structure, typically by adding, removing, or manipulating elements. Structural directives are easy to recognize. An asterisk (*) precedes the directive attribute name as in this example.

```html
<ul>
  <li *ngFor="let name of names">{{name}}</li>
</ul>
```

The ngFor directive iterates over the component's names array and renders an instance of this template for each name in that array.
Some of the other structural directives in Angular are ngIf and ngSwitch.

## What is Directive in Angular 4? How it differs from Components?

Directives allow us to attach behavior to elements in the DOM, for example, doing something on mouse over or click. In Angular, a Directive decoraor (@Directive) is used to mark a class as an Angular directive and provides additional metadata that determines how the directive should be processed. Below are the metadata properties of a directive.

* `selector` - css selector that identifies this component in a template
`host` - map of class property to host element bindings for events, properties and attributes
* `inputs` - list of class property names to data-bind as component inputs
`outputs` - list of class property names that expose output events that others can subscribe to
* `providers` - list of providers available to this component and its children
* `queries` - configure queries that can be injected into the component
* `exportAs` - name under which the component instance is exported in a template

A Component is a directive with a template. So we should use a Component whenever we want reusable set of DOM elements with behaviors of UI. And we should use a Directive whenever we want reusable behavior to supplement the DOM.

## What are all the types of Directives?

There are three types of directives in Angular. They are attribute directives, structural directives, and components.

* `Structural directives` change the DOM layout by adding and removing DOM elements. For example, `*ngIf` and `*ngFor`
* `Attribute directives` change the appearance or behavior of an element. . For example, `*ngStyle` and `*ngClass`
* `Components` are basically directives with a template.

## What are all the uses of a service?

 Services encapsulates business logic and separates them from UI concerns or the controller concerns, which governs them both.

Services focus on functionality thus benefits in maintainability. The separation of UI logic from business logic is intended to reduce the coupling between the UI layer and the Model layer, leading to a cleaner design that is easier to develop, test, and maintain.

## What is Pure and Impure Pipes?

Pure pipes are stateless that flow input date without remembering anything or causing detectable side-effects. Pipes are pure by default, hence most pipes are pure. We can make a pipe impure by setting its pure flag to false. Angular executes a pure pipe only when it detects a pure change to the input value. A pure change is either a change to a primitive input value or a changed object reference.

Impure pipes are those which can manage the state of the data they transform. A pipe that creates an HTTP request, stores the response and displays the output, is a impure or stateful pipe. Stateful Pipes should be used cautiously. Angular provides AsyncPipe, which is stateful. In the following code, the pipe only calls the server when the request URL changes and it caches the server response.

## What is Redux and @ngRx?

Redux is an application state manager for JavaScript applications, and keeps with the core principles of the Flux-architecture by having a unidirectional data flow in our application. Redux applications have only one global, read-only application state. This state is calculated by “reducing” over a collection or stream of actions that update it in controlled ways.

@ngrx is a set of modules that implement the same way of managing state as well as some of the middleware and tools in the Redux ecosystem. In other way, ngrx is a collection of reactive libraries for angular, containing a redux implementation and many other useful libraries.

Using this technique, we keep our application state in Store and everything saved in the store is read only. The only way to change the state is to emit an action, an object describing what happened.

## How to prevent security threads in Angular App? What are all the ways we could secure our App?

Some of them are:

* Avoid using/injecting dynamic HTML content to your component.
* If using external HTML which is coming from database or somewhere outside the application, sanitize it before using.
* Try not to put external urls in the application unless it is trusted. Avoid url re-direction unless it is trusted.
* Consider using AOT compilation or offline compilation.
* Try to prevent XSRF attack by restricting the api and use of the app for known or secure environment/browsers.

## How to optimize Angular app?

* Consider lazy loading instead of fully bundled app if the app size is more.
* Make sure that any 3rd party library, which is not used, is removed from the application.
* Have all dependencies and dev-dependencies are clearly separated.
* Make sure the application doesn’t have un-necessary import statements.
* Make sure the application is bundled, uglified, and tree shaking is done.
* Consider AOT compilation.

## What is NgZone service? How Angular is notified about the changes?

Zone.js is one of the Angular dependencies which provides a mechanism, called zones, for encapsulating and intercepting asynchronous activities in the browser (e.g. setTimeout, setInterval, promises). These zones are execution contexts that allow Angular to track the start and completion of asynchronous activities and perform tasks as required (e.g. change detection). Zone.js provides a global zone that can be forked and extended to further encapsulate/isolate asynchronous behaviour, which Angular does so in its NgZone service, by creating a fork and extending it with its own behaviours.

The NgZone service provides us with a number of Observables and methods for determining the state of Angular's zone and to execute code in different ways inside and outside Angular's zone.

NgZone exposes a set of Observables that allow us to determine the current status, or stability, of Angular's zone.

* onUnstable – Notifies when code has entered and is executing within the Angular zone.
* onMicrotaskEmpty - Notifies when no more microtasks are queued for execution. Angular subscribes to this internally to signal that it should run change detection.
* onStable – Notifies when the last onMicroTaskEmpty has run, implying that all tasks have completed and change detection has occurred.
* onError – Notifies when an error has occurred. Angular subscribes to this internally to send uncaught errors to its own error handler, i.e. the errors you see in your console prefixed with 'EXCEPTION:'.

We can inject the NgZone service in our component/services/etc. and can subscribe to these observables.

```typescript
import { Injectable, NgZone } from '@angular/core';

@Injectable()
export class OurZoneWatchingService() {
  constructor(private ngZone: NgZone) {
    this.ngZone.onStable.subscribe(this.onZoneStable);
  }
  onZoneStable() {
    console.log('We are stable');
  }
}
```
Subscribing to these can help you determine if your code is unexpectedly triggering change detection as a result of operations that do not affect application state.

---

<!-- https://medium.com/@vigowebs/frequently-asked-angular-interview-questions-and-answers-d996be87cc7c -->


## Основы TypeScript

### Что такое декоратор?

Декоратор - способ добавления метаданных к объявлению класса. Это специальный вид объявления, который может быть присоединен к объявлению класса, методу, методу доступа, свойству или параметру.

Декораторы используют форму @expression, где expression - функция, которая будет вызываться во время выполнения с информацией о декорированном объявлении.

Чтобы написать собственный декоратор, нам нужно сделать его factory и определить тип:
* ClassDecorator
* PropertyDecorator
* MethodDecorator
* ParameterDecorator

#### Декоратор класса

Вызывается перед объявлением класса, применяется к конструктору класса и может использоваться для наблюдения, изменения или замены определения класса. Expression декоратора класса будет вызываться как функция во время выполнения, при этом конструктор декорированного класса является единственным аргументом. Если класс декоратора возвращает значение, он заменит объявление класса вернувшимся значением.

```typescript
export function logClass(target: Function) {
      // Сохранение ссылки на оригинальный конструктор
      const original = target;

      // Функция генерирует экземпляры класса
      function construct(constructor, args) {
          const c: any = function () {
              return constructor.apply(this, args);
          }
          c.prototype = constructor.prototype;
          return new c();
      }

      // Определение поведения нового конструктора
      const f: any = function (...args) {
          console.log(`New: ${original['name']} is created`);
          //New: Employee создан
          return construct(original, args);
      }

      // Копирование прототипа, чтобы оператор intanceof работал
      f.prototype = original.prototype;

      // Возвращает новый конструктор, переписывающий оригинальный
      return f;
  }

  @logClass
  class Employee {

  }

  let emp = new Employee();
  console.log('emp instanceof Employee');
  //emp instanceof Employee
  console.log(emp instanceof Employee);
  //true
```

#### Декоратор свойства

Объявляется непосредственно перед объявлением метода. Будет вызываться как функция во время выполнения со следующими двумя аргументами:

* target - прототип текущего объекта, т.е. если Employee является объектом, Employee.prototype
* propertyKey - название свойства

```typescript
function logParameter(target: Object, propertyName: string) {

      // Значение свойства
      let _val = this[propertyName];

      // Геттер свойства
      const getter = () => {
          console.log(`Get: ${propertyName} => ${_val}`);
          return _val;
      };

      // Сеттер свойства
      const setter = newVal => {
          console.log(`Set: ${propertyName} => ${newVal}`);
          _val = newVal;
      };

      // Удаление свойства
      if (delete this[propertyName]) {

          // Создает новое свойство с геттером и сеттером
          Object.defineProperty(target, propertyName, {
              get: getter,
              set: setter,
              enumerable: true,
              configurable: true
          });
      }
  }

  class Employee {

      @logParameter
      name: string;
  }

  const emp = new Employee();
  emp.name = 'Mohan Ram';
  console.log(emp.name);
  // Set: name => Mohan Ram
  // Get: name => Mohan Ram
  // Mohan Ram
```

#### Декоратор метода

Объявляется непосредственно перед объявлением метода. Будет вызываться как функция во время выполнения со следующими двумя аргументами:

* target - прототип текущего объекта, т.е. если Employee является объектом, Employee.prototype
* propertyName - название свойства
* descriptor - дескриптор свойства метода т.е. - Object.getOwnPropertyDescriptor (Employee.prototype, propertyName)

```typescript
export function logMethod(
     target: Object,
     propertyName: string,
     propertyDesciptor: PropertyDescriptor): PropertyDescriptor {
     const method = propertyDesciptor.value;

     propertyDesciptor.value = function (...args: any[]) {

         // Конвертация списка аргументов greet в строку
         const params = args.map(a => JSON.stringify(a)).join();

         // Вызов greet() и получение вернувшегося значения
         const result = method.apply(this, args);

         // Конвертация результата в строку
         const r = JSON.stringify(result);

         // Отображение в консоли деталей вызова
         console.log(`Call: ${propertyName}(${params}) => ${r}`);

         // Возвращение результата вызова
         return result;
     }
     return propertyDesciptor;
 }

 class Employee {

     constructor(
         private firstName: string,
         private lastName: string
     ) {
     }

     @logMethod
     greet(message: string): string {
         return `${this.firstName} ${this.lastName} says: ${message}`;
     }

 }

 const emp = new Employee('Mohan Ram', 'Ratnakumar');
 emp.greet('hello');
 //Call: greet("hello") => "Mohan Ram Ratnakumar says: hello"
```

#### Декоратор параметра

Объявляется непосредственно перед объявлением метода. Будет вызываться как функция во время выполнения со следующими двумя аргументами:

* target - прототип текущего объекта, т.е. если Employee является объектом, Employee.prototype
* propertyKey - название свойства
* index - индекс параметра в массиве аргументов

```typescript
function logParameter(target: Object, propertyName: string, index: number) {

     // Генерация метаданных для соответствующего метода
     // для сохранения позиции декорированных параметров
     const metadataKey = `log_${propertyName}_parameters`;

     if (Array.isArray(target[metadataKey])) {
         target[metadataKey].push(index);
     }
     else {
         target[metadataKey] = [index];
     }
 }

 class Employee {
     greet(@logParameter message: string): void {
         console.log(`hello ${message}`);
     }
 }
 const emp = new Employee();
 emp.greet('world');
```

## Основные концепции

### Что такое Angular?

Angular — это платформа для разработки мобильных и десктопных веб-приложений. Наши приложения теперь представляют из себя «толстый клиент», где управление отображением и часть логики перенесены на сторону браузера. Так сервер уделяет больше времени доставке данных, плюс пропадает необходимость в постоянной перерисовке. С Angular мы описываем структуру приложения декларативно, а с TypeScript начинаем допускать меньше ошибок, благодаря статической типизации. В Angular присутствует огромное количество возможностей из коробки. Это может быть одновременно и хорошо и плохо, в зависимости от того, что вам необходимо.

#### Какие плюсы можно выделить:

* Поддержка Google, Microsoft
* Инструменты разработчика (CLI)
* Typescript из коробки
* Реактивное программирование с RxJS
* Единственный фреймворк с Dependency Injection из коробки
* Шаблоны, основанные на расширении HTML
* Кроссбраузерный Shadow DOM из коробки (либо его эмуляция)
* Кроссбраузерная поддержка HTTP, WebSockets, Service Workers
* Не нужно ничего дополнительно настраивать. Больше никаких оберток. jQuery плагины и D3 можно * использовать на прямую
* Более современный фреймворк, чем AngularJS (на уровне React, Vue)
* Большое комьюнити

#### Минусы:

* Выше порог вхождения из-за Observable (RxJS) и Dependency Injeciton
* Чтобы все работало хорошо и быстро нужно тратить время на дополнительные оптимизации (он не супер быстрый, по умолчанию, но быстрее AngularJS во много раз)
* Если вы планируете разрабатывать большое enterprise-приложение, то в этом случае, у вас нет архитектуры из коробки - нужно добавлять Mobx, Redux, MVVM, CQRS/CQS или другой state-менеджер, чтобы потом не сломать себе мозг
* Angular-Univesal имеет много подводных камней
* Динамическое создание компонентов оказывается нетривиальной задачей

### В чем разница между AngularJS и Angular?

AngularJS является фреймворком, который может помочь вам в разработке Single Page Application. Он появился в 2009 году и с годами выяснилось, что имел много проблем. Angular (Angular 2+) же в свою очередь направлен на тоже самое, но дает больше преимуществ по сравнению с AngularJS 1.x, включая лучшую производительность, ленивую загрузку, более простой API, более легкую отладку.

#### Что появилось в Angular:

* Angular ориентирован на мобильные платформы и имеет лучшую производительность
* Angular имеет встроенные сервисы для поддержки интернационализации
* AngularJS проще настроить, чем Angular
* AngularJS использует контроллеры и $scope
* Angular имеет много способов определения локальных переменных
* В Angular новый синтаксис структурных директив (camelCase)
* Angular работает напрямую с свойства и собитиями DOM элементов
* Одностороннее связывание данных через [property]
* Двустороннее связывание данных через [(property)]
* Новый механизм DI, роутинга, запуска приложения

#### Основные преимущества Angular:

* Обратная совместимость Angular 2, 4, 5, ..
* TypeScript с улучшенной проверкой типов
* Встроенный компилятор с режимами JIT и AOT (+ cокращение кода)
* Встроенные анимации

### Что такое MVVM и в чем разница перед MVC?

MVVM - шаблон проектирования архитектуры приложения. Состоит из 3 ключевых блоков: Model, View, ViewModel.
Отличие от MVС заключаются в:

* View реагирует на действия пользователя и передает их во View Model через Data Binding.
* View Model, в отличие от контроллера в MVC, имеет осоьый механизм, автоматизирущий связь между View и связанными свойствами в ViewModel.

Привязка данных между View и ViewModel может быть односторонней или двусторонней (one-way, two-way data-binding). (Angular Template синтаксис)

### Что такое интерполяция в Angular?

Разметка интерполяции с внедренными выражениями используется в Angular для присвоение данных текстовым нодам и значения аттрибутов. Например:

```html
<a href="img/{{username}}.jpg">Hello {{username}}!</a>
```

### Какие способы использования шаблонов в Angular вы знаете?

???

### В чем разница между структурной и атрибутной директивой, назовите встроенные директивы?

* Структурные директивы влияют на DOM и могут добавлять/удалять элементы
(ng-template, NgIf, NgFor, NgSwitch, etc)
* Атрибутные директивы меняют внешний вид или поведение элементов, компонентов или других директив
(NgStyle, NgClass, etc).

### Для чего нужны директивы ng-template, ng-container, ng-content?

#### ng-template

`<template>` — это механизм для отложенного рендера клиентского контента, который не отображается во время загрузки, но может быть инициализирован при помощи JavaScript.

Template можно представить себе как фрагмент контента, сохранённый для последующего использования в документе. Хотя парсер и обрабатывает содержимое элемента template во время загрузки страницы, он делает это только чтобы убедиться в валидности содержимого; само содержимое при этом не отображается.


`<ng-template>` - является имплементацией стандартного элемента template, данный элемент появился с четвертой версии Angular, это было сделано с точки зрения совместимости со встраиваемыми на страницу template элементами, которые могли попасть в шаблон ваших компонентов по тем или иным причинам.

Пример:

```html
<div class="lessons-list" *ngIf="lessons else loading">
  ...
</div>

<ng-template #loading>
    <div>Loading...</div>
</ng-template>
```

#### ng-container

`<ng-container>` - это логический контейнер, который может использоваться для группировки узлов, но не отображается в дереве DOM как узел (node).

На самом деле структурные директивы (*ngIf, *ngFor, ..) являются синтаксическим сахаром для наших шаблонов. В реальности, данные шаблоны трансформируются в такие конструкции:

```html
<ng-template [ngIf]="lessons" [ngIfElse]="loading">
   <div class="lessons-list">
     ...
   </div>
</div>

<ng-template #loading>
    <div>Loading...</div>
</ng-template>
```

Но что делать, если я хочу применить несколько структурных директив? (спойлер: к сожалению, так нельзя сделать)

```html
<div class="lesson" *ngIf="lessons" *ngFor="let lesson of lessons">
  <div class="lesson-detail">
      {{lesson | json}}
  </div>
</div>
```

```
Uncaught Error: Template parse errors:
Can't have multiple template bindings on one element. Use only one attribute
named 'template' or prefixed with *
```

Но можно сделать так:

```html
<div *ngIf="lessons">
  <div class="lesson" *ngFor="let lesson of lessons">
    <div class="lesson-detail">
        {{lesson | json}}
    </div>
  </div>
</div>
```

Однако, чтобы избежать необходимости создавать дополнительный div, мы можем вместо этого использовать директиву ng-container:

```html
<ng-container *ngIf="lessons">
    <div class="lesson" *ngFor="let lesson of lessons">
        <div class="lesson-detail">
            {{lesson | json}}
        </div>
    </div>
</ng-container>
```

Как мы видим, директива ng-container предоставляет нам элемент, в котором мы можем использовать структурную директиву, без необходимости создавать дополнительный элемент.

Еще пара примечательных примеров, если все же вы хотите использовать ng-template вместо ng-container, по определенным правилам вы не сможете использовать полную конструкцию структурных директив.

Вы можете писать либо так:

```html
<div class="mainwrap">
    <ng-container *ngIf="true">
        <h2>Title</h2>
        <div>Content</div>
    </ng-container>
</div>
```

Либо так:

```html
<div class="mainwrap">
    <ng-template [ngIf]="true">
        <h2>Title</h2>
        <div>Content</div>
    </ng-template>
</div>
```

На выходе, при рендеринге будет одно и тоже:

```html
<div class="mainwrap">
      <h2>Title</h2>
      <div>Content</div>
</div>
```

#### ng-content

`<ng-content>` - позволяет внедрять родительским компонентам html-код в дочерние компоненты.

Здесь на самом деле, немного сложнее уже чем с ng-template, ng-container. Так как ng-content решает задачу проецирования контента в ваши веб-компоненты. Веб-компоненты состоят из нескольких отдельных технологий. Вы можете думать о Веб-компонентах как о переиспользуемых виджетах пользовательского интерфейса, которые создаются с помощью открытых веб-технологий. Они являются частью браузера и поэтому не нуждаются во внешних библиотеках, таких как jQuery или Dojo. Существующий Веб-компонент может быть использован без написания кода, просто путем импорта выражения на HTML-страницу. Веб-компоненты используют новые или разрабатываемые стандартные возможности браузера.

Давайте представим ситуацию от обратного, нам нужно параметризировать наш компонент. Мы хотим сделать так, чтобы на вход в компонент мы могли передать какие-либо статичные данные. Это можно сделать несколькими способами.

`comment.component.ts`:

```typescript
@Component({
  selector: 'comment',
  template: `
    <h1>Комментарий: </h1>
    <p>{{data}}</p>
  `
})
export class CommentComponent {
  @Input() data: string = null;
}
```

`app.component.html`

```typescript
<div *ngFor="let message of comments">
  <comment [data]="message"></comment>
</div>
```

Но можно поступить и другим путем.
`comment.component.ts`:

```typescript
@Component({
  selector: 'comment',
  template: `
    <h1>Комментарий: </h1>
    <ng-content></ng-content>
  `
})
export class CommentComponent {
}
```

`app.component.html`

```typescript
<div *ngFor="let message of comments">
  <comment>
    <p>{{message}}</p>
  </comment>
</div>
```

Конечно, эти примеры плохо демонстрируют подводные камни, свои плюсы и минусы. Но второй способ демонстрирует подход при работе, когда мы оперируем независимыми абстракциями и можем проецировать контент внутрь наших компонентов (подход веб-компонентов).

## Angular development enviroments

### Что такое директива и как создать собственную?

Директивы бывают трех видов: компонент, структуные и атрибутные (см. выше).

#### Создание атрибутных директив:

```typescript
@Directive({
   selector: '[appHighlight]'
})
export class HighlightDirective { .. }
```

Декоратор определяет селектор атрибута [appHighlight], [] - указывают что это селектор атрибута. Angular найдет каждый элемент в шаблоне с этим атрибутом и применит к ним логику директивы.

```typescript
@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
  constructor(el: ElementRef) {
     el.nativeElement.style.backgroundColor = 'yellow';
  }
}
```

Необходимо указать в конструткторе ElementRef, чтобы через его свойство nativeElement иметь прямой доступ к DOM элементу, который должен быть изменен.
Теперь, используя @HostListener, можно добавить обработчики событий, взаимодействующие с декоратором.

```typescript
@HostListener('mouseenter')
public onMouseEnter(): void {
    this.highlight('yellow');
}

@HostListener('mouseleave')
public onMouseLeave(): void {
   this.highlight(null);
}

private highlight(color: string): void {
   this.el.nativeElement.style.backgroundColor = color;
}
```

#### Структурные директивы создаются так:

Напишем UnlessDirective, которая будет противоположна NgIf.
Необходимо использовать @Directive, и импортировать Input, TemplateRef, и ViewContainerRef. Они вам понадобятся при воздании любой структурной директивы.

```typescript
import { Directive, Input, TemplateRef, ViewContainerRef } from '@angular/core';

@Directive({ selector: '[appUnless]'})
  export class UnlessDirective {
}
```

В конструкторе мы получаем доступ к viewcontainer и содержимое.

```
constructor(
    private templateRef: TemplateRef<any>,
    private viewContainer: ViewContainerRef) { }
```

Наша директива предполагает работу с true/false. Для этого нужно свойство appUnless, добавленное через @Input.

```typescript
@Input() public set appUnless(condition: boolean) {
  if (!condition && !this.hasView) {
       this.viewContainer.createEmbeddedView(this.templateRef);
       this.hasView = true;
  } else if (condition && this.hasView) {
       this.viewContainer.clear();
       this.hasView = false;
  }
}
```

### Что такое директива, компонент, модуль, сервис, пайп в Angular и для чего они нужны?

* Директива - см. выше.
* Компонент контролирует участок экрана, т.н. view.
* Сервис это класс с узкой, четко определенной целью. Это может быть значение, функция, запрос, etc. Главное в них то, что они повторно используются, отделяя чистую функциональность компонента.
* Пайп преобразует отображение значений в шаблоне, к примеру отображение дат в разных локалях или изменяют в отображении регистр строк.

### Расскажите об основных параметрах @NgModule, @Component, @Directive, @Injectable, @Pipe

Декораторы динамически подключают дополнительное поведение к объекту. Они помечают класс и предоставляют конфигурационные метаданные.

#### @NgModule может содержать следующие параметры:

* `providers` - список инжектируемых объектов, которые добавляются в этот модуль
* `declarations` - компоненты, директивы и пайпы, принадлежащие этому модулю
* `imports` - модули, которые экспортируются декларируемыми и доступны в шаблоне этого модуля
* `exports` - компоненты, директивы и пайпы, которые объявлены декларируемыми, и могут быть импользованы в шаблоне любого компонента, которые принадлежит NgModule импортирующему их.
entryComponent - компилируемые компоненты при определенни NgModule, для динамической загрузки в view.
* `bootstrap` - компоненты, которые загружаются при загрузке этого модуля, автоматически добавляются в entryComponent.
* `schemas` - набор схем, объявляющих разрешенные элементы в MgModules
* `id` - имя или путь, уникальный идентификатор этого NgModule в getModuleFactory. Если не заоплнять - не будет там зарегистрирован.
* `jit` - если true, то этот модуль будет пропущен компилятором AOT и всегда будет компилироваться JIT.

#### @Component может содержать следующие параметры:

* `changeDetection` - стратегия обнаружения изменений, используемая для этого компонента
* `viewProviders` - инжектируемые объекты, которые видны DOM children этого компонента.
* `moduleId` - id модуля, к которому относится компонент.
* `templateUrl` - относительный путь или абсолютный URL к шаблону компонента.
* `template` - инлайн шаблон для этого компонента.
* `styleUrls` - один и более путь до файла, содержащего CSS, абсолютный или относительный.
* `styles` - инлайн CSS, используемые в этом компоненте.
* `animations` - один и более вызовов анимации trigger(), содержащих state() и transistion().
* `encapsulation` - правила инкапсуляции для шаблона и CSS.
* `interpolation` - переопределение базовых знаков интерполяции.
* `entryComponents` - компоненты, которые должны быть скомпилированы вместе с этим компонентом. Для каждого упомянутого здесь компонента создается ComponentFactory и сохраняется в ComponentFactoryResolver.
* `preserveWhitespaces` - при значении true удаляются потенциально лишние пробелы из скомпилированного шаблона.

#### @Directive может содержать следующие параметры:

* `selector` - CSS-селектор, который идентифицирует эту директиву в шаблоне и запускает создание этой директивы.
* `inputs` - ?????.
* `outputs` -??????
* `providers` - настраивает инжектор этой директивы или компонента с помощью токена.
* `exportAs` - определяет имя, которое можно использовать в шаблоне для присвоения этой директивы переменной.
* `queries` - настраивает запросы, которые могут быть инжектированы в директиву.
* `host` - состоставляет свойства класса со сбайнженными элементами для свойств, атрибутов и ивентов.
* `jit` - если true, то этот модуль будет пропущен компилятором AOT и всегда будет компилироваться JIT.

#### @Injectable может содержать следующие параметры:

* `providedIn` - определяет, где будет заинжектировано, либо, если объявлено "root" растространится на все приложение.

#### @Pipe может содержать следующие параметры:

* `name` - имя пайпа, которое будет использовано в шаблоне.
* `pure` - если true, то пайп считается "чистым", и метод transform() вызовется только при изменении его входных агрументов. По умолчанию стоит true.

### Что такое динамические компоненты и как их можно использовать в Angular?

???

### Как применить анимацию к компонентам?

???

## Angular render lifecycle and core environments

### Объясните механизм загрузки (bootstrap) Angular-приложения в браузере?

???

### Как происходит взаимодействие компонентов в Angular (опишите components view)?

???

### Каков жизненный цикл у компонентов?

После создания компонента или директивы через вызов конструктора, Angular вызывает методы жизненного цикла в следующей последовательности в строго определенные моменты:
* `ngOnChanges()` - вызывается когда Angular при/переприсваивает привязанные данные к input properties. Метод получает объект SimpleChanges, со старыми и новыми значениями. Вызывается перед NgOnInit и каждый раз, когда изменяется одно или несколько связанных свойств.
* `ngOnInit()` - инициализует директиву/компонент после того, как Angular впервые отобразит связанные свойства и устанавливает входящие параметры.
* `ngDoCheck()` - при обнаружении изменений, которые Angular не может самостоятельно обнаружить, реаигрует на них.
* `ngAfterContentInit()` - вызывается после того, как Angular спроецирует внешний контент в отображение компонента или отображение с директивой. Вызывается единожды, после первого ngDoCheck().
* `ngAfterContentChecked()` - реагирует на проверку Angular-ом проецируемого содержимого. Вызывается после ngAfterContentInit() и каждый последующий ngDoCheck().
* `ngAfterViewInit()` - вызывается после инициализации отображения компонента и дочерних/директив. Вызывается единожды, после первого ngAfterContentChecked().
* `ngAfterViewChecked()` - реагирует на проверку отображения компонента и дочерних/директив. Вызывается после ngAfterViewInit() и каждый последующий ngAfterContentChecked().
* `ngOnDestroy()` - после уничтожния директивы/компонента выполняется очистка. Отписывает Observables и отключает обработчики событий, чтобы избежать утечек памяти.

### Что такое Shadow DOM и как с ним работать в Angular?

???

### Что такое Data Binding и какие проблемы связанные с ним вы знаете?

Angular поддерживает одностороннюю и двустороннюю Data Binding. Это механизм координации частей шаблона с частями компонента.

Добавление специальной разметки сообщает Angular как соединять обе стороны. Следующая диаграмма показывает четыре формы привязки данных.

Односторонние:
* От компонента к DOM с привязкой значения: {{hero.name}}
* От компонента к DOM с привязкой свойства и присвоением значения: [hero]="selectedHero"
* От DOM к компоненту с привязкой на ивент: (click)="selectHero(hero)"

Двусторонняя в основном используется в template-driven forms, сочетает в себе параметр и ивент. Вот пример, использующий привязку с директивой ngModel.

Здесь значение попадает в input из компонента, как при привязке значения, но при изменении юзером значения новое передается в компонент и переопределяется.

### Как вы используете одностороннюю и двухстороннюю привязку данных?

???

В чем преимущества и недостатки Regular DOM (Angular) перед Virtual DOM (React)?

???

### Как обновлять представление, если ваша модель данных обновляется вне 'зоны'?

#### Используя метод ApplicationRef.prototype.tick, который запустит change detection на всем дереве компонентов.

```typescript
import { Component, ApplicationRef, NgZone } from '@angular/core';

@Component({
    selector: 'app-root',
    template: `
        <h1>Hello, {{ name }}!</h1>
    `
})
export class AppComponent {

    public name: string = null;

    constructor(private app: ApplicationRef, private zone: NgZone) {
        this.zone.runOutsideAngular(() => {
            setTimeout(() => {
                this.name = window.prompt('What is your name?', 'Jake');
                this.app.tick();
            }, 5000);
        });
    }

}
```

#### Используя метод NgZone.prototype.run, который также запустит change detection на всем дереве.

```typescript
import { Component, NgZone } from '@angular/core';
import { SomeService } from './some.service'

@Component({
    selector: 'app-root',
    template: `
        <h1>Hello, {{ name }}!</h1>
    `,
    providers: [SomeService]
})
export class AppComponent {

   public name: string = null;

   constructor(private zone: NgZone, private service: SomeService) {
       this.zone.runOutsideAngular(() => {
           this.service.getName().then((name: string) => {
               this.zone.run(() => this.name = name);
           });
       });
   }

}
```

Метод `run` под капотом сам вызывает `tick`, а параметром принимает функцию, которую нужно выполнить перед `tick`. То есть:

```typescript
this.zone.run(() => this.name = name);

// идентично

this.name = name;
this.app.tick();
```

#### Используя метод ChangeDetectorRef.prototype.detectChanges, который запустит change detection на текущем компоненте и дочерних.

```typescript
import { Component, NgZone, ChangeDetectorRef } from '@angular/core';

@Component({
    selector: 'app-root',
    template: `
        <h1>Hello, {{ name }}!</h1>
    `
})
export class AppComponent {

   public name: string = null;

   constructor(private zone: NgZone, private ref: ChangeDetectorRef) {
       this.zone.runOutsideAngular(() => {
           this.name = window.prompt('What is your name?', 'Jake');
           this.ref.detectChanges();
       });
   }
}
```

### Что такое EventEmmiter и как подписываться на события?

Используется в директивах и компонентах для подписки на пользовательские ивенты синхронно или асинхронно, и регистрации обработчиков для этих ивентов.


### Что такое Change Detection, как работает Change Detection Mechanism?

#### Change Detection

Change Detection - процесс синхронизации модели с представлением. В Angular поток информации однонаправленный, даже при использовании ngModel для реализации двустороннего связывания, которая является синтаксическим сахаром поверх однонаправленного потока.

#### Change Detection Mechanism

Change Detection Mechanism - продвигается только вперед и никогда не оглядывается назад, начиная с корневого (рут) компонента до последнего. В этом и есть смысл одностороннего потока данных. Архитектура Angular приложения очень проста — дерево компонентов. Каждый компонент указывает на дочерний, но дочерний не указывает на родительский. Односторонний поток устраняет необходимость $digest цикла.

### Какие существуют стратегии обнаружения изменений?

Всего есть две стратегии - `Default` и `OnPush`. Если все компоненты используют первую стратегию, то Zone проверяет все дерево независимо от того, где произошло изменение. Чтобы сообщить Angular, что мы будем соблюдать условия повышения производительности нужно использовать стратегию обнаружения изменений `OnPush`. Это сообщит Angular, что наш компонент зависит только от входных данных и любой объект, который передается ему должен считаться immutable. Это все построено на принципе автомата Мили, где текущее состояние зависит только от входных значений.

### Сколько Change Detector'ов может быть во всем приложении?

У каждого компонента есть свой Change Detector, все Change Detector'ы наследуются от AbstractChangeDetector.

### Основное отличие constructor от ngOnInit?

Конструктор сам по себе является фичей самого класса, а не Angular. Основная разница в том, что Angular запустит ngOnInit, после того, как закончит настройку компонента, то есть, это сигнал, благодаря которому свойства @Input() и другие байндинги, и декорируемые свойства доступны в ngOnInit, но не определены внутри конструктора, по дизайну.

## Angular data flow

### Что такое Dependency Injection?

Это важный паттерн шаблон проектирования приложений. В Angular внедрение зависимостей реализовано из-под капота.
Зависимости - это сервисы или объекты, которые нужны классу для выполнения своих функций. DI -позволяет запрашивать зависимости от внешних источников.

### Что такое Singleton Service и с какой целью его используют в Angular?


Это сервисы, объявленные в приложении и имеющие один экземляр на все приложение. Его можно объявить двумя способами:

* Объявить его @Injectable(root)
* Включить его в AppModule в providers, либо в единственный модуль импортируемый в AppModule.

### Как можно определить свой обработчик ErrorHandler, Logging, Cache в Angular?

???

### Что такое Observable?

Observable — это набюдатель, который подписывается "зрелище" и реагирует на все события до момента отписки.

### В чём разница между Observable и Promise?

Promise обрабатывает одно значение по завершению асинхронной операции, вне зависимости от ее исхода, и не поддерживают отмену операции.
Observable же является потоком, и позволяет передавать как ноль, так и несколько событий, когда callback вызывается для каждого события.

### В чём разница между Observable и BehaviorSubject/Subject?

Subjects - специальные Observable. Представьте, что есть спикер с микрофоном, который выступает в комнате, полной людей. Это и есть Subjects, их сообщение передается сразу нескольким получателям. Обычные же Observables можно сравнить с разговором 1 на 1.

* `Subject` - является multicast, то есть может передавать значение сразу нескольким подписчикам.
* `BehaviorSubject` - требует начальное значение и передает текущее значение новым подпискам.

### В чём разница между switchMap, mergeMap, concatMap?

* `switchMap` - отменит подписку на Observable, возвращенный ее аргументом project, как только он снова вызовет ее в новом элементе.
* `mergeMap` - в отличие от switchMap позволяет реализовать одновременно несколько внутренних подписок.
* `concatMap` - послеждовательно обрабатывает каждое событие, в отличие от mergeMap.

## Angular with Backend integration

### Какими способами можно взаимодействовать API бекенда, что требуется для проксирования запросов?

???

### Что такое HTTP Interceptors?

Interceptor (перехватчик) - просто причудливое слово для функции, которая получает запросы / ответы до того, как они будут обработаны / отправлены на сервер. Нужно использовать перехватчики, если имеет смысл предварительно обрабатывать многие типы запросов одним способом. Например нужно для всех запросов устанавливать хедер авторизации Bearer:

`token.interceptor.ts`

```typescript
import { Injectable } from '@angular/core';
import { HttpInterceptor, HttpRequest, HttpHandler, HttpEvent } from '@angular/common/http';
import { Observable } from 'rxjs/Observable';

@Injectable()
export class TokenInterceptor implements HttpInterceptor {

    public intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
        const token = localStorage.getItem('token') as string;

        if (token) {
            req = req.clone({
                setHeaders: {
                    'Authorization': `Bearer ${token}`
                }
            });
        }

        return next.handle(req);
    }
}
```

И регистрируем перехватчик как синглтон в провайдерах модуля:

`app.module.ts`

```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { HTTP_INTERCEPTORS } from '@angular/common/http';
import { AppComponent } from './app.component';
import { TokenInterceptor } from './token.interceptor';

@NgModule({
    imports: [
        BrowserModule
    ],
    declarations: [
        AppComponent
    ],
    bootstrap: [AppComponent],
    providers: [{
        provide: HTTP_INTERCEPTORS,
        useClass: TokenInterceptor,
        multi: true // <--- может быть зарегистрирован массив перехватчиков
    }]
})
export class AppModule {}
```

### Как использовать Json Web Tokens для аутентификации при разработке на Angular?

???

### Как обрабатываются атаки XSS и CSRF в Angular?

???

## Angular routing

### Что такое роутинг и как его создать в Angular?

Роутинг позволяет реализовать навигацию от одного view приложения к другому при работе пользователя с приложением.
Это реализовано через взаимодействие с адресной строкой, Angular Router интерпретирует ее как инструкцию по переходу между view. Возможна передача параметров вспомогательному компоненту для конкретизирования предоставляемого контента. Навигация может осуществлять по ссылкам на странице, кнопкам или другим элементам, как кнопки "вперед-назад" в браузере.
Для создания роутинга первым делом необходимо импортировать "RouterModule" и "Routes" в AppModule.
Затем необходимо реализовать конфигурацию по приложению, определить path и относящие к ним компоненты, и в метод RouterModule.forRoot() передать конфигурацию.
Наконец необходимо добавить routerLink в шаблон.

### Каков жизненный цикл у Angular Router?

???

### Что такое ленивая загрузка (Lazy-loading) и для чего она используется?

???

### В чем разница между Routing и Navigation?

???

### Как загрузить данные до того как активируется роут?

???

## Angular Forms (also big ui enterprise)

### Что такое FormGroup и FormControl и для чего они используются?

* FormControl - отслеживает значение и статус валидации отдельного элемента формы.
* FormGroup - отслеживает состояние и статус валидациии группы FormControl

Они используются для создания и работы с формами.

### Что такое реактивные формы в Angular?

Реактивные формы обеспечивают управляемый моделями подход к обработке входных данных форм, значения которых могут меняться со временем. Они строятся вокруг наблюдаемых потоков, где входные данные и значения форм предоставляются в виде потоков входных значений, к которым можно получить синхронный доступ.

### Как применять валидацию для простых и сложных форм?

В реактивных формах валидация реализуется в компоненте. Есть два типа валидаторов: синхронные и асинхронные.
Можно использовать встроенные валидаторы, либо создать свои. Валидаторы доабвляются

## Build environments

### В чем разница между Angular CLI и Webpack Development Environment?

<!-- end of https://github.com/Angular-RU/angular-ru-interview-questions -->
