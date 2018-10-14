# OOJS: Цветочный сад


## Введение
Требуется построить JavaScript объекты: сад как объект, содержащий массив цветов
цветов.

### Объекты JavaScript
Требуется построить объекты с использованием трех приемов: 
1. используя синтаксис `объект-литерал`
2. используя `prototype`
3. используя `class` из ES6


**Синтаксис объект-литерал**. Когда нам нужно только один экземпляр
объекта, удобно использовать синтаксис объект-литерал. Требуется
”буквально” записать объект, который мы хотим получить в конце, с
описанием свойств и ценностей объекта. На первом рисунке
требуется создать человека с именем и фамилией. Также надо добавить метод, чтобы
чтобы соединить это в полное имя.

```js
let person = {
 firstName: "Kweku",
 lastName: "White",
 fullName: function() {
   return this.firstName + " " + this.lastName;
 }
}
person.firstName;
// => "Kweku"
person.fullName();
// => "Kweku White"
```
*Рисунок 1*. Использование синтаксиса объект-литерал для представление человека как
объект JavaScript.

***Конструктор***. Если нам нужно создать тестовый объект с похожим
поведением и значениями, мы можем записать его с помощью конструктора.
Конструктор определяет класс с помощью метода инициализации, который
настраивает объекты. Использование конструктора, позволяет нам делить
свойства и методы среди объектов через прототип конструктора, которые являются общими для всех экземпляров этого класса.
На втором рисунке мы используем конструктор, чтобы создать двух
людей с теми же атрибутами и поведением что и на "Рисунок 1". Конструктор
`Person()` настраивает атрибуты, которые уникальны для каждого экземпляра:
имя и фамилия. Полное имя составляется при помощи метода прототипа `Person.prototype`.

```js
let Person = function(firstName, lastName) {
 this.firstName = firstName;
 this.lastName = lastName;
}
Person.prototype.fullName = function() {
 return this.firstName + " " + this.lastName
}
let grayson = new Person("Grayson", "Arthur");
grayson.firstName;
// => "Grayson"
let warner = new Person("Warner", "Constable");
warner.fullName();
// => "Warner Constable"
```
*Рисунок 2*. Использование конструктора для представления людей как объекты JavaScript.

***ES6 - Class***
Начиная с ES6 все стало намного проще, так как появилась возможность объявлять классы, как это делается в большинстве объектно-ориентированных языках программирования. Рассмотрим тот же пример, но с использованием новой конструкции.

```js
class Person{
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }

  
  fullName() {
    return this.firstName + " " + this.lastName
  }

let grayson = new Person("Grayson", "Arthur");
grayson.firstName;
// => "Grayson"
let warner = new Person("Warner", "Constable");
warner.fullName();
// => "Warner Constable"
```
*Рисунок 3*. Использование `Class` для представления людей как объекты JavaScript.



### Тестирование Jasmine
Для тестирования требуется использовать Jasmine [Jasmine][]. Основные методы, используемые в Jasmine: `describe()`, `it()`, `expect()`, и другие.
Если мы хотим установить настройки перед каждым тестом,
нужно использовать `beforeEach()` и/или `beforeAll()`. Когда мы вызываем функцию `describe ()`, мы передаем анонимную функцию, содержащую фактические тесты. На Рисунках 3 показан тест, написанный в Jasmine.

```js
describe("a string with my name", function() {
  let myName;
  beforeEach(function() {
    myName = "Carson Hollands";
  });

  it("is my name", function() {
    expect(myName).toEqual("Carson Hollands");
  });

});
```

*Рисунок 4.* Тестирование значения объекта строки JavaScript с помощью Jasmine.
   
## Releases
### Pre-release: Проверка и выполнение тестов
У нас есть набор тестов, которые будут направлять нас, пока мы
разрабатываем наши объекты сада и цветов; тестовые файлы расположены в
папке " spec/". Чтобы запустить тесты, нужно открыть ' SpecRunner.файл
html в браузере. Откройте Spec runner. 

### Release 0: Цветы
Наши объекты цветов просты. Каждый цветок имеет два атрибута: название
и цвет. Мы создадим экземпляр flower с помощью функции конструктора`Flower ()`, которая была определена в файле `src/flower.js`.
Тесты на цветы не были написаны. Напишите тесты, демонстрирующие, что
наша функция конструктора создает объекты с правильными именами и
цветами. Затем обновите функцию конструктора `Flower ()`, чтобы пройти
тесты.
*Примечание:* Следуйте примеру на Рисунке 4, чтобы написать тесты Jasmine.

### Release 1: Сад
Начните с создания объекта сада. В файле `src/garden.js`  есть переменная `garden`, значение которой является [литералом](https://ru.wikipedia.org/wiki/%D0%9B%D0%B8%D1%82%D0%B5%D1%80%D0%B0%D0%BB_(%D0%B8%D0%BD%D1%84%D0%BE%D1%80%D0%BC%D0%B0%D1%82%D0%B8%D0%BA%D0%B0)) объекта без свойств.
Используйте тесты для добавления нужных свойств в сад. Некоторые из
свойств будут атрибутами, такими как имя и местоположение. Другие
свойства будут примерами поведения как засаживать цветки.

### Release 2: Class
Теперь перепишите цветы и сад с использованием `Class` в стиле ES6.



[object literal syntax]: http://www.dyn-web.com/tutorials/object-literal/
[Объектно-ориентировнный подход]: https://developer.mozilla.org/enUS/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript
