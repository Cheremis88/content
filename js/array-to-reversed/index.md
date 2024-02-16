---
title: "`.toReversed()`"
description: "Возвращает массив с измененным порядком элементов."
authors:
  - vitya-ne
related:
  - js/arrays
  - js/array-reverse
tags:
  - doka
---

## Кратко

Метод `toReversed()` возвращает новый массив, в котором порядок всех элементов будет противоположен порядку в исходном массиве: первый элемент станет последним, а последний первым.

## Пример

```js
const planets = ['Меркурий', 'Венера', 'Земля', 'Марс']

const reversedPlanets = planets.toReversed()

console.log(reversedPlanets)
// ['Марс', 'Земля', 'Венера', 'Меркурий']

console.log(planets) // исходный массив не изменился
// ['Меркурий', 'Венера', 'Земля', 'Марс']

```

## Как пишется

`Array.toReversed()` не имеет аргументов.

`Array.toReversed()` возвращает новый массив, в котором порядок всех элементов будет противоположен порядку в исходном массиве.


## Как понять

Массивы уже имеют метод `reverse()` для получения массива с обратным порядком элементов. В отличие от него, метод `toReversed()` не изменяет исходный массив.

Потренируемся на кошках:

```js
const cats = ['Мурка', 'Кузя', 'Мурр', 'Чеширский кот']

console.log(cats.toReversed())
// ['Чеширский кот', 'Мурр', 'Кузя', 'Мурка']

console.log(cats) // исходный массив не изменился
// ['Мурка', 'Кузя', 'Мурр', 'Чеширский кот']

```

При использовании метода `reverse()` исходный массив тоже изменяется:

```js
const cats = ['Мурка', 'Кузя', 'Мурр', 'Чеширский кот']

// перевернем массив используя reverse()
console.log(cats.reverse())
// ['Чеширский кот', 'Мурр', 'Кузя', 'Мурка']

console.log(cats) // исходный массив изменился!
// ['Чеширский кот', 'Мурр', 'Кузя', 'Мурка']

```

Если элементы исходного массива являются объектами, то возвращаемый в результате работы метода `toReversed()` массив будет содержать ссылки, а не новые объекты. Таким образом, изменения объекта в исходном массиве будут видны в созданном массиве и наоборот:

```js
const versions = [{name: 'ES6'}, {name:'ES2016'}, {name: 'ES2017'}]

const result = versions.toReversed();
console.log(result)
// [{ name: 'ES2017'}, {name: 'ES2016'}, {name: 'ES6'}]

// изменим элемент исходного массива
versions[0].year = 2015

console.log(versions)
// [{name: 'ES6', year: 2015}, {name: 'ES2016'}, {name: 'ES2017'}]

// изменение так же видны в созданном массиве
console.log(result)
// [{ name: 'ES2017'}, {name: 'ES2016'}, {name: 'ES6', year: 2015}]
```

Подробнее об особенностях копирования объектов можно прочитать в статье [Поверхностное и глубокое копирование (shallow copy) элементов](/js/shallow-or-deep-clone/).

## Подсказки

💡 Если массив имеет незаполненные элементы, то `toReversed()` вернёт `undefined` как значение для всех незаполненных элементов:

```js
const poets = ['Эмили Дикинсон']

poets[3] = 'Роберт Фрост'
console.log(poets)
// ['Эмили Дикинсон', <2 empty items>, 'Роберт Фрост']

console.log(poets.toReversed())
// ['Роберт Фрост', undefined, undefined, 'Эмили Дикинсон']

```

💡 Поддержка метода `toReversed()` в основных браузерах и в Node.js появилась сравнительно недавно. Например, попытка использовать `toReversed()` в Node.js v.18.19.0 приведёт к ошибке:

```js
try {
console.log([1, 2, 3].toReversed())
} catch (err) {
  console.log('Поймали ошибку! Вот она: ', err.message)
}
// Поймали ошибку! Вот она: [1,2,3].toReversed is not a function

```