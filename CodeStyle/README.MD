# Стиль кода

## Именование

- Кодировка UTF-8 без [BOM](http://en.wikipedia.org/wiki/Byte-order_mark).
- Перевод строки: LF. В конце файла перевод строки **обязателен**.
- Отступ 2 пробела, знаки табуляции не применяются.
- Длина линии не должна превышать 120 символов.
- Нет лишних пробелов в конце строк (настраиваем свой текстовый редактор, чтобы он удалял лишние пробелы при сохранении).

## Именование

- `variableNamesLikeThis`
- `functionNamesLikeThis`
- `functionArgumentsLikeThis`
- `ClassNamesLikeThis`
- `methodNamesLikeThis`
- `CONSTANTS_LIKE_THIS`
- `event-like-this`
- `private` свойства и методы объектов начинаются с подчеркивания `_`
- `protected` свойства и методы объектов также начинаются с подчеркивания `_`
- Избегаем коротких или немногословных названий
- В именовании аббревиатур соблюдаем `CamelCase`. Например: `Json`, `Xml`.

## Объявление переменных

- Все переменные объявляются с `let/const`.
- Каждая переменная в пределах одной области видимости объявляется только один раз.
- Каждая переменная объявляется на новой строке. Это позволяет легко менять строки местами и подписывать к ним комментарии.
- Переменные объявляются как можно ближе к месту использования.

## Литералы

### Объекты

- После открывающей фигурной скобки и перед закрывающей пробел ставится:

```
var obj = { a: 1, b: 2, c: 3 };

this.method({ a: 1, b: 2 });
```

- Пробел перед двоеточием не ставится:

```
var obj = {
    prop: 0
};
```

- Выравнивание не используется:

**Хорошо:**

```
var obj = {
    a: 0,
    b: 1,
    lengthyName: 2
};
```

**Плохо:**

```
var obj = {
    a          : 0,
    b          : 1,
    lengthyName: 2
};
```

- Имена ключей заключаются в кавычки только по необходимости:

**Хорошо:**

```
var obj = {
    key: 0,
    'key-key': 1
};
```

**Плохо:**

```
var obj = {
    'key': 0,
    'key-key': 1
};
```

### Массивы

При объявлении массива, пробел ставится лишь после запятой:

```
var fellowship = ['foo', 'bar', 'baz'];
```

### Строки

- Строки записываются с использованием одинарных кавычек или обратных кавычек:

```
	var lyrics = 'Never gonna give you up, Never gonna let you down';
```

- Если в строке встречается одинарная кавычка, она экранируется:

```
var test = 'It shouldn\'t fail';
```

## Точка с запятой Точка с запятой ставится всегда.

## Ключевые слова

- Ключевые слова отделяются пробелом:

```
if (test) {
    // ...
}

function foo() {
    // ...
}

var bar = function () {
    // ...
};
```

- Перед точкой с запятой пробел не ставится:

```
return;
```

## Блочные инструкции

- Открывающая фигурная скобка ставится на той же строке и отделяется пробелом от предыдущей конструкции:

```
if (test) {
    // ...
}

function foo() {
    // ...
}
```

- Фигурные скобки ставятся всегда:

**Хорошо:**

```
if (test) {
    return;
}
```

**Плохо:**

```
if (test)
    return;

if (test) return;

if (test) { return; }
```

## Условные инструкции

### if

- `else` пишется на той же строке, что и закрывающая фигурная скобка

```
if (test) {
    // ...
} else {
    // ...
}
```

- Присваивание в условном выражении не используется:

**Хорошо:**

```
var foo = bar();
if (foo > 0) {
    // ...
}
```

**Плохо:**

```
var foo;
if ((foo = bar()) > 0) {
    // ...
}
```

- Выражения используются только там, где требуется значение:

**Хорошо:**

```
if (condition) {
    actionIfTrue();
} else {
    actionIfFalse();
}
```

**Плохо:**

```
condition && actionIfTrue() || actionIfFalse();
```

- Длинные условия, которые не вмещаются на одну строку, разбиваются следующим образом:

```
if (longCondition ||
    anotherLongCondition &&
    yetAnotherLongCondition
) {
    // ...
}
```

- [Yoda conditions](http://en.wikipedia.org/wiki/Yoda_conditions) не используются:

**Хорошо:**

```
if (getType() === 'driving') {

}
```

**Плохо:**

```
if ('driving' === getType()) {

}
```

### switch

```
switch (value) {
    case 1:
        // ...
        break;

    case 2:
        // ...
        break;

    default:
        // ...
        // no break keyword on the last case
}
```

## Циклы

### for По возможности вместо `for` используется [Array.prototype.forEach](https://developer.mozilla.org/ru/docs/JavaScript/Reference/Global_Objects/Array/forEach):

```
[1, 2, 3].forEach(function (value) {
    console.log(value);
});
```

Код с использованием `forEach` проще читать (легче абстрагироваться от того, что происходит в каждой итерации). Где критична скорость используется обычный `for`.

### for (var i in obj) По возможности вместо `for-in` используется [Object.keys](https://developer.mozilla.org/ru/docs/JavaScript/Reference/Global_Objects/Object/keys):

```
Object.keys(obj).forEach(function (key) {
    console.log(key);
});
```

## Операторы

### with

Оператор `with` не используется.

### Оператор равенства Всегда используется строгое равенство `===` (неравенство `!==`), если нет необходимости в приведении типов.

### Тернарный оператор

```
var x = a ? b : c;

var y = a ?
    longButSimpleOperandB : longButSimpleOperandC;

var z = a ?
    moreComplicatedB :
    moreComplicatedC;
```

### Унарный оператор Все унарные операторы пишутся слитно с операндами:

```
var foo = !bar;
```

## eval Избегаем использования `eval`. Для парсинга `json` используется [JSON.parse](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Global_Objects/JSON/parse).

## undefined

Проверяем значение через строгое сравнение.

**Хорошо:**

```
x === undefined;
```

**Плохо:**

```
// в современных браузерах уже определен immutable undefined.
var undefined;
x === undefined;

// больше писать
typeof x === 'undefined'

x === void 0
```

## Круглые скобки

- Ставятся, если только это необходимо синтаксисом или семантикой.
- Не используются с унарными операторами `delete`, `typeof` и `void`, а также ключевыми словами `return`, `throw`, `new`.

## Исключения

Создаём исключения с помощью `new Error`:

**Хорошо:**

```
throw new Error('msg');
```

**Плохо:**

```
throw 'msg';
```

## Приведение типов в сложных выражениях

Используются явные приведения типов ***в сложных выражениях***:

**Хорошо:**

```
Boolean(foo)
Number(bar)
String(baz)
[].indexOf(qux) === -1 или [].indexOf(qux) < 0
```

**Плохо:**

```
!!foo
+bar
baz + ''
~[].indexOf(qux)
```

## Переносы строк

- Максимальная длина строки `120` символов, если строка выходит длиннее, то по возможности делаются переносы строки, с соответствующими отступами после переноса.
- Операторы размещаются на предыдущей строке:

```
var debt = this.calculateBaseDebt() + this.calculateSharedDebt() + this.calculateDebtPayments() +
    this.calculateDebtFine();
```

- Закрывающие скобки не прижимаются к переносимому коду:

**Хорошо:**

```
DoSomethingThatRequiresALongFunctionName(
    veryLongArgument1,
    argument2,
    argument3,
    argument4
);
anotherStatement;
```

**Плохо:**

```
DoSomethingThatRequiresALongFunctionName(
    veryLongArgument1,
    argument2,
    argument3,
    argument4);
anotherStatement;
```

## Цепочки вызовов

- При переносе вызова функции на новую строку:
    - Оператор доступа к свойству `.` ставится на новой строке.
    - Добавляется отступ относительно объекта, у которого вызывается функция.

**Хорошо**:

```
someObject
    .operation()
    .operationWithCallback(function (obj) {
        obj.processed = true;
    })
   .end();
```

**Плохо**:

```
someObject.
   start().
   end();

someObject
.start()
.end();
```

## Пустые линии Могут использоваться для логической группировки частей кода:

```
doSomethingTo(x);
doSomethingElseTo(x);
andThen(x);

nowDoSomethingWith(y);

andNowWith(z);
```

## Контекст функции

- Рекомендуется использовать `Function.prototype.bind`:

```
doAsync(function () {
    this.fn();
}.bind(this));
```

- Если функция позволяет передать `this` параметром, используем его:

**Хорошо:**

```
[1, 2, 3].forEach(function (n) {
    this.fn(n);
}, this);
```

**Плохо:**

```
[1, 2, 3].forEach(function (n) {
    this.fn(n);
}.bind(this));
```

- Если используется переменная, называем ее `_this`:

```
var _this = this;
doAsync(function () {
    _this.fn();
});
```

## node.js

### Импортирование модулей

- Все модули импортируются в начале файла сразу после описания к нему, если оно есть:

**Хорошо:**

```
var http = require('http');
var fs = require('fs');

// code here
```

**Плохо:**

```
var http = require('http');

// code here

var fs = require('fs');

// code here
```

Исключение: модули, импортируемые по требованию.

- Импорты должны быть сгруппированы в следующем порядке:
1. стандартные модули node.js
2. модули сторонних библиотек
3. модули вашего приложения