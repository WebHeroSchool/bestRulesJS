#  JavaScript Style Guide



#### 1) Используйте === вместо ==

> В JavaScript существует два разных типа операций сравнения: === / !== и == / !=. Считается хорошим тоном всегда использовать первую пару для сравнения.

```
0 == "";        // true
1 == "1";       // true
1 == true;      // true

0 === "";       // false
1 === "1";      // false
1 === true;     // false

```



#### 2)  Переместите скрипты вниз страницы

> Основная цель этого совета — заставить страницу грузиться как можно быстрее. Когда браузер грузит скрипт он не продолжит рендеринг пока весь файл не будет загружен. Таким образом пользователю придется ждать дольше.
> Если ваши JS скрипты служать для добавления функционала — например, обработки кликов кнопки то вам стоит перенести скрипты вниз поставив их перед закрывающимся тегом body.

```
<p>And now you know my favorite kinds of corn. </p>  
<script type="text/javascript" src="path/to/file.js"></script>  
<script type="text/javascript" src="path/to/anotherFile.js"></script>  
</body>  
</html>
```



#### 3) Уберите „language“

Давным-давно это не было редкой практикой использования аттрибута language у тега script.

```
<script type="text/javascript" language="javascript">  
...  
</script> 
```

Сейчас же он считается устаревшим. Избавьтесь от него.



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



#### 9)  Используйте {} вместо New Object()

Есть несколько путей для создания объектов в JavaScript. Возможно наиболее традиционный это использование конструктора «new», например

```
var o = new Object();  
o.name = 'Jeffrey';  
o.lastName = 'Way';  
o.someFunction = function() {  
   console.log(this.name);  
}  
```

Хотя этот метод получил штамп «плохой практики» он таковой не является. Вместо него, я рекомендую использовать более надежный метод c литералом объекта.

```
var o = {  
   name: 'Jeffrey',  
   lastName = 'Way',  
   someFunction : function() {  
      console.log(this.name);  
   }  
};  
```



#### 10) Используйте [] вместо new Array()

**Нормально**

```
var a = new Array();  
a[0] = "Joe";  
a[1] = 'Plumber';  
```

**Лучше**

```
var a = ['Joe','Plumber'];  
```

