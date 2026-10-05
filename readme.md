# Жаргон функционального программирования

Функциональное программирование (ФП) предоставляет много преимуществ, и, как следствие, его популярность растет. Однако, каждая парадигма программирования имеет собственный уникальный жаргон и ФП не исключение. Цель этого словаря терминов - облегчить изучение ФП.

Примеры написаны на JavaScript (ES2015). [Почему JavaScript?](https://github.com/hemanth/functional-programming-jargon/wiki/Why-JavaScript%3F)

Где уместно, в этом документе используются термины, определенные в [Fantasy Land spec](https://github.com/fantasyland/fantasy-land).

> 🌐 **Интерактивный граф**: [hemanth.github.io/functional-programming-jargon](https://hemanth.github.io/functional-programming-jargon)
> 🤖 **Спецификация агента / LLM**: [hemanth.github.io/functional-programming-jargon/llms.txt](https://hemanth.github.io/functional-programming-jargon/llms.txt)

__Содержание__
<!-- RM(noparent,notop) -->

- [Arity / Арность](#arity)
- [Higher-Order Function (HOF) / Функция более высокого порядка](#higher-order-function-hof)
- [Closure / Замыкание](#closure)
- [Partial Application / Частичное применение](#partial-application)
- [Currying / Каррирование](#currying)
- [Auto Currying / Автокаррирование](#auto-currying)
- [Function Composition / Композиция функций](#function-composition)
- [Continuation / Продолжение](#continuation)
- [IO](#io)
- [Trampoline / Трамплин](#trampoline)
- [Thunk](#thunk)
- [Algebraic Effects / Алгебраические эффекты](#algebraic-effects)
- [Pure Function / Чистая функция](#pure-function)
- [Side effects / Сторонние эффекты](#side-effects)
- [Idempotence / Идемпотентность](#idempotence)
- [Point-Free Style / Беспараметрический стиль](#point-free-style)
- [Predicate / Предикат](#predicate)
- [Contract / Контракт](#contract)
- [Category / Категория](#category)
- [Semigroupoid / Полугруппа](#semigroupoid)
- [Value / Значение](#value)
- [Constant / Константа](#constant)
  - [Constant Function / Константная функция](#constant-function)
  - [Constant Functor / Константная функтор](#constant-functor)
  - [Constant Monad / Константная монада](#constant-monad)
- [Functor / Функтор](#functor)
- [Pointed Functor / Пунктированный функтор](#pointed-functor)
- [Lift / Поднятие](#lift)
- [Referential Transparency / Ссылочная прозрачность](#referential-transparency)
- [Equational Reasoning / Рассуждение на основе равенств](#equational-reasoning)
- [Memoization / Мемоизация](#memoization)
- [Lambda / Лямбда](#lambda)
- [Lambda Calculus / Лямбда-исчисление](#lambda-calculus)
- [Functional Combinator / Функциональный комбинатор](#functional-combinator)
- [Lazy evaluation / Ленивое вычисление](#lazy-evaluation)
- [Monoid / Моноид](#monoid)
- [Monad / Монада](#monad)
- [Comonad / Комонада](#comonad)
- [Kleisli Composition / Композиция Клейсли](#kleisli-composition)
- [Free Monad / Свободная монада](#free-monad)
- [Monad Transformer / Трансформер монад](#monad-transformer)
- [Applicative Functor / Аппликативный функтор](#applicative-functor)
- [Bifunctor / Бифунктор](#bifunctor)
- [Contravariant Functor / Контравариантный функтор](#contravariant-functor)
- [Profunctor / Профунктор](#profunctor)
- [Alternative / Альтернатива](#alternative)
- [Morphism / Морфизм](#morphism)
  - [Homomorphism / Гомоморфизм](#homomorphism)
  - [Endomorphism / Эндоморфизм](#endomorphism)
  - [Isomorphism / Изоморфизм](#isomorphism)
  - [Catamorphism / Катаморфизм](#catamorphism)
  - [Anamorphism / Анаморфизм](#anamorphism)
  - [Hylomorphism / Гиломорфизм](#hylomorphism)
  - [Paramorphism / Параморфизм](#paramorphism)
  - [Apomorphism / Апоморизм](#apomorphism)
- [Natural Transformation / Естественное преобразование](#natural-transformation)
- [Setoid / Сетоид](#setoid)
- [Semigroup / Полугруппа](#semigroup)
- [Foldable / Свертка](#foldable)
- [Traversable / Проходимый](#traversable)
- [Lens / Линза](#lens)
- [Prism / Призма](#prism)
- [Iso](#iso)
- [Traversal / Обход](#traversal)
- [Type Signatures / Сигнатуры типов](#type-signatures)
- [Algebraic data type / Алгебраический тип данных](#algebraic-data-type)
  - [Sum type / Тип-сумма](#sum-type)
  - [Product type / Тип-произведение](#product-type)
- [Option / Опция](#option)
- [Either / Или](#either)
- [Function / Функция](#function)
- [Partial function / Частичная функция](#partial-function)
  - [Dealing with partial functions / Работа с частичными функциями](#dealing-with-partial-functions)
- [Total function / Полная функция](#total-function)
- [Библиотеки функционального программирования на JavaScript](#библиотеки-функционального-программирования-на-javascript)

<!-- /RM -->

## Arity

__Арность__

Количество аргументов, принимаемых функцией. От слов, вроде "унарный", "бинарный", "тернарный" и т.п.

```javascript
const sum = (a, b) => a + b
// Арность sum - 2 (бинарный)
const inc = a => a + 1
// Арность inc - 1 (унарный)
const zero = () => 0
// Арность zero - 0 (нульарный)
```

__Дополнительные материалы__

* [Арность](https://ru.wikipedia.org/wiki/%D0%90%D1%80%D0%BD%D0%BE%D1%81%D1%82%D1%8C) в Википедии

## Higher-Order Function (HOF)

__Функция более высокого порядка__

Функция, принимающая другую функцию в качестве аргумента и/или возвращающая функцию:

```javascript
const filter = (predicate, xs) => xs.filter(predicate)
```

```javascript
const is = (type) => (x) => Object(x) instanceof type
```

```javascript
filter(is(Number), [0, '1', 2, null]) // [0, 2]
```

## Closure

__Замыкание__

Замыкание - это область, которая захватывает локальные переменные функции и делает их доступными даже после того, как выполнение кода выходит из блока, в котором они определены. Это позволяет значениям в замыкании быть доступными возвращающим функциям.

```javascript
const addTo = x => y => x + y
const addToFive = addTo(5)
addToFive(3) // => 8
```

В данном случае `x` сохраняется в замыкании `addToFive` со значением `5`. `addToFive` затем может вызываться с `y` для получения суммы.

__Дополнительные материалы__
* [Lambda Vs Closure](http://stackoverflow.com/questions/220658/what-is-the-difference-between-a-closure-and-a-lambda)
* [JavaScript Closures](http://stackoverflow.com/questions/111102/how-do-javascript-closures-work)

## Partial Application

__Частичное применение__

Частичное применение функции означает создание новой функции путем предварительного определения некоторых аргументов исходной функции:

```javascript
// Утилита для создания частично примененных функций.
// Принимает функцию и аргументы
const partial = (f, ...args) =>
  // Возвращает функцию, которая принимает другие аргументы
  (...moreArgs) =>
    // и вызывает оригинальную функцию со всеми аргументами
    f(...args, ...moreArgs)

// Нечто для применения
const add3 = (a, b, c) => a + b + c

// Частичное применение `2` и `3` к `add3` дает функцию с одним параметром
const fivePlus = partial(add3, 2, 3) // (c) => 2 + 3 + c

fivePlus(4) // 9
```

Для частичного применения функций в JS также можно использовать `Function.prototype.bind`:

```javascript
const add1More = add3.bind(null, 2, 3) // (c) => 2 + 3 + c
```

Частичное применение помогает создавать более простые функции из более сложных путем предварительного сохранения данных при их наличии.

## Currying

__Каррирование__

Процесс преобразования функции, принимающей несколько аргументов в функцию, принимающую один аргумент за раз.

При каждом вызове функция принимает только один аргумент и возвращает функцию, которая также принимает один аргумент, до тех пор, пока не будут переданы все аргументы:

```javascript
const sum = (a, b) => a + b

const curriedSum = (a) => (b) => a + b

curriedSum(40)(2) // 42

const add2 = curriedSum(2) // (b) => 2 + b

add2(10) // 12
```

## Auto Currying

__Автокаррирование__

Преобразование функции, которая принимает несколько аргументов в функцию, которая при передаче меньшего количества аргументов, чем требуется, возвращает функцию, принимающую оставшиеся аргументы. Функция вычисляется только после передачи всех аргументов.

Lodash и Ramda предоставляют функцию `curry`, которая работает именно так.

```javascript
const add = (x, y) => x + y

const curriedAdd = _.curry(add)
curriedAdd(1, 2) // 3
curriedAdd(1) // (y) => 1 + y
curriedAdd(1)(2) // 3
```

__Дополнительные материалы__
* [Favoring Curry](http://fr.umio.us/favoring-curry/)
* [Hey Underscore, You're Doing It Wrong!](https://www.youtube.com/watch?v=m3svKOdZijA)

## Function Composition

__Композиция функций__

Объединение двух функций в одну, где результат одной функции передается на вход другой функции. Эта одна из наиболее важных концепций ФП.

```javascript
const compose = (f, g) => (a) => f(g(a)) // Определение
const floorAndToString = compose((val) => val.toString(), Math.floor) // Использование
floorAndToString(121.212121) // '121'
```

## Continuation

__Продолжение__

В любой момент выполнения программы часть кода, которая сейчас будет выполняться, называется продолжением.

```javascript
const printAsString = (num) => console.log(`Given ${num}`)

const addOneAndContinue = (num, cc) => {
  const result = num + 1
  cc(result)
}

addOneAndContinue(2, printAsString) // 'Given 3'
```

Продолжения часто встречаются в асинхронном программировании, когда программе нужно ждать данных, чтобы продолжить выполнение. После получения данных они часто передаются другой части программы, которая является продолжением:

```javascript
const continueProgramWith = (data) => {
  // Продолжение выполнения программы с данными
}

readFileAsync('path/to/file', (err, response) => {
  if (err) {
    // Обработка ошибки
    return
  }
  // Передача ответа
  continueProgramWith(response)
})
```

## IO

Чистая структура данных, которая инкапсулирует сторонний эффект. Вместо выполнения эффекта сразу, `IO` оборачивает операцию в нульарную (nullable) функцию ([thunk](#thunk)), позволяя преобразовывать операции с эффектами, создавать из них цепочки и композиции чистых [значений](#value) без их выполнения до явного вызова.

```javascript
const IO = (run) => ({
  run,
  map: (f) => IO(() => f(run())),
  chain: (f) => IO(() => f(run()).run())
})

// Чистое описание - пока ничего не выполняется
const readTimestamp = IO(() => Date.now())
const formatted = readTimestamp.map((ts) => new Date(ts).toISOString())

// Сторонний эффект выполняется только после вызова .run()
formatted.run()
```

__Дополнительные материалы__
* [IO container](https://drboolean.gitbooks.io/mostly-adequate-guide/content/ch8.html#pure-functional-magic)

## Trampoline

__Трамплин/батут__

Механизм, позволяющий глубоким или взаимно рекурсивным функциям выполняться без переполнения стека вызовов.

В средах выполнения без Tail Call Optimization (TCO) (оптимизации хвостовых вызовов), рекурсивные вызовы возвращают функцию (thunk) вместо прямого выполнения. Трамплин запускает цикл while, который разматывает каждый thunk до достижения финального значения.

```javascript
const trampoline = (fn) => (...args) => {
  let result = fn(...args)
  while (typeof result === 'function') {
    result = result()
  }
  return result
}

// Без трамплина: sumBelow(1000000) выбрасывает "Maximum call stack size exceeded"
const sumBelow = (n, acc = 0) =>
  n === 0
    ? acc
    : () => sumBelow(n - 1, acc + n) // возвращает thunk вместо прямого выполнения

const safeSum = trampoline(sumBelow)
safeSum(1000000) // 500000500000
```

__Дополнительные материалы__
* [Trampolining in JavaScript](https://raganwald.com/2013/03/28/trampolines-in-javascript.html)

## Thunk

Нульарная (nullable) функция (функция, не принимающая аргументы), которая оборачивает выражение для задержки его вычисления до вызова. Thunk - фундаментальный механизм реализации [ленивых вычислений](#lazy-evaluation), [трамплинов](#trampoline) и отложенных сторонних эффектов.

```javascript
// Жадное (eager) вычисление выполняется сразу:
// const data = expensiveCalculation()

// Thunk оборачивает выражение в функцию, откладывая ее выполнение:
const thunk = () => 42 * 2

// Выражение вычисляется только при явном вызове:
thunk() // 84
```

__Дополнительные материалы__
* [Thunk](https://en.wikipedia.org/wiki/Thunk) on Wikipedia

## Algebraic Effects

__Алгебраические эффекты__

Система вычислительных эффектов, которая отделяет вызов эффекта от его обработки. Вместо привязки функции к среде выполнения, функция "выполняет" операцию эффекта (такую как чтение состояния, запрос конфигурации или логгирование). Внешний "обработчик" перехватывает выполняемый эффект и предоставляет результат, позволяя возобновить вычисления или прервать их; это обобщает механизмы исключений, async/await и генераторов, не требуя использования сложных стеков трансформеров монад.

```javascript
// Генераторы моделируют ограниченные продолжения / алгебраические эффекты:
const perform = (effect) => ({ [Symbol.for('effect')]: true, effect })

// Программа выполняет эффекты без знания того, кто их обрабатывает:
function * fetchUserProfile (userId) {
  const config = yield perform({ type: 'ask_config' })
  yield perform({ type: 'log', message: `Fetching user ${userId} from ${config.apiUrl}` })
  return { id: userId, name: 'Alice' }
}

// Обработчик эффектов перехватывает их и продолжает вычисление:
const handle = (generator, handlers) => {
  const iter = generator()
  const step = (value) => {
    const { done, value: yielded } = iter.next(value)
    if (done) return yielded
    if (yielded && yielded[Symbol.for('effect')]) {
      const { type } = yielded.effect
      if (handlers[type]) {
        return handlers[type](yielded.effect, (resumeVal) => step(resumeVal))
      }
    }
    return step(yielded)
  }
  return step()
}

// Запуск с интерпретатором / обработчиком:
handle(
  () => fetchUserProfile(42),
  {
    ask_config: (effect, resume) => resume({ apiUrl: 'https://api.test.local' }),
    log: (effect, resume) => {
      console.log(effect.message)
      return resume()
    }
  }
)
```

__Дополнительные материалы__
* [Algebraic Effects for the Rest of Us](https://overreacted.io/algebraic-effects-for-the-rest-of-us/)
* [What is Algebraic Effects?](https://koka-lang.github.io/koka/doc/book.html#why-effects)

## Pure Function

__Чистая функция__

Функция называется чистой, если возвращаемое ей значение определяется только входящими значениями, и она не выполняет сторонние эффекты. Функция должна возвращать одинаковый результат для одинаковых входных данных.

```javascript
const greet = (name) => `Hi, ${name}`

greet('Brianne') // 'Hi, Brianne'
```

Примеры "нечистых" функций:

```javascript
window.name = 'Brianne'

const greet = () => `Hi, ${window.name}`

greet() // "Hi, Brianne"
```

Здесь результат зависит от данных, хранящихся за пределами функции.

```javascript
let greeting

const greet = (name) => {
  greeting = `Hi, ${name}`
}

greet('Brianne')
greeting // "Hi, Brianne"
```

Здесь модифицируется состояние, не принадлежащее функции.

## Side effects

__Сторонние эффекты__

Функция или выражение содержат сторонний эффект, если, помимо возврата значения, они взаимодействуют с (читаю из или пишут в) внешнее модифицируемое состояние:

```javascript
const differentEveryTime = new Date()
```

```javascript
console.log('IO is a side effect!')
```

## Idempotence

__Идемпотентность__

Функция является идемпонтентной, если ее повторное применение всегда дает одинаковый результат:

```javascript
Math.abs(Math.abs(10))
```

```javascript
sort(sort(sort([2, 1])))
```

## Point-Free Style

__Беспараметрический стиль__

Написание функций, где дефиниция не определяет используемые аргументы явно. Этот стиль обычно требует [каррирования](#currying) или других [функций более высокого порядка](#higher-order-functions-hof). Другое название - бесточечное программирование (tacit programming).

```javascript
// Дано
const map = (fn) => (list) => list.map(fn)
const add = (a) => (b) => a + b

// Затем

// Не беспараметрический стиль - `numbers` - явный аргумент
const incrementAll = (numbers) => map(add(1))(numbers)

// Беспараметрический стиль - `list` - неявный аргумент
const incrementAll2 = map(add(1))
```

Такие определения функций выглядят как обычные присваивания без `function` или `=>`. Следует отметить, что беспараметрические функции не обязательно лучше обычных, поскольку они могут быть более сложными в понимании в сложных случаях.

## Predicate

__Предикат__

Предикат - это функция, возвращающая `true` или `false` для переданного значения. Частый случай использования - коллбек для фильтрации массива.

```javascript
const predicate = (a) => a > 2

;[1, 2, 3, 4].filter(predicate) // [3, 4]
```

## Contract

__Контракт__

Контракт определяет обязательства и гарантии относительно поведения функции или выражения во время выполнения. Он представляет собой набор правил, касающихся входных и выходных данных функции или выражения, и, как правило, при нарушении контракта возникает ошибка:

```javascript
// Определяем наш контракт: int -> boolean
const contract = (input) => {
  if (typeof input === 'number') return true
  throw new Error('Contract violated: expected int -> boolean')
}

const addOne = (num) => contract(num) && num + 1

addOne(2) // 3
addOne('some string') // контракт нарушен: ожидалось int -> boolean
```

## Category

__Категория__

В теории категорий категория представляет собой совокупность объектов и морфизмов (morphisms) между ними. В программировании объектами обычно выступают типы, а морфизмами - функции.

Три правила валидной категории:

1. Должен существовать морфизм тождества, отображающий объект в самого себя. Если `a` - объект некоторой категории, то должно существовать отображение `a -> a`.
2. Морфизмы должны обладать свойством композиции. Если `a`, `b` и `c` - объекты некоторой категории, `f` - морфизм из `a` в `b`, а `g` - морфизм из `b` в `c`, то `g(f(x))` должно быть эквивалентно `(g • f)(x)`.
3. Композиция должна быть ассоциативной: `f • (g • h)` - это то же самое, что `(f • g) • h`.

Поскольку эти правила регулируют композицию на очень высоком уровне абстракции, теория категорий прекрасно подходит для выявления новых способов компоновки объектов.

В качестве примера мы можем определить категорию `Max` как класс:

```javascript

class Max {
  constructor (a) {
    this.a = a
  }

  id () {
    return this
  }

  compose (b) {
    return this.a > b.a ? this : b
  }

  toString () {
    return `Max(${this.a})`
  }
}

new Max(2).compose(new Max(3)).compose(new Max(5)).id().id() // => Max(5)
```

__Дополнительные материалы__
* [Category Theory for Programmers](https://bartoszmilewski.com/2014/10/28/category-theory-for-programmers-the-preface/)

## Semigroupoid

__Полугруппоид__

Алгебраическая структура с объектами и морфизмами, которые можно ассоциативно компоновать, но которая не гарантирует существования тождественного морфизма для каждого объекта.

Полугруппоид удовлетворяет свойству ассоциативности для [композиции](#function-composition): `f.compose(g).compose(h) === f.compose(g.compose(h))`.

Любая [категория](#category) является полугруппоидом, однако для полугруппоида наличие морфизма тождества (`id`) не требуется. Композиция функций образует естественный пример полугруппоида:

```javascript
const Semigroupoid = (fn) => ({
  run: fn,
  compose: (other) => Semigroupoid((x) => fn(other.run(x)))
})

const toUpper = Semigroupoid((s) => s.toUpperCase())
const exclaim = Semigroupoid((s) => `${s}!`)

const loudGreeting = exclaim.compose(toUpper)
loudGreeting.run('hello') // 'HELLO!'
```

__Дополнительные материалы__
* [Semigroupoid](https://github.com/fantasyland/fantasy-land#semigroupoid) in Fantasy Land

## Value

__Значение__

Все, что может быть присвоено переменной:

```javascript
5
Object.freeze({ name: 'John', age: 30 }) // функция `freeze` обеспечивает иммутабельность
;(a) => a
;[1]
undefined
```

## Constant

__Константа__

Переменная, значение которой не может меняться после определения:

```javascript
const five = 5
const john = Object.freeze({ name: 'John', age: 30 })
```

Константы [ссылочно прозрачны](#referential-transparency). Поэтому они могут быть заменены значениями, которые они представляют, без влияния на результат.

Следующее выражение всегда возвращает `true`:

```javascript
john.age + five === ({ name: 'John', age: 30 }).age + 5
```

### Constant Function

__Константная функция__

[Каррированая](#currying) функция, игнорирующая второй аргумент:

```javascript
const constant = a => () => a

;[1, 2].map(constant(0)) // => [0, 0]
```

### Constant Functor

__Константный функтор__

Объект, чей метод `map` не модифицирует его содержимое. См. [функтор](#functor).

```javascript
Constant(1).map(n => n + 1) // => Constant(1)
```

### Constant Monad

__Константная монада__

Объект, чем метод `chain` не модифицирует его содержимое. См. [монада](#monad).

```javascript
Constant(1).chain(n => Constant(n + 1)) // => Constant(1)
```

## Functor

__Функтор__

Объект, реализующий функцию `map`, которая принимает функцию, которая выполняется на содержимом этого объекта. Функтор должен удовлетворять двум условиям:

__Сохранение идентичности__

```javascript
object.map(x => x)
```

это эквивалент простого `object`.

__Компонуемость__

```javascript
object.map(x => g(f(x)))
```

это эквивалент следующего:

```javascript
object.map(f).map(g)
```

(`f`, `g` - произвольные компонуемые функции).

Эталонная реализация [опции](#option) является функтором, поскольку удовлетворяет следующим условиям:

```javascript
Some(1).map(x => x) // = Some(1)
```

и

```javascript
const f = x => x + 1
const g = x => x * 2

Some(1).map(x => g(f(x))) // = Some(4)
Some(1).map(f).map(g) // = Some(4)
```

## Pointed Functor

__Пунктированный функтор__

Это объект с функцией `of`, которая добавляет в него любое единичное значение.

ES2015 добавил метод `Array.of`, сделав массив пунктированным функтором:

```javascript
Array.of(1) // [1]
```

## Lift

__Подъем/поднятие__

Поднятие - это когда мы берем значение и помещаем его в объект, вроде [функтора](#pointed-functor). Если функция поднимается в [аппликативный функтор](#applicative-functor), можно сделать так, чтобы она работала со значениями, которые также находятся в функторе.

Некоторые реализации имеют функцию под названием `lift` или `liftA2` для облегчения запуска функций на функторах:

```javascript
const liftA2 = (f) => (a, b) => a.map(f).ap(b) // заметьте, что второй метод - `ap`, а не `map`

const mult = a => b => a * b

const liftedMult = liftA2(mult) // эта функция не работает на функторах, как массив

liftedMult([1, 2], [3]) // [3, 6]
liftA2(a => b => a + b)([1, 2], [30, 40]) // [31, 41, 32, 42]
```

Поднятие одноаргументной функции и ее применение аналогично тому, что делает `map`:

```javascript
const increment = (x) => x + 1

lift(increment)([2]) // [3]
;[2].map(increment) // [3]
```

Поднятие простых значений может быть просто созданием объекта:

```javascript
Array.of(1) // => [1]
```

## Referential Transparency

__Ссылочная прозрачность__

Выражение, которое можно заменить его значением без изменения поведения программы, называется ссылочно (референциально) прозрачным.

Рассмотрим такую функцию:

```javascript
const greet = () => 'Hello World!'
```

Любой вызов `greet()` можно заменить на `Hello World!`, следовательно, функция `greet` обладает свойством референциальной прозрачности. Это свойство было бы нарушено, если бы `greet` зависела от внешнего состояния, например, от конфигурации или обращения к базе данных. См. также [чистые функции](#pure-function) и [рассуждение на основе равенств](#equational-reasoning).

## Equational Reasoning

__Рассуждение на основе равенств__

Когда приложение состоит из выражений и не имеет побочных эффектов,
выводы о системе можно сделать на основе анализа ее отдельных частей. Кроме того, можно быть уверенным в деталях работы системы, не изучая при этом каждую функцию.

```javascript
const grainToDogs = compose(chickenIntoDogs, grainIntoChicken)
const grainToCats = compose(dogsIntoCats, grainToDogs)
```

В приведенном примере, если мы знаем, что `chickenIntoDogs` и `grainIntoChicken` - [чистые функции](#pure-function), тогда мы знаем, что композиция чистая. Этот подход можно развить дальше, когда станет больше известно о свойствах функций (ассоциативности, коммутативности, идемпотентности и т.д.).

## Memoization

__Мемоизация__

Техника оптимизации, которая кэширует возвращаемое функцией значение на основе ее входных параметров. Мемоизация валидна и безопасна только для [чистых функций](#pure-function), обладающих [ссылочной прозрачностью](#referential-transparency), поскольку вызов функции с идентичными аргументами должен всегда возвращать одинаковые результаты без наблюдаемых [сторонних эффектов](#side-effects).

```javascript
const memoize = (fn) => {
  const cache = new Map()
  return (arg) => {
    if (!cache.has(arg)) {
      cache.set(arg, fn(arg))
    }
    return cache.get(arg)
  }
}

const factorial = memoize((n) => (n <= 1 ? 1 : n * factorial(n - 1)))
factorial(5) // вычислено: 120
factorial(5) // извлечено из кэша: 120
```

__Дополнительные материалы__
* [Мемоизация](https://ru.wikipedia.org/wiki/%D0%9C%D0%B5%D0%BC%D0%BE%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D1%8F) в Википедии

## Lambda

__Лямбда__

Анонимная функция, с которой можно обращаться как со значением:

```javascript
;(function (a) {
  return a + 1
})

;(a) => a + 1
```

Лямбды часто передаются как аргументы в функции более высокого порядка:

```javascript
;[1, 2].map((a) => a + 1) // [2, 3]
```

Лямбду можно присвоить переменной:

```javascript
const add1 = (a) => a + 1
```

## Lambda Calculus

__Лямбда-исчисление__

Раздел математики, использующий функции для создания [универсальной модели вычислений](https://ru.wikipedia.org/wiki/%D0%9B%D1%8F%D0%BC%D0%B1%D0%B4%D0%B0-%D0%B8%D1%81%D1%87%D0%B8%D1%81%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5).

## Functional Combinator

__Функциональный комбинатор__

Функция более высокого порядка, как правило, каррированная, которая возвращает новую функцию, модифицированную тем или иным образом. Функциональные комбинаторы часто используются в [беспараметрическом стиле](#point-free-style) для написания особо лаконичных программ.

```javascript
// Комбинатор "C" принимает каррированную двуаргументную функцию и возвращает функцию,
// которая вызывает оригинальную функцию с аргументами в обратном порядке
const C = (f) => (a) => (b) => f(b)(a)

const divide = (a) => (b) => a / b

const divideBy = C(divide)

const divBy10 = divideBy(10)

divBy10(30) // => 3
```

См. также [список функциональных комбинаторов в JavaScript](https://gist.github.com/Avaq/1f0636ec5c8d6aed2e45).

## Lazy evaluation

__Ленивое вычисление__

Ленивые вычисления - это механизм вычисления по требованию, при котором вычисление выражения откладывается до момента, когда его значение действительно необходимо. В функциональных языках это позволяет создавать такие структуры, как бесконечные списки, которые обычно недоступны в императивных языках, где важна последовательность выполнения команд.

```javascript
const rand = function * () {
  while (1 < 2) {
    yield Math.random()
  }
}
```

```javascript
const randIter = rand()
randIter.next() // каждое выполнение дает произвольное значение, выражение оценивается по требованию
```

## Monoid

__Моноид__

Объект с функцией, которая "комбинирует" этот объект с другим объектом того же типа (полугруппа), который имеет "идентичное" значение.

Примером простого моноида является сложение чисел:

```javascript
1 + 1 // 2
```

В данном случае число - это объект, а `+` - функция.

Когда любое значение комбинируется с идентичным значением, результатом должно быть оригинальное значение. Идентичность также должна быть коммутативной.

Идентичным значением для сложения является `0`:

```javascript
1 + 0 // 1
0 + 1 // 1
1 + 0 === 0 + 1
```

Также требуется, чтобы группировка операций не влияла на результат (ассоциативность):

```javascript
1 + (2 + 3) === (1 + 2) + 3 // true
```

Конкатенация массивов также формирует моноид:

```javascript
;[1, 2].concat([3, 4]) // [1, 2, 3, 4]
```

Идентичным значением в данном случае является пустой массив `[]`:

```javascript
;[1, 2].concat([]) // [1, 2]
```

Напротив, вычитание не формирует моноид, поскольку не существует для него коммутативного идентичного значения:

```javascript
0 - 4 === 4 - 0 // false
```

## Monad

__Монада__

Монада - это объект с функциями [`of`](#pointed-functor) и `chain`. `chain` похожа на [`map`](#functor), за исключением того, что она раскрывает (unnest) вложенные объекты.

```javascript
// Реализация
Array.prototype.chain = function (f) {
  return this.reduce((acc, it) => acc.concat(f(it)), [])
}

// Использование
Array.of('cat,dog', 'fish,bird').chain((a) => a.split(',')) // ['cat', 'dog', 'fish', 'bird']

// Пример с map
Array.of('cat,dog', 'fish,bird').map((a) => a.split(',')) // [['cat', 'dog'], ['fish', 'bird']]
```

`of` также именуется `return` в других функциональных языках, а `chain` - `flatmap` и `bind`.

## Comonad

__Комонада__

Объект, содержащий функции `extract` и `extend`:

```javascript
const CoIdentity = (v) => ({
  val: v,
  extract () {
    return this.val
  },
  extend (f) {
    return CoIdentity(f(this))
  }
})
```

`extract` извлекает значение из функтора:

```javascript
CoIdentity(1).extract() // 1
```

`extend` запускает функцию на комонаде. Функция должна возвращать тот же тип, что и комонада:

```javascript
CoIdentity(1).extend((co) => co.extract() + 1) // CoIdentity(2)
```

## Kleisli Composition

__Композиция Клейсли__

Операция композиции двух функций, возвращающих [монаду](#monad) (стрелки Клейсли), при условии совместимости их типов. В Haskell это оператор `>=>`.

С помощью [опции](#option):

```javascript
// safeParseNum :: String -> Number Option
const safeParseNum = (b) => {
  const n = parseNumber(b)
  return isNaN(n) ? None() : Some(n)
}

// validatePositive :: Number -> Number Option
const validatePositive = (a) => a > 0 ? Some(a) : None()

// kleisliCompose :: Monad M => ((b -> M c), (a -> M b)) -> a -> M c
const kleisliCompose = (g, f) => (x) => f(x).chain(g)

// parseAndValidate :: String -> Number Option
const parseAndValidate = kleisliCompose(validatePositive, safeParseNum)

parseAndValidate('1') // => Some(1)
parseAndValidate('asdf') // => None
parseAndValidate('999') // => Some(999)
```

Это работает, поскольку:

 * [опция](#option) - это [монада](#monad),
 * и `validatePositive`, и `safeParseNum` возвращают одинаковый тип монад (Option),
 * тип аргумента `validatePositive` совпадает с раскрытым (unwrapped) результатом `safeParseNum`.

## Free Monad

__Свободная монада__

Свободная монада - это конструкция, позволяющая создать [монаду](#monad) из любого [функтора](#functor) без добавления какой-либо предметно-специфичной логики. Она обеспечивает четкое разделение описания программы (абстрактного синтаксического дерева команд) и ее выполнения (интерпретатора, вычисляющего это дерево).

Свободная монада бывает двух видов:
* `Pure`: оборачивает финальное значение и прерывает вычисление.
* `Free`: оборачивает функтор, содержащий следующий шаг вычисления.

```javascript
// Конструкторы свободных монад:
const Pure = (x) => ({
  isPure: true,
  value: x,
  map: (f) => Pure(f(x)),
  chain: (f) => f(x)
})

const Free = (fn) => ({
  isPure: false,
  functor: fn,
  map: (f) => Free(fn.map((next) => next.map(f))),
  chain: (f) => Free(fn.map((next) => next.chain(f)))
})

// Поднятие инструкции функтора в свободную монаду:
const liftF = (cmd) => Free(cmd.map(Pure))

// Функтор, представляющий инструкции логгирования:
const Log = (msg, next) => ({
  type: 'log',
  msg,
  next,
  map: (f) => Log(msg, f(next))
})

// Программа: описание операций без их выполнения
const logMsg = (msg) => liftF(Log(msg, null))
const program = logMsg('Starting').chain(() => logMsg('Done')).chain(() => Pure(42))

// Интерпретатор: выполняет дерево инструкций
const interpret = (freeMonad) => {
  if (freeMonad.isPure) return freeMonad.value
  const { type, msg, next } = freeMonad.functor
  if (type === 'log') {
    console.log(msg)
    return interpret(next)
  }
}

interpret(program) // логгирует 'Starting', 'Done', возвращает 42
```

__Дополнительные материалы__
* [Free monads in JavaScript](https://medium.com/@gcanti/free-monads-in-javascript-f5df234d3d2a)

## Monad Transformer

__Трансформер монад__

В то время как [функторы](#functor) и [аппликативные функторы](#applicative-functor) естественным образом компонуются друг с другом, [монады](#monad) в общем случае не поддаются композиции без знания их конкретных типов. Трансформер монад - это конструктор типов, который принимает существующую монаду и создает новую, обладающую объединенными возможностями (например, сочетающую в себе обработку ошибок, асинхронные задачи и работу с состоянием).

Названия трансформеров монад, обычно, заканчивается на `T` (например, `MaybeT`, `ReaderT`, `StateT`).

```javascript
// MaybeT оборачивает любую внешнюю монаду M для добавления опциональности:
const MaybeT = (M) => {
  const of = (value) => MaybeTInstance(M.of({ isSome: true, value }))
  const none = () => MaybeTInstance(M.of({ isSome: false }))

  const MaybeTInstance = (run) => ({
    run,
    chain: (f) =>
      MaybeTInstance(
        run.chain((opt) => (opt.isSome ? f(opt.value).run : M.of(opt)))
      ),
    map: (f) =>
      MaybeTInstance(
        run.map((opt) => (opt.isSome ? { isSome: true, value: f(opt.value) } : opt))
      )
  })

  return { of, none, from: MaybeTInstance }
}

// Монада тождества:
const Id = (x) => ({
  value: x,
  map: (f) => Id(f(x)),
  chain: (f) => f(x)
})
Id.of = Id

// Объединение монады с переданным Id с эффектом Maybe:
const MaybeId = MaybeT(Id)

const findUser = (id) =>
  id === 1 ? MaybeId.of({ name: 'Alice', age: 30 }) : MaybeId.none()

const getAge = (id) =>
  findUser(id)
    .chain((user) => MaybeId.of(user.age))
    .run

getAge(1).value // { isSome: true, value: 30 }
getAge(2).value // { isSome: false }
```

__Дополнительные материалы__
* [Monad Transformers Step by Step](https://page.mi.fu-berlin.de/scravy/realworldhaskell/materialien/monad-transformers-step-by-step.pdf)

## Applicative Functor

__Аппликативный функтор__

Аппликативный функтор - это объект с функцией `ap`. `ap` применяет функцию в объекте к значению другого объекта с тем же типом.

```javascript
// Реализация
Array.prototype.ap = function (xs) {
  return this.reduce((acc, f) => acc.concat(xs.map(f)), [])
}

// Пример использования
;[(a) => a + 1].ap([1]) // [2]
```

Это полезно, когда есть два объекта и нужно применить бинарную функцию к их содержимому:

```javascript
// Массивы, которые нужно объединить
const arg1 = [1, 3]
const arg2 = [4, 5]

// Объединяющая функция - должна быть каррирована
const add = (x) => (y) => x + y

const partiallyAppliedAdds = [add].ap(arg1) // [(y) => 1 + y, (y) => 3 + y]
```

Это дает массив функций, на котором можно вызвать `ap` для получения результата:

```javascript
partiallyAppliedAdds.ap(arg2) // [5, 6, 7, 8]
```

## Bifunctor

__Бифунктор__

Структура с двумя независимыми параметрами типа, допускающая одновременное отображение по обоим параметрам. Бифунктор предоставляет метод `bimap`, который принимает две функции и применяет первую к первому параметру типа, а вторую - ко второму:

```javascript
const Pair = (first, second) => ({
  first,
  second,
  bimap: (f, g) => Pair(f(first), g(second)),
  firstMap: (f) => Pair(f(first), second),
  secondMap: (g) => Pair(first, g(second))
})

const score = Pair('alice', 10)
score.bimap((name) => name.toUpperCase(), (points) => points * 2)
// Pair('ALICE', 20)
```

__Дополнительные материалы__
* [Bifunctor](https://github.com/fantasyland/fantasy-land#bifunctor)

## Contravariant Functor

__Контравариантный функтор__

Структура, подобная [функтору](#functor), но в которой преобразование происходит в обратном направлении. Если ковариантный (covariant) функтор преобразует производителя (producer) `F<A>` в `F<B>` с помощью функции `(a -> b)`, то контравариантный функтор преобразует потребителя (consumer) `F<A>` в `F<B>` с помощью функции `(b -> a)`, используя метод `cmap` (или `contramap`).

Контравариантные функторы часто используются для моделирования предикатов, валидаторов, кодировщиков и компараторов сортировки, выполняя предварительную обработку входных данных перед их передачей потребителю.

```javascript
// Predicate оборачивает тестовую функцию (x) -> Boolean
const Predicate = (test) => ({
  test,
  // cmap :: (b -> a) -> Predicate a -> Predicate b
  cmap: (f) => Predicate((x) => test(f(x)))
})

// Существующий Predicate проверяет длину строки
const isLongString = Predicate((s) => s.length > 5)

// Contramap преобразует объект User в строку (user.bio)
const hasLongBio = isLongString.cmap((user) => user.bio)

hasLongBio.test({ bio: 'Hello World' }) // true
hasLongBio.test({ bio: 'Hi' }) // false
```

__Дополнительные материалы__
* [Contravariant Functor](https://github.com/fantasyland/fantasy-land#contravariant)

## Profunctor

__Профунктор__

Профунктор - это [бифунктор](#bifunctor), который контравариантен по первому аргументу и ковариантен по второму аргументу.

Для структуры `P<A, B>`, представляющей вычисление, которое потребляет `A` и выдает `B`, функция `promap` принимает две функции - `(a' -> a)` и `(b -> b')` - и возвращает `P<A', B'>`.

Функции вида `(a -> b)` являются каноническими профункторами: можно предварительно обработать входные данные с помощью `(a' -> a)` и пост-обработать выходные данные с помощью `(b -> b')`. Профункторы составляют математическую основу оптик на профункторах.

```javascript
// Функции - натуральные профункторы:
const Profunctor = (fn) => ({
  run: fn,
  // promap :: (a' -> a) -> (b -> b') -> P a b -> P a' b'
  promap: (f, g) => Profunctor((x) => g(fn(f(x))))
})

// Существующая функция: String -> Number
const stringLength = Profunctor((str) => str.length)

// Предварительно обработанные входные данные (удаление пробелов) и пост-обработанные выходные данные (проверка на четность):
const isTrimmedLengthEven = stringLength.promap(
  (raw) => raw.trim(), // контрвариант: предобработка аргумента
  (len) => len % 2 === 0 // ковариант: пост-обработка результата
)

isTrimmedLengthEven.run('   code   ') // 4 четное -> true
isTrimmedLengthEven.run(' hello ') // 5 нечетное -> false
```

__Дополнительные материалы__
* [Profunctor](https://github.com/fantasyland/fantasy-land#profunctor)

## Alternative

__Альтернатива__

[Аппликативный функтор](#applicative-functor), который также образует [моноид](#monoid), предоставляя бинарный оператор выбора `alt` (часто записываемый как `<|>`) и нейтральный элемент для обработки сбоев и реализации резервной логики.

При объединении вычислений с помощью `alt` структура обычно реализует принцип "побеждает первый успешный вариант": если предыдущее вычисление завершилось неудачей или вернуло пустой результат, управление переходит к следующим альтернативам.

```javascript
const AltOption = {
  Some: (x) => ({
    alt: (_other) => AltOption.Some(x),
    value: x
  }),
  None: () => ({
    alt: (other) => other,
    value: null
  })
}

// Цепочка конфигурации с механизмом резервирования: используется первое валидное значение
const primaryConfig = AltOption.None()
const secondaryConfig = AltOption.Some({ port: 8080 })
const defaultConfig = AltOption.Some({ port: 3000 })

const finalConfig = primaryConfig.alt(secondaryConfig).alt(defaultConfig)
finalConfig.value // { port: 8080 }
```

__Дополнительные материалы__
* [Alt](https://github.com/fantasyland/fantasy-land#alt)
* [Alternative](https://github.com/fantasyland/fantasy-land#alternative)

## Morphism

__Морфизм__

Отношение между объектами одной [категории](#category). В контексте функционального программирования все функции являются морфизмами.

### Homomorphism

__Гомоморфизм__

Функция, обладающая структурным свойством, которое сохраняется неизменным при переходе от входных данных к выходным.

Например, в гомоморфизме [моноидов](#monoid) и входные, и выходные данные являются моноидами, даже если их типы различаются:

```javascript
// toList :: [number] -> string
const toList = (a) => a.join(', ')
```

`toList` - это гомоморфизм, поскольку:
* массив - это моноид: содержит операцию `concat` и идентичное значение (`[]`)
* строка - это моноид: содержит операцию `concat` и идентичное значение (`''`)

Таким образом, гомоморфизм связывает те свойства входных и выходных данных преобразования, которые нас интересуют.

[Эндоморфизмы](#endomorphism) и [изоморфизмы](#isomorphism) являются примерами гомоморфизма.

__Дополнительные материалы__
* [Homomorphism | Learning Functional Programming in Go](https://subscription.packtpub.com/book/application-development/9781787281394/11/ch11lvl1sec90/homomorphism#:~:text=A%20homomorphism%20is%20a%20correspondence,pointing%20to%20it%20from%20A.)

### Endomorphism

__Эндоморфизм__

Функция, у которой тип входных данных совпадает с типом выходных данных. Поскольку типы идентичны, эндоморфизмы также являются [гомоморфизмами](#homomorphism).

```javascript
// uppercase :: String -> String
const uppercase = (str) => str.toUpperCase()

// decrement :: Number -> Number
const decrement = (x) => x - 1
```

### Isomorphism

__Изоморфизм__

Морфизм, представляющий собой пару преобразований между объектами двух типов; он носит структурный характер, и при этом не происходит потери данных.

Например, двумерные координаты можно хранить в виде массива `[2,3]` или объекта `{x: 2, y: 3}`.

```javascript
// Наличие функций для преобразования в обоих направлениях делает структуры двумерных координат изоморфными
const pairToCoords = (pair) => ({ x: pair[0], y: pair[1] })

const coordsToPair = (coords) => [coords.x, coords.y]

coordsToPair(pairToCoords([1, 2])) // [1, 2]

pairToCoords(coordsToPair({ x: 1, y: 2 })) // {x: 1, y: 2}
```

Изоморфизмы - интересный пример [морфизма](#morphism), поскольку для него требуется нечто большее, чем просто одна функция. Изоморфизмы также являются [гомоморфизмами](#homomorphism), так как типы входных и выходных данных обладают свойством обратимости.

### Catamorphism

__Катаморфизм__

Функция, которая преобразует структуру в простое значение. `reduceRight` — это пример катаморфизма для массивов:

```javascript
// sum - это катаморфизм из [Number] -> Number
const sum = xs => xs.reduceRight((acc, x) => acc + x, 0)

sum([1, 2, 3, 4, 5]) // 15
```

### Anamorphism

__Анаморфизм__

Функция, которая формирует структуру путем многократного применения функции к своему аргументу. Примером служит `unfold`, генерирующая массив на основе функции и начального значения. Это операция, обратная [катаморфизму](#catamorphism). Можно сказать, что анаморфизм создает структуру, а катаморфизм - разбирает ее.

```javascript
const unfold = (f, seed) => {
  function go (f, seed, acc) {
    const res = f(seed)
    return res ? go(f, res[1], acc.concat([res[0]])) : acc
  }
  return go(f, seed, [])
}
```

```javascript
const countDown = n => unfold((n) => {
  return n <= 0 ? undefined : [n, n - 1]
}, n)

countDown(5) // [5, 4, 3, 2, 1]
```

### Hylomorphism

__Гиломорфизм__

Функция, которая компонует [анаморфизм](#anamorphism) и следующий за ним [катаморфизм](#catamorphism).

```javascript
const sumUpToX = (x) => sum(countDown(x))
sumUpToX(5) // 15
```

### Paramorphism

__Параморфизм__

Функция, подобная `reduceRight`. Однако есть отличие - в параморфизме аргументами функции-редуктора являются текущее значение, результат свертки всех предыдущих значений и список значений, из которых этот результат был получен:

```javascript
// Небезопасно для списков, содержащих `undefined`,
// но вполне подходит для иллюстрации
const para = (reducer, accumulator, elements) => {
  if (elements.length === 0) { return accumulator }

  const head = elements[0]
  const tail = elements.slice(1)

  return reducer(head, tail, para(reducer, accumulator, tail))
}

const suffixes = list => para(
  (x, xs, suffxs) => [xs, ...suffxs],
  [],
  list
)

suffixes([1, 2, 3, 4, 5]) // [[2, 3, 4, 5], [3, 4, 5], [4, 5], [5], []]
```

Третий параметр в редукторе (в приведенном примере - `[x, ... xs]`) - это своего рода история того, как было получено текущее значение `acc`.

### Apomorphism

__Апоморфизм__

Это противоположность параморфизма - точно так же, как анаморфизм противоположен катаморфизму. В то время как параморфизм сохраняет доступ к аккумулятору и накопленным данным, апоморфизм позволяет выполнять развертывание (unfold) с возможностью досрочного завершения.

## Natural Transformation

__Естественное преобразование__

Отображение между двумя [функторами](#functor), сохраняющее структуру и преобразующее `F<A>` в `G<A>` без изменения или анализа содержащегося внутри значения `A`.

В функциональном программировании естественное преобразование - это функция, которая меняет тип контейнера, сохраняя его содержимое и удовлетворяя закону естественности: `nat(fa.map(f)) === nat(fa).map(f)`.

```javascript
// nat :: F a -> G a
// Например, массив в Option (берем головной элемент)
const listToOption = (arr) => (arr.length > 0 ? { value: arr[0], isSome: true } : { value: null, isSome: false })

const double = (x) => x * 2

// Закон естественности: преобразование после отображения равно отображению после преобразования
const arrayTransformed = listToOption([1, 2, 3].map(double)) // { value: 2, isSome: true }
const mappedOption = { value: double(listToOption([1, 2, 3]).value), isSome: true } // { value: 2, isSome: true }
arrayTransformed.value === mappedOption.value // true
```

__Дополнительные материалы__
* [Естественное преобразование](https://ru.wikipedia.org/wiki/%D0%95%D1%81%D1%82%D0%B5%D1%81%D1%82%D0%B2%D0%B5%D0%BD%D0%BD%D0%BE%D0%B5_%D0%BF%D1%80%D0%B5%D0%BE%D0%B1%D1%80%D0%B0%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5) в Википедии

## Setoid

__Сетоид__

Объект, имеющий функцию `equals`, которую можно использовать для сравнения других объектов того же типа.

Делаем массив сетоидом:

```javascript
Array.prototype.equals = function (arr) {
  const len = this.length
  if (len !== arr.length) {
    return false
  }
  for (let i = 0; i < len; i++) {
    if (this[i] !== arr[i]) {
      return false
    }
  }
  return true
}

;[1, 2].equals([1, 2]) // true
;[1, 2].equals([0]) // false
```

## Semigroup

__Полугруппа__

Объект, содержащий функцию `concat`, которая комбинирует его с другим объектом такого же типа:

```javascript
;[1].concat([2]) // [1, 2]
```

## Foldable

__Свертка__

Объект, имеющий функцию `reduce`, которая применяет заданную функцию к аккумулятору и каждому элементу массива (слева направо), сводя его к единственному значению:

```javascript
const sum = (list) => list.reduce((acc, val) => acc + val, 0)
sum([1, 2, 3]) // 6
```

## Traversable

__Проходимый/обходимый?__

Тип, являющийся одновременно [сверткой](#foldable) и [функтором](#functor), который позволяет "вывернуть наизнанку" коллекцию вложенных значений с помощью методов `sequence` или `traverse`, преобразуя `F<G<A>>` в `G<F<A>>`.

Этот механизм часто используется для обработки списка асинхронных операций или значений, допускающих отсутствие результата (nullable), когда требуется вынести эффект, создаваемый внешней оболочкой, на более высокий уровень:

```javascript
// promiseSequence преобразует список промисов в промис, возвращающий список
// [Promise<1>, Promise<2>] -> Promise<[1, 2]>
const promiseSequence = (promises) =>
  promises.reduce(
    (acc, p) => acc.then((arr) => p.then((val) => [...arr, val])),
    Promise.resolve([])
  )

promiseSequence([
  Promise.resolve(1),
  Promise.resolve(2),
  Promise.resolve(3)
]).then(console.log) // [1, 2, 3]
```

__Дополнительные материалы__
* [Traversable](https://github.com/fantasyland/fantasy-land#traversable)

## Lens

__Объектив/линза__

Линза - это структура (часто объект или функция), объединяющая геттер и немутирующий сеттер для некоторой другой структуры данных:

```javascript
// С помощью [лизны Ramda](http://ramdajs.com/docs/#lens)
const nameLens = R.lens(
  // Геттер для свойства name объекта
  (obj) => obj.name,
  // Сеттер для свойства name
  (val, obj) => Object.assign({}, obj, { name: val })
)
```

Наличие пары методов `get` и `set` для конкретной структуры данных открывает ряд интересных возможностей:

```javascript
const person = { name: 'Gertrude Blanch' }

// Вызов геттера
R.view(nameLens, person) // 'Gertrude Blanch'

// Вызов сеттера
R.set(nameLens, 'Shafi Goldwasser', person) // {name: 'Shafi Goldwasser'}

// Запуск функции на значении структуры
R.over(nameLens, uppercase, person) // {name: 'GERTRUDE BLANCH'}
```

Линзы также компонуемы. Это облегчает иммутабельные обновления глубоко вложенных данных:

```javascript
// Эта линза фокусируется на первом элементе непустого массива
const firstLens = R.lens(
  // Извлекаем первый элемент массива
  xs => xs[0],
  // Иммутабельный сеттер для первого элемента массива
  (val, [__, ...xs]) => [val, ...xs]
)

const people = [{ name: 'Gertrude Blanch' }, { name: 'Shafi Goldwasser' }]

// Линзы компонуются слева направо
R.over(compose(firstLens, nameLens), uppercase, people) // [{'name': 'GERTRUDE BLANCH'}, {'name': 'Shafi Goldwasser'}]
```

Другие реализации:
* [partial.lenses](https://github.com/calmm-js/partial.lenses) - приятный синтаксический сахар и множество мощных возможностей
* [nanoscope](http://www.kovach.me/nanoscope/) - текучий (fluent) интерфейс

## Prism

__Призма__

Оптика, фокусирующаяся на подтипе или варианте [суммарного типа](#sum-type). В отличие от [линзы](#lens), которая всегда предполагает наличие целевого поля в финальном типе (product type), призма может не сработать, так как целевой вариант может отсутствовать.

Призма состоит из функции `preview` (которая возвращает [опцию](#option) или null) и функции `review` (которая реконструирует всю структуру данных из части, находящейся в фокусе):

```javascript
const Prism = (preview, review) => ({
  preview,
  review
})

// Призма, фокусируемая на числах в строках
const integerPrism = Prism(
  (str) => (/^-?\d+$/.test(str) ? Number(str) : null),
  (num) => String(num)
)

integerPrism.preview('42') // 42
integerPrism.preview('hello') // null
integerPrism.review(42) // '42'
```

__Дополнительные материалы__
* [Optics / Prism](https://github.com/flunc/optics)

## Iso

Оптический объект, определяющий взаимно-однозначное (биективное) и обратимое соответствие без потерь между двумя представлениями одной и той же информации (`s` и `a`). Iso состоит из функции `to` (типа `s -> a`) и функции `from` (типа `a -> s`), для которых выполняются условия `from(to(x)) === x` и `to(from(y)) === y`.

Iso лежат в основе обратимых преобразований, таких как перевод температурных шкал, смена систем координат или кодирование и декодирование структур данных.

```javascript
const Iso = (to, from) => ({
  to,
  from
})

// Преобразование между градусами Цельсия и градусами Фаренгейта
const tempIso = Iso(
  (c) => (c * 9) / 5 + 32, // в градусы Фаренгейта
  (f) => ((f - 32) * 5) / 9 // из градусов Фаренгейта
)

tempIso.to(100) // 212
tempIso.from(212) // 100
```

__Дополнительные материалы__
* [Изоморфизм](https://ru.wikipedia.org/wiki/%D0%98%D0%B7%D0%BE%D0%BC%D0%BE%D1%80%D1%84%D0%B8%D0%B7%D0%BC) в Википедии
* [Optics / Iso](https://github.com/flunc/optics) на GitHub

## Traversal

__Обход__

Оптика, которая одновременно фокусируется на нуле, одном или нескольких значениях (`0..*`) внутри структуры данных.

В то время как [линза](#lens) фокусируется ровно на одном значении, а [призма](#prism) - на нуле или одном значении, обход обобщает понятие оптики для работы с коллекциями, деревьями или отфильтрованными подмножествами.

Обход предоставляет:
* `getAll`: извлекает все искомые значения в массив.
* `modify`: иммутабельно преобразует каждое искомое значение с помощью связывающей (mapping) функции

```javascript
const Traversal = (getAll, modify) => ({
  getAll,
  modify
})

// Обход фокусируется только на четных числах в массиве:
const evenTraversal = Traversal(
  (arr) => arr.filter((n) => n % 2 === 0),
  (f, arr) => arr.map((n) => (n % 2 === 0 ? f(n) : n))
)

const numbers = [1, 2, 3, 4, 5, 6]

evenTraversal.getAll(numbers) // [2, 4, 6]
evenTraversal.modify((n) => n * 10, numbers) // [1, 20, 3, 40, 5, 60]
```

__Дополнительные материалы__
* [Optics - Traversals](https://github.com/calmm-js/partial.lenses#traversal)

## Type Signatures

__Сигнатуры типов__

Часто функции в JavaScript включают комментарии с типами их аргументов и возвращаемых значений.

Шаблон часто выглядит так:

```javascript
// functionName :: firstArgType -> secondArgType -> returnType

// add :: Number -> Number -> Number
const add = (x) => (y) => x + y

// increment :: Number -> Number
const increment = (x) => x + 1
```

Если функция принимает другую функцию в качестве аргумента, последняя оборачивается в скобки:

```javascript
// call :: (a -> b) -> a -> b
const call = (f) => (x) => f(x)
```

Буквы `a`, `b`, `c`, `d` используются для обозначения того, что аргумент может быть любого типа. Приведенная ниже версия функции `map` принимает функцию, преобразующую значение типа `a` в значение типа `b`, а также массив значений типа `a`, и возвращает массив значений типа `b`.

```javascript
// map :: (a -> b) -> [a] -> [b]
const map = (f) => (list) => list.map(f)
```

__Дополнительные материалы__
* [Ramda's type signatures](https://github.com/ramda/ramda/wiki/Type-Signatures)
* [Mostly Adequate Guide](https://web.archive.org/web/20170602130913/https://drboolean.gitbooks.io/mostly-adequate-guide/content/ch7.html#whats-your-type)
* [What is Hindley-Milner?](http://stackoverflow.com/a/399392/22425)

## Algebraic data type

__Алгебраический тип данных__

Составной тип, образованный путем объединения других типов. К числу распространенных видов алгебраических типов относятся [типы-суммы](#sum-type) и [типы-произведения](#product-type).

### Sum type

__Тип-сумма__

Тип-сумма (sum type) - это объединение двух типов в один новый тип. Он называется суммой, поскольку количество возможных значений результирующего типа равно сумме количеств значений исходных типов.

В JavaScript нет таких типов, но мы можем имитировать их поведение с помощью `Set`:

```javascript
// Представьте, что вместо множеств у нас есть типы,
// которые могут иметь только определенные значения
const bools = new Set([true, false])
const halfTrue = new Set(['half-true'])

// Тип weakLogic содержит сумму значений из bools и halfTrue
const weakLogicValues = new Set([...bools, ...halfTrue])
```

Типы-суммы иногда называют типами-объединениями (union types), исключающими объединениями (discriminated unions) или тегированными объединениями (tagged unions).

В JavaScript существует [несколько](https://github.com/paldepind/union-type) [библиотек](https://github.com/puffnfresh/daggy), упрощающих определение и использование типов-объединений.

Flow предоставляет [типы-объединения](https://flow.org/en/docs/types/unions/), а в TypeScript для решения той же задачи используются [перечисления (enums)](https://www.typescriptlang.org/docs/handbook/enums.html).

### Product type

__Тип-произведение__

Тип-произведение объединяет типы более привычным способом:

```javascript
// point :: (Number, Number) -> {x: Number, y: Number}
const point = (x, y) => ({ x, y })
```

Это называется "произведением", поскольку общее количество возможных значений такой структуры данных представляет собой произведение количества различных значений. Во многих языках программирования существует тип кортеж (tuple), являющийся простейшей реализацией типа-произведения.

__Дополнительные материалы__
* [Теория множеств](https://ru.wikipedia.org/wiki/%D0%A2%D0%B5%D0%BE%D1%80%D0%B8%D1%8F_%D0%BC%D0%BD%D0%BE%D0%B6%D0%B5%D1%81%D1%82%D0%B2) в Википедии

## Option

__Опция__

Опция - это [тип-сумма](#sum-type) с двумя вариантами, часто называемыми `Some` и `None`.

Опция полезна для компоновки функций, которые не всегда возвращают значение:

```javascript
// Наивное определение

const Some = (v) => ({
  val: v,
  map (f) {
    return Some(f(this.val))
  },
  chain (f) {
    return f(this.val)
  }
})

const None = () => ({
  map (f) {
    return this
  },
  chain (f) {
    return this
  }
})

// maybeProp :: (String, {a}) -> Option a
const maybeProp = (key, obj) => typeof obj[key] === 'undefined' ? None() : Some(obj[key])
```

Используем `chain` для создания последовательности функций, возвращающих `Option`:

```javascript
// getItem :: Cart -> Option CartItem
const getItem = (cart) => maybeProp('item', cart)

// getPrice :: Item -> Option Number
const getPrice = (item) => maybeProp('price', item)

// getNestedPrice :: cart -> Option a
const getNestedPrice = (cart) => getItem(cart).chain(getPrice)

getNestedPrice({}) // None()
getNestedPrice({ item: { foo: 1 } }) // None()
getNestedPrice({ item: { price: 9.99 } }) // Some(9.99)
```

`Option` также известна, как `Maybe`. `Some` иногда называется `Just`, а `None` - `Nothing`.

## Either

__Или__

[Тип-сумма](#sum-type) с двумя вариантами, `Left` и `Right`. По соглашению, `Right` представляет успешное вычисление, а `Left` содержит ошибку или причину провала ("right is right" - правый есть правильный).

`Either` полезен для обработки ошибок без исключений, позволяя вычислениям мягко (gracefully) проваливаться, оставаясь [чистыми](#pure-function) и компонуемыми:

```javascript
const Left = (x) => ({
  value: x,
  map: (_f) => Left(x),
  chain: (_f) => Left(x),
  fold: (f, _g) => f(x),
  isLeft: true
})

const Right = (x) => ({
  value: x,
  map: (f) => Right(f(x)),
  chain: (f) => f(x),
  fold: (_f, g) => g(x),
  isRight: true
})

// parseJson :: String -> либо String Object
const parseJson = (str) => {
  try {
    return Right(JSON.parse(str))
  } catch (err) {
    return Left(err.message)
  }
}

parseJson('{"user": "hemanth"}').map((obj) => obj.user) // Right('hemanth')
parseJson('invalid json').map((obj) => obj.user) // Left('Unexpected token...')
```

__Дополнительные материалы__
* [Either](https://github.com/fantasyland/fantasy-land#either)
* [Folktale Result](https://folktale.origamitower.com/api/v2.3.0/en/folktale.result.html)

## Function

__Функция__

Функция `f :: A => B` - это выражение (часто называемое стрелочным или лямбда-выражением), принимающее ровно один (неизменяемый) параметр типа `A` ​​и возвращающее ровно одно значение типа `B`. Это значение полностью определяется аргументом, благодаря чему функции не зависят от контекста и обладают свойством [ссылочной прозрачности](#referential-transparency). Подразумевается, что функция не должна вызывать никаких скрытых [побочных эффектов](#side-effects); по определению, такая функция всегда является [чистой](#pure-function). Эти свойства делают работу с функциями удобной: они полностью детерминированы и, следовательно, предсказуемы. Функции позволяют работать с кодом как с данными, обеспечивая абстрагирование от поведения:

```javascript
// times2 :: Number -> Number
const times2 = n => n * 2

;[1, 2, 3].map(times2) // [2, 4, 6]
```

## Partial function

__Частичная функция__

Частичная функция - это [функция](#function), которая определена не для всех аргументов: она может вернуть неожиданный результат или вообще не завершить выполнение. Частичные функции создают дополнительную когнитивную нагрузку, их сложнее анализировать, и они могут приводить к ошибкам во время выполнения. Вот несколько примеров:

```javascript
// Пример 1: сумма списка
// sum :: [Number] -> Number
const sum = arr => arr.reduce((a, b) => a + b)
sum([1, 2, 3]) // 6
sum([]) // TypeError: Reduce of empty array with no initial value

// Пример 2: получение первого элемента списка
// first :: [A] -> A
const first = a => a[0]
first([42]) // 42
first([]) // undefined
// Или даже хуже:
first([[42]])[0] // 42
first([])[0] // Uncaught TypeError: Cannot read property '0' of undefined

// Пример 3: выполнение функции N раз
// times :: Number -> (Number -> Number) -> Number
const times = n => fn => n && (fn(n), times(n - 1)(fn))
times(3)(console.log)
// 3
// 2
// 1
times(-1)(console.log)
// RangeError: Maximum call stack size exceeded
```

### Dealing with partial functions

__Работа с частичными функциями__

Частичные функции опасны, и обращаться с ними следует с большой осторожностью. Можно получить неожиданный (неверный) результат или столкнуться с ошибками во время выполнения. Иногда частичная функция может вообще не вернуть никакого значения. Учет всех подобных граничных случаев и соответствующая их обработка могут стать весьма утомительным занятием. К счастью, частичную функцию можно преобразовать в обычную (или тотальную (total)). Мы можем задать значения по умолчанию или использовать "защитников" (guards) для обработки входных данных, для которых исходная частичная функция не была определена. Используя тип [`Option`](#Option), мы можем возвращать `Some(value)` или `None` в тех ситуациях, когда в противном случае поведение программы было бы непредсказуемым:

```javascript
// Пример 1: сумма списка
// Можно предоставить дефолтное значение, чтобы функция всегда возвращала какой-то результат
// sum :: [Number] -> Number
const sum = arr => arr.reduce((a, b) => a + b, 0)
sum([1, 2, 3]) // 6
sum([]) // 0

// Пример 2: получение первого элемента списка
// Меняем результат на Option
// first :: [A] -> Option A
const first = a => a.length ? Some(a[0]) : None()
first([42]).map(a => console.log(a)) // 42
first([]).map(a => console.log(a)) // console.log не будет выполнен
// Предыдущий худший результат
first([[42]]).map(a => console.log(a[0])) // 42
first([]).map(a => console.log(a[0])) // не будет выполнен, поэтому не возникнет ошибки
// Благодаря типу возвращаемого значения (Option) мы понимаем,
// что для доступа к данным нужно использовать метод `.map`,
// и никогда не забудем проверить входные данные,
// поскольку такая проверка встроена в саму функцию

// Пример 3: выполнение функции N раз
// Следует обеспечить обязательное завершение функции путем изменения условий:
// times :: Number -> (Number -> Number) -> Number
const times = n => fn => n > 0 && (fn(n), times(n - 1)(fn))
times(3)(console.log)
// 3
// 2
// 1
times(-1)(console.log)
// Ничего не будет выполнено
```

Преобразование частичных функций в полные позволяет предотвратить подобные ошибки времени выполнения. Кроме того, гарантированный возврат значения делает код более простым в сопровождении и анализе.

## Total function

__Полная фукнция__

Функция, возвращающая корректный результат для всех входных данных, определенных в ее типе. Это противоположность [частичных функций](#partial-function), которые могут вызвать ошибку, вернуть неожиданный результат или не завершить выполнение.

## Библиотеки функционального программирования на JavaScript

* [mori](https://github.com/swannodette/mori)
* [Immutable](https://github.com/facebook/immutable-js/)
* [Immer](https://github.com/mweststrate/immer)
* [Ramda](https://github.com/ramda/ramda)
* [ramda-adjunct](https://github.com/char0n/ramda-adjunct)
* [ramda-extension](https://github.com/tommmyy/ramda-extension)
* [Folktale](http://folktale.origamitower.com/)
* [monet.js](https://cwmyers.github.io/monet.js/)
* [lodash](https://github.com/lodash/lodash)
* [Underscore.js](https://github.com/jashkenas/underscore)
* [Lazy.js](https://github.com/dtao/lazy.js)
* [maryamyriameliamurphies.js](https://github.com/sjsyrek/maryamyriameliamurphies.js)
* [Haskell in ES6](https://github.com/casualjavascript/haskell-in-es6)
* [Sanctuary](https://github.com/sanctuary-js/sanctuary)
* [Crocks](https://github.com/evilsoft/crocks)
* [Fluture](https://github.com/fluture-js/Fluture)
* [fp-ts](https://github.com/gcanti/fp-ts)
