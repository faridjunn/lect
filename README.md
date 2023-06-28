Объекты JavaScript
=
#### Реальные объекты, свойства и методы
В реальной жизни машина — это объект .

Автомобиль имеет такие свойства , как вес и цвет, а также такие методы , как запуск и остановка:
- car.name = Fiat
car.model = 500
car.weight = 850kg
car.color = белый	
car.start()
car.drive()
car.brake()
car.stop()

Все автомобили имеют одинаковые свойства , но значения свойств различаются от автомобиля к автомобилю.

Все автомобили имеют одинаковые методы , но методы выполняются в разное время .
- let car = "Fiat";

Объекты тоже переменные. Но объекты могут содержать множество значений.
Этот код присваивает множество значений (Fiat, 500, белый) переменной car :
- const car = {type:"Fiat", model:"500", color:"white"};

Значения записываются в виде пар имя:значение (имя и значение разделены двоеточием).
Общепринятой практикой является объявление объектов с помощью ключевого слова const .

###### Определение объекта
Вы определяете (и создаете) объект JavaScript с литералом объекта:
Пример:
- const person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};

Пробелы и переносы строк не важны. Определение объекта может занимать несколько строк:
Пример:
- const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};

###### Свойства объекта
Пары имя:значения в объектах JavaScript называются свойствами :
- Свойство   => 	Стоимость имущества
- имя        =>    	Джон
- фамилия  	 =>     Доу
- возраст	 =>     50
- цвет глаз	 =>     синий

####### Доступ к свойствам объекта
Вы можете получить доступ к свойствам объекта двумя способами: 
1. objectName.propertyName
или
2. objectName["propertyName"]

Пример1: person.lastName;
Пример2: person["lastName"];
Объекты JavaScript — это контейнеры для именованных значений, называемых свойствами.

######  Методы объекта
Объекты также могут иметь методы .
Методы — это действия , которые можно выполнять над объектами.
Методы хранятся в свойствах как определения функций .
- Свойство   =>	 Стоимость имущества
- имя	     =>  Джон
- фамилия	 =>  Доу
- возраст  	 =>  50
- цвет глаз  =>	 синий
- полное имя =>	 function() {возвратите this.firstName + " " + this.lastName;}

Метод — это функция, хранимая как свойство.
Пример:
- const person = {
  firstName: "John",
  lastName : "Doe",
  id       : 5566,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};

В приведенном выше примере thisотносится к объекту person .
IE this.firstName означает свойство firstName этого .
IE this.firstName означает свойство firstName человека .

Object.entries()
=
Object.entries()метод представляет собой совокупность перечисляемых свойств множества объектов в формате [key, value], в том же порядке, что и в цикле for...in(разница в томе, что for-in перечисляет свойства из прототипов). Порядок элементов в массиве, который возвращается, Object.entries()не зависит от того, как объект объявляет. Если существует требование в установленном порядке, то должно быть отсортировано до вызова метода, например Object.entries(obj).sort((a, b) => a[0] - b[0]);.

###### Интерактивный пример
- const object1 = {
  a: 'somestring',
  b: 42
};
for (const [key, value] of Object.entries(object1)) {
  console.log(`${key}: ${value}`);
}
// Expected output:
// "a: somestring"
// "b: 42"

Объект, перечисленные свойства возвращаются в виде массива [key, value].
###### Описание
Object.entries()возвращаются, массивы, которые являются массивами, время от времени перечисляемому свойству [key, value],найденной прямо в object. Порядок свойств тот же, что и при прохождении циклом по свойствам объекта вручную.
Примеры:
- var obj = { foo: "bar", baz: 42 };
console.log(Object.entries(obj)); // [ ['foo', 'bar'], ['baz', 42] ]

- // массив как объект
var obj = { 0: 'a', 1: 'b', 2: 'c' };
console.log(Object.entries(obj)); // [ ['0', 'a'], ['1', 'b'], ['2', 'c'] ]

- // массив как объект c random сортировкой ключей
var an_obj = { 100: 'a', 2: 'b', 7: 'c' };
console.log(Object.entries(an_obj)); // [ ['2', 'b'], ['7', 'c'], ['100', 'a'] ]

- // getFoo is property which isn't enumerable
var my_obj = Object.create({}, { getFoo: { value: function() { return this.foo; } } });
my_obj.foo = "bar";
console.log(Object.entries(my_obj)); // [ ['foo', 'bar'] ]

- // non-object argument will be coerced to an object
console.log(Object.entries("foo")); // [ ['0', 'f'], ['1', 'o'], ['2', 'o'] ]
- // returns an empty array for any primitive type, since primitives have no own properties
console.log(Object.entries(100)); // [ ]

- // iterate through key-value gracefully
const obj = { a: 5, b: 7, c: 9 };
for (const [key, value] of Object.entries(obj)) {
  console.log(`${key} ${value}`); // "a 5", "b 7", "c 9"
}

- // Or, using array extras
Object.entries(obj).forEach(([key, value]) => {
  console.log(`${key} ${value}`); // "a 5", "b 7", "c 9"
});

