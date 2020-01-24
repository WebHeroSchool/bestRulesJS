#  JavaScript Style Guide

#### 1) Не используйте var

```
// badvar example = 42;
// goodlet example = 42;
```

#### 2) Отдавайте предпочтение стрелочным функциям

```
// bad
[1, 2, 3].map(function (x) {
  const y = x + 1;
  return x * y;
});

// good
[1, 2, 3].map((x) => {
  const y = x + 1;
  return x * y;
});
```

#### 3) Используйте шаблонные строки вместо конкатенации

```
// bad
function sayHi(name) {
  return 'How are you, ' + name + '?';
}

// bad
function sayHi(name) {
  return ['How are you, ', name, '?'].join();
}

// bad
function sayHi(name) {
  return `How are you, ${ name }?`;
}

// good
function sayHi(name) {
  return `How are you, ${name}?`;
}
```

#### 4) Не используйте eval()

```
// badlet obj = { a: 20, b: 30 };
let propName = getPropName();  // returns "a" or "b"
eval( 'var result = obj.' + propName );

// good
let obj = { a: 20, b: 30 };
let propName = getPropName();  // returns "a" or "b"
let result = obj[ propName ];  //  obj[ "a" ] is the same as obj.a
```

#### 5) Одна переменная за раз

> Каждое объявление локальной переменной объявляет только одну переменную: такие объявления, как let a = 1, b = 2; не используются.

```
// badlet a = 1, b = 2, c = 3;// goodlet a = 1;let b = 2;let c = 3;
```

#### 6) Используйте одинарные кавычки, а не двойные

> Обычные строковые литералы разделяются одинарными кавычками (‘), а не двойными (“).
>
> Совет: если строка содержит символ одинарной кавычки, попробуйте использовать шаблонные строки, чтобы не экранировать кавычки.

```
// bad
let directive = "No identification of self or mission."
// bad
let saying = 'Say it ain\u0027t so.';
// good
let directive = 'No identification of self or mission.';
// good
let saying = `Say it ain't so`;
```

#### 7) Точка с запятой — ОБЯЗАТЕЛЬНА

> Каждая инструкция должна заканчиваться точкой с запятой. Использование автоматической вставки точки с запятой запрещено.

```
// bad
let luke = {}
let leia = {}
[luke, leia].forEach(jedi => jedi.father = 'vader')
// good
let luke = {};
let leia = {};
[luke, leia].forEach((jedi) => {
  jedi.father = 'vader';
});
```

#### 8) Не используйте модули ES6 (пока)

> Пока не используйте модули ES6 (т.е. ключевые слова экспорта и импорта), так как их семантика ещё не завершена. Обратите внимание, что эта политика будет пересмотрена, как только семантика будет полностью стандартизирована.

```
// Don't do this kind of thing yet:

//------ lib.js ------
export function square(x) {
    return x * x;
}
export function diag(x, y) {
    return sqrt(square(x) + square(y));
}

//------ main.js ------
import { square, diag } from 'lib';
```

#### 9) Горизонтальное выравнивание не рекомендуется (но и не запрещается)

> Такая практика допустима, но, в целом, не рекомендуется «стилем» Google. Не следует продолжать горизонтальное выравнивание даже в местах, где оно уже применялось.

Горизонтальное выравнивание — это практика добавления дополнительных пробелов в коде, чтобы определённые значения, отображались непосредственно под другими значениями в предыдущих строках.

```
// bad
{
  tiny:   42,  
  longer: 435, 
};
// good
{
  tiny: 42, 
  longer: 435,
};
```

#### 10) Используйте шаблонные строки вместо конкатенации.

> Используйте шаблонные строки (разделённые символом `) вместо конкатенации комплексных строк, особенно если используется несколько строковых литералов. Шаблонные строки могут занимать несколько строк.

```
// bad
function sayHi(name) {
  return 'How are you, ' + name + '?';
}

// bad
function sayHi(name) {
  return ['How are you, ', name, '?'].join();
}

// bad
function sayHi(name) {
  return `How are you, ${ name }?`;
}

// good
function sayHi(name) {
  return `How are you, ${name}?`;
}
```