##### Object. keys()
Сводка
Метод Object.keys() возвращает массив из собственных перечисляемых свойств переданного объекта, в том же порядке, в котором они бы обходились циклом for...in (разница между циклом и методом в том, что цикл перечисляет свойства и из цепочки прототипов).
###### Описание
Метод Object.keys возвращает массив строковых элементов, соответствующих именам перечисляемых свойств, найденных непосредственно в самом объекте. Порядок свойств такой же, как и при ручном перечислении свойств в объекте через цикл.

Примеры:
- var arr = ['a', 'b', 'c'];
console.log(Object.keys(arr)); // консоль: ['0', '1', '2']

- // Массивоподобный объект
var obj = { 0: 'a', 1: 'b', 2: 'c' };
console.log(Object.keys(obj)); // консоль: ['0', '1', '2']

- // Массивоподобный объект со случайным порядком ключей
var an_obj = { 100: 'a', 2: 'b', 7: 'c' };
console.log(Object.keys(an_obj)); // консоль: ['2', '7', '100']

- // Свойство getFoo является не перечисляемым свойством
var my_obj = Object.create({}, { getFoo: { value: function() { return this.foo; } } });
my_obj.foo = 1;
console.log(Object.keys(my_obj)); // консоль: ['foo']

Если вы хотите увидеть все свойства, а не только перечисляемые, смотрите метод [Object.getOwnPropertyNames()](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertyNames).

###### Object. values()
Статический Object.values()метод возвращает массив собственных перечислимых значений свойств данного объекта со строковыми ключами.
- const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};
console.log(Object.values(object1));
// Expected output: Array ["somestring", 42, false]

##### Описание
Object.values()возвращает массив, элементы которого являются значениями перечисляемых свойств со строковыми ключами, найденных непосредственно в object. Это то же самое, что итерация с помощью for...inцикла, за исключением того, что for...inцикл также перечисляет свойства в цепочке прототипов. Порядок возвращаемого массива Object.values()такой же, как и в for...inцикле.

Если вам нужны ключи свойств, используйте Object.keys()вместо них. Если вам нужны как ключи свойств, так и значения, используйте Object.entries()вместо них.

Примеры:
- const obj = { foo: "bar", baz: 42 };
console.log(Object.values(obj)); // ['bar', 42]

- // Array-like object
const arrayLikeObj1 = { 0: "a", 1: "b", 2: "c" };
console.log(Object.values(arrayLikeObj1)); // ['a', 'b', 'c']

- // Array-like object with random key ordering
// When using numeric keys, the values are returned in the keys' numerical order
const arrayLikeObj2 = { 100: "a", 2: "b", 7: "c" };
console.log(Object.values(arrayLikeObj2)); // ['b', 'c', 'a']

- // getFoo is a non-enumerable property
const myObj = Object.create(
  {},
  {
    getFoo: {
      value() {
        return this.foo;
      },
    },
  },
);
myObj.foo = "bar";
console.log(Object.values(myObj)); // ['bar']

###### this
Ключевое слово функции thisведет себя в JavaScript немного иначе, чем в других языках. Он также имеет некоторые различия между строгим режимом и нестрогим режимом.

В большинстве случаев значение thisопределяется тем, как вызывается функция (привязка во время выполнения). Его нельзя установить путем присваивания во время выполнения, и он может быть другим при каждом вызове функции. Метод bind()может установить значение функции thisнезависимо от того, как она вызывается , а стрелочные функции не предоставляют свою собственную thisпривязку (она сохраняет thisзначение окружающего лексического контекста).
- const test = {
  prop: 42,
  func: function() {
    return this.prop;
  },
};
console.log(test.func());
// Expected output: 42

###### Описание
Значение thisзависит от того, в каком контексте оно появляется: функции, класса или глобального.
- function getThis() {
  return this;
}
const obj1 = { name: "obj1" };
const obj2 = { name: "obj2" };
obj1.getThis = getThis;
obj2.getThis = getThis;
console.log(obj1.getThis()); // { name: 'obj1', getThis: [Function: getThis] }
console.log(obj2.getThis()); // { name: 'obj2', getThis: [Function: getThis] }

###### Date
Объекты JavaScript Dateпредставляют один момент времени в независимом от платформы формате. Dateобъекты инкапсулируют целое число, которое представляет миллисекунды с полуночи в начале 1 января 1970 года по всемирному координированному времени (эпоха ) .
- console.log(new Date(8.64e15).toString()); // "Sat Sep 13 275760 00:00:00 GMT+0000 (Coordinated Universal Time)"
console.log(new Date(8.64e15 + 1).toString()); // "Invalid Date"

Существуют различные методы, которые позволяют вам взаимодействовать с отметкой времени, хранящейся в дате:
- Вы можете напрямую взаимодействовать со значением метки времени, используя методы [getTime()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getTime) и [setTime()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setTime).
- Методы [valueOf()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/valueOf) and [@@toPrimitive]()(при передаче "number") — которые автоматически вызываются при приведении числа — возвращают метку времени, заставляя Dateобъекты вести себя как их метки времени при использовании в числовых контекстах.
- Все статические методы ( [Date.now()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/now), [Date.parse()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/parse) и [Date.UTC()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/UTC)) вместо Dateобъектов возвращают метки времени.
- Конструктор [Date()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/Date) можно вызвать с отметкой времени в качестве единственного аргумента.