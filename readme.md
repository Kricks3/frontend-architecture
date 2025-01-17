# Spa Architecture

- [Демо приложение](#%D0%B4%D0%B5%D0%BC%D0%BE-%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B5)
  * [Установка](#%D1%83%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0)
  * [Вход](#%D0%B2%D1%85%D0%BE%D0%B4)
- [Основные идеи](#%D0%BE%D1%81%D0%BD%D0%BE%D0%B2%D0%BD%D1%8B%D0%B5-%D0%B8%D0%B4%D0%B5%D0%B8)
  * [Фичи](#%D1%84%D0%B8%D1%87%D0%B8)
    + [Страницы](#%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D1%8B)
  * [Состояние](#%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D0%B5)
    + [Иерархия состояния](#%D0%B8%D0%B5%D1%80%D0%B0%D1%80%D1%85%D0%B8%D1%8F-%D1%81%D0%BE%D1%81%D1%82%D0%BE%D1%8F%D0%BD%D0%B8%D1%8F)
    + [Модель](#%D0%BC%D0%BE%D0%B4%D0%B5%D0%BB%D1%8C)
    + [Стадия объявления и стадия инициализации. Структура модели.](#%D1%81%D1%82%D0%B0%D0%B4%D0%B8%D1%8F-%D0%BE%D0%B1%D1%8A%D1%8F%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D1%8F-%D0%B8-%D1%81%D1%82%D0%B0%D0%B4%D0%B8%D1%8F-%D0%B8%D0%BD%D0%B8%D1%86%D0%B8%D0%B0%D0%BB%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%B8-%D1%81%D1%82%D1%80%D1%83%D0%BA%D1%82%D1%83%D1%80%D0%B0-%D0%BC%D0%BE%D0%B4%D0%B5%D0%BB%D0%B8)
    + [Структура модели](#%D1%81%D1%82%D1%80%D1%83%D0%BA%D1%82%D1%83%D1%80%D0%B0-%D0%BC%D0%BE%D0%B4%D0%B5%D0%BB%D0%B8)
    + [Соглашение об именовании юнитов модели](#%D1%81%D0%BE%D0%B3%D0%BB%D0%B0%D1%88%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BE%D0%B1-%D0%B8%D0%BC%D0%B5%D0%BD%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B8-%D1%8E%D0%BD%D0%B8%D1%82%D0%BE%D0%B2-%D0%BC%D0%BE%D0%B4%D0%B5%D0%BB%D0%B8)
  * [Представление](#%D0%BF%D1%80%D0%B5%D0%B4%D1%81%D1%82%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5)
    + [Стили.](#%D1%81%D1%82%D0%B8%D0%BB%D0%B8)
  * [DAL](#dal)
  * [Библиотеки и хелперы](#%D0%B1%D0%B8%D0%B1%D0%BB%D0%B8%D0%BE%D1%82%D0%B5%D0%BA%D0%B8-%D0%B8-%D1%85%D0%B5%D0%BB%D0%BF%D0%B5%D1%80%D1%8B)
- [Работа с формами.](#%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B0-%D1%81-%D1%84%D0%BE%D1%80%D0%BC%D0%B0%D0%BC%D0%B8)
- [Общая структура проекта](#%D0%BE%D0%B1%D1%89%D0%B0%D1%8F-%D1%81%D1%82%D1%80%D1%83%D0%BA%D1%82%D1%83%D1%80%D0%B0-%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82%D0%B0)
- [Тестирование](#%D1%82%D0%B5%D1%81%D1%82%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5)
- [Оптимизация производительности.](#%D0%BE%D0%BF%D1%82%D0%B8%D0%BC%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D1%8F-%D0%BF%D1%80%D0%BE%D0%B8%D0%B7%D0%B2%D0%BE%D0%B4%D0%B8%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D0%BE%D1%81%D1%82%D0%B8)


Данный репозиторий содержит описание архитектуры и рекомендации по проектированию фронтенда на javascript (typescript) в компании "42 пикселя".
Отдельные аспекты архитектуры были рождены внутри компании, отдельные являются общепринятыми в сообществе хорошими практиками.

Помимо документации, репозиторий также содержит пример приложения, реализующего все ключевые идеи ```examples/react```.

Демонстрационный пример реализован на стеке React + EffectorJS. Все листинги, приводимые ниже, также содержат код на React. 

Для хорошего понимания требуется знание стейт-менеджера  [Effector](https://effector.now.sh/docs/introduction/installation).


# Демо приложение

Демо приложение представляет собой простой не публичный (требуется вход) каталог товаров с возможностью добавления товаров в корзину. 

В качестве бэкенда используется миниатюрный мок-сервер (запускается автоматически вместе с webpack-dev-server)

## Установка

```
$ cd examples/react
$ npm ci
$ cp .env.example .env
```

Запуск webpack dev server:
```
$ npm run start
```

Сборка production бандла:
```
$ npm run build
```
Запуск unit-тестов:
```
$ npm run test
```

## Вход 
```
42px
123
```

# Основные идеи

Любое клиентское приложение, в самом первом приближении состоит из следующих слоев:

1. Представление (компоненты и стили)
2. Состояние (пользовательский ввод, данные для вывода, состояние элементов)
3. Слой взаимодействия с внешними источниками данных (RESTful API, GraphQL, клиенсткая СУБД, etc)

В зависимости от степени проработки архитектуры, фанатазии разработчиков, времени отведенного на проект, размера проекта и прочих факторов, данные слои могут быть склеены и перемешаны друг с другом практически любым образом. 

Ключевая идея описываемой архитектуры заключается в том, что все три указанных слоя отделены друг от друга и взаимодействуют только посредством определенного API.


## Фичи

Для организации структуры проекта мы используем подход, известный как FeatureSlices. Этот родом из мира .NET и был адаптирован сообществом для современных spa.

Суть подхода заключается в том что основные элементы приложения разбиваются на **фичи**.

Каждая фича - это совокупность компонентов (представление), состояния и бизнес логики, несущая конкретную, определенную бизнес ценность.
Фичи обладают знанием о предметной области и не абстрагированы от нее.

По этой причине, фичи могут переиспользоваться между разными частями одного приложения, или даже между разными приложениями в составе одного проекта (например между мобильным приложением и веб-клиентом, если это позволяет стек). Но фичи никогда не переиспользуются в двух различных проектах. 

В нашем демо-примере фичи расположены в каталоги features.

Каждая фича обладает следующей структурой:
```
model - директория, которая содержит состояние и бизнес-логику
view - директория, которая содержит представления (компоненты)
```

Внутри каждой из двух папок находится index-файл. index файл формирует публичное API модели и представлений данной фичи. 

Фичи могут импортировать друг друга ТОЛЬКО через публичное апи. 
Несмотря на то, что технически ничто не мешает импортировать напрямую "из кишков" фичи так делать не стоит, так как это нарушает инкапсуляцию.

**Хорошо**
```ts
import { addToCart } from '@/features/cart/model'
import { Cart } from '@/features/cart/view'
```

**Плохо**
```ts
import { event } from 'features/cart/view/entries/Cart'
```

Любая фича теоретически (и практически) может быть вынесена в отдельный репозиторий/npm модуль, если этого потребует масштаб проекта. 

Корректное разбиение функциональности проекта на фичи есть своеобразное искусство, и понимание того как это делать правильно приходит с опытом.

Общая рекомендация в следующем: не стоит бояться делать маленькие фичи. 
Фича "auth" - это скорее всего неудачно выделенная огромная фича. И лучше выделить из нее отдельные фичи "sign-in", "sign-up", "password-recovery".

В некоторых приложениях удобно выделять фичу "app" или "app-init", которая содержит глобальное состояние и логику инициализации приложения.

В демо-проекте фичи находятся в каталоге ```src/features```. На данном этапе рекомендуется поверхностно изучить его содержимое.


Подробнее о feature slices можно почитать [здесь](https://t.me/feature_slices) (проскроллить до самого верха и читать сверху вниз). Стоит иметь в виду: там приводится пример на стеке React + Redux, однако, все основные идеи применимы и к нашему стеку. 

### Страницы

На практике мы пришли к необходимости выделения в отдельную директорию фич особого рода: фичи-страницы. 
Эти фичи находятся в директории pages (или screens в случае React Native). 

Страницы импортируют отдельные логические компоненты интерфейса из разных фич, собирают их в компоненты страниц и экспортируют наружу (впоследствие они импортируются в роутере). 

Страницы, как и обычные фичи, могут содержать модель и простую логику. 

В отношении страниц действуют два важных ограничения:
1. Страницы могут содержать только простую "лэйаут-логику" - то есть управлять отображением/скрытием отдельных элементов стораницы. Вся бизнес-логика должна оставаться в фичах
2. Страницы импортируют компоненты из фич. Страницы никогда (!) не могут импортироваться внутрь фич

Помимо чисто удобства организации файлов (все страницы в одном месте), страницы являются одной из меры борьбы с циклическими зависимостями через компоненты. 

## Состояние
### Иерархия состояния 

Все состояние в клиентский приложениях можно разделить на три категории (последние две часто объединяют, но для наших целей важно подчеркнуть различие):

1. **Application state** (global state, common state) глобальное состояние, которое может быть востребовано во многих, не связанных друг с другом, частях приложения: профиль текущего пользователя, данные для нотификации, etc
2. **Local state** (ephemeral state) локальное состояние отдельных независимых частей приложения: пользовательский ввод в формах, данные для вывода пользователю (каталог товаров, новости, список постов, комментари)
3. **Element state** состояние конкретного элемента интерфейса: закрыт/открыт выпадающий список, меню или датапикер, активный таб, etc 

Одна из ключевых идей данной архитектуры заключается в следующем

> Как глобальное состояние приложение (Application state), так и состояние его частей (Local state) хранится *только* в эффектор-сторах. Внутри компонентов (```React.useState```) допустимо хранить *только* состояние элементов. 

Глобальное состояние хранится внутри фич "app", "profile", "user" или подобных им фичах. Все прочее локальное состояние - внутри остальных фич.

Ниже будет подробно описан способ организации состояния, вплоть до его распределения по директории.


### Модель

Под моделью приложения в целом подразумевается его состояние и API для изменения этого состояния. При использовании эффектора (в отличие от redux) модель является децентрализованной. Каждый отдельный "кусочек" модели представляет собой набор условно независимых (от остального приложения) связанных друг с другом данных (`effector.Store`), событий (`effector.Event`) и эффектов(`effector.Effect`). В дальнейшем, каждый такой "кусочек" мы тоже будем называть словом "модель". 

Часть данных и событий экспортируется во внешний мир (и может быть использована другой моделью), часть является приватной и используется только внутри данной модели.
Отдельные модели могут связываться друг с другом и взаимодействовать (но только через публичное API). 

Мы рекомендуем использовать [домены](https://effector.now.sh/docs/api/effector/domain) и упаковывать каждую отдельную модель в домен. Это делает объявление сторов и эффектов более изящным, уменьшая количество импортов, упрощает тестирование, позволит одномоментно навешивать некоторое событие на все сторы данной модели используя хуки доменов (это актуально для события reset), а так же упроситит введрение server side rendering, если он, не дай бог, понадобится в будущем. 

С целью упрощения тестирования, рекомендуется помещать все домены моделей в единый на всё приложение корневой домен. Такой подход значительно упрощает тестирование: достаточно сделать fork корневого домена чтобы получить чистый, независимый скоуп состояния приложения, не беспокоясь о сайд-эффектах при тестировании. 


### Стадия объявления и стадия инициализации. Структура модели. 
Эффектор модели создаются в две стадии:

1. Стадия объявления. На этой стадии создаются сторы, эвенты и эффекты. 
```typescript
export const catalog = root.domain('catalog')

export const $productsList = catalog.store<Product[]>([])

export const init = catalog.event<void>()
export const reset = catalog.event<void>()

export const getProductsFx = attach({
  effect: productsClient.getProductsReqFx,
  mapParams: () => ({ limit: PRODUCTS_PAGINATION_LIMIT, offset: 0 }),
})
```

2. Стадия инициализации. На этой стадии связываются сторы, эвенты и эффекты, объявляются сайд-эффекты. 
```typescript
// reset all stores on 'reset' event
catalog.onCreateStore((store) => store.reset(reset))

/* use cases logic */
$productsList.on(
  getProductsFx.doneData,
  (currentList, products) => [...currentList, ...products],
)

// get products on init
forward({
  from: init,
  to: getProductsFx,
})
```

Очень важно, разделить эти две стадии по различным модулям (файлам). 
1. В модулях с объявлениями создаются сторы, эвенты и эффекты без какой либо бизнес логики. Эти модули *могут* и должны экспортировать во внешний мир. 
2. В модулях инициализации содержится *только* чистая бизнес логика. Эти модули *никогда* ничего не экспортируют. 

Тут можно задаться логичным вопросом: как же бизнес логика, содержащаяся в модулях инициализации вообще попадет в бандл? Через точку входа. 
[Точка входа](examples/react/src/index.tsx) импортирует модуль [init.ts](examples/react/src/init.ts) в котором импортируются init модули из всех модулей приложения. 


Пробегитесь по этим цепочкам импортов в демо примере чтобы лучше понять о чем идет речь:
```
src/index.tsx > src/init.ts > src/features/app/init.ts > src/fetures/app/model/init.ts
src/index.tsx > src/init.ts > src/features/products-list/init.ts > src/fetures/products-list/model/init.ts
src/index.tsx > src/init.ts > src/features/cart/init.ts > src/fetures/cart/model/init.ts
```

Каждая фича предоставляет init файл, в котором импортит init файлы своих моделей (если их несколько). Это нужно для инкапсуляции содержимого модуля: точка входа не должна знать о том какие модели содержатся внутри модулей, она просто импортит ```feature/init```

Здесь можно задаться вопросом: "зачем разбивать бизнес-логику и объявления по разным модулям? Почему бы не написать все в одном месте?". И на то есть две очень веские причины:
1. (субъективная) Разбиение на отдельные модули улучшает читаемость модели. Читая бизнес логику вы не отвлекаетесь на рутинные объявления сущностей 
2. (объективная) Разибение на отдельные модули поможет избежать падения вашего приложения, если в нем вдруг обнаружаться цилкические зависимости. 

Если с первым пунктом все ясно, то на втоом остановимся подробнее. 
Да, любое современное окружение (включая webpack+typescript+es6 modules) легко справляется с циклическими зависимостями. 
Однако, любой алгоритм разрешения циклических зависимостей (включая тот который используется в webpack) допускает ситуацию, при которой В НЕКОТОРЫЙ момент инициализации приложения оказывается невозможно предоставить модулю его зависимость (она будет предоставлена позднее).
В случае wepack в этот момент времени эта переменная будет undefined. 
Это создает проблемы, так как наши модули инициализации моделей содержат сайд-эффекты и обязательно требуют наличия всех своих зависимостей:

```ts
import { someEvent } from '../../antoherModel'
import { $someStore } from './state'

$foo.on(someEvent, (prevState, payload) => ({ ...prevState, ...payload }))
```

Если на момент того, как любой модуль нашего приложения импортировал данный модуль, переменная someEvent окажется undefined (из за циклической зависимости) это приведет к исключению в глобальной области, которое почти наверняка уронит все приложение. 

Чтобы избежать этой неприятной ситуации, мы отделяем бизнес логику в отдельный файл, который импортится непосредственно в точке входа, причем ПОСЛЕ всего остального. В этот момент все фичи и страницы уже импортированы и возможные цилкические зависимости разрешены, поэтому мы можем быть уверен что не наткнемся на undefined. 

Описанная здесь схема в действительности является частью общего правила, применимого не только к эффектор моделям:
> Сайд-эффекты в корне модуля, который экспортирует что-либо недопустимы. Такой модуль не должен экспортировать


К слову, эта проблема актуальна даже при использовании сервис-контейнеров. Как правило любая реализация сервис-контейнера жестко разделяет стадию создания и стадию инициализации, на которой допустимы сайд-эффекты. 


P. S. 
Помните, что любой вызов функции, в который в качестве аргумента передается переменная, импортированная из другого модуля - это потенциальный сайд-эффект. Более того, вызов любой функции, которая может выбросить исключение - это сайд-эффект (речь идет не о багах, а об ожидаемых исключениях)

Этот код содержит сайд эффекты
```ts
someFunc(a)
JSON.parse(b)
```

Этот код не содержит сайдэффекты
```ts
const $s = createStore({ a: 0 })
const client = new HttpClient()
```

Отделение создания от инициализации является хорошей утоявшейся практикой в эффектор-сообществе 
https://effector.now.sh/docs/conventions/best-practices#file-structure


### Структура модели

В дополнение к вышесказаному, мы также рекомендуем разделять юниты модели на *публичные* и *приватные*. 

Также бывает удобно выносить в отдельный модуль обработчики эвентов (редьюсеры), если они становятся слишком велики и ухудшают читаемость модели.

Таким образом, наша модель приобретает следующую структуру:
```
public.ts - внешние "публичные" юниты модели
private.ts - приватные юниты модели 
reducers.ts - обработчики событий (опциональны)
init.ts - бизнес логика, связывание сторов и эвентов, никогда не экспортирует
index.ts - точка входа, реэкспорт все юниты из public
```

Объявленные в public.ts публичные юниты реэкспортируются во внешний мир в точке входа модели (index.ts). 
Объявленные в private.ts приватные юниты НИКОГДА не должны экспортироваться за пределы фичи. Эти юниты допускается импортить только в init.ts этой же модели, или в представлениях этой же фичи. 

Если определенное приватное событие или состояние требуется "отдать" во внешний мир - создайте второе публичное событие и связите их через forward в init.ts:


public.ts:
```ts
export const publicEvent = domain.event<void>()
export const $publicState = domain.store<Item[]>()
```

private.ts:
```ts
export const privateEvent = domain.event<void>()
export const $privateState = domain.store<Item[]>()
```

init.ts:
```ts
import { forward } from 'effector'
import { publicEvent, $publicState } from './public.ts'
import { privateEvent, $privateState } from './private.ts'

forward({
  from: publicEvent,
  to: privateEvent,
})

forward({
  from: $privateState,
  to: $publicState,
})
```

Подобная практика, в сочетании с разделением объявления и инициализации позволяет:
1. Полностью избежать проблем с циклическими зависимосятми между моделями
2. Явно и прозрачно выделить публичное API через которое внешние модели могут изменять её состояние

Не создавайте пустые файлы только "Ради структуры". Если в данной модели нет данного модуля - не делайте его. 

### Соглашение об именовании юнитов модели

Все эвенты публичного API можно разделить на push и pull эвенты:

* push эвенты совершают некоторое действие со своей моделью (изменяют состояние или совершают сайд-эффекты). Push эвенты *вызываются* внешней моделью.
* pull эвенты уведомляют внешнюю модель о некотором событии. На pull эвенты *подписывается* внешняя модель. 

Чтобы визуально видеть разницу между двумя этими типами эвентов мы рекомендуем следовать соглашению:
1. push эвенты именуются в инфинитиве в повелительном наклонении: addToCart, selectItem, doSomething
2. pull эвенты всегда начинаются с on: onItemAdded, onItemSelected, onSomethingHappened

Все сторы должны именоваться с префиксом $: $cart, $items...
Все эффекты должны именоваться с постфиксом Fx: signInFx, getProductsFx...

## Представление

Представление реализуется как React-компоненты. Все компоненты можно разделить на две различные категории:

1. Доменные компоненты. Эти компоненты обладают знанием о предметной области проекта, могут обладать доступом к локальному или глобальному состоянию приложения, доступом к локализации и роутингу. Примеры доменных компонентов: LoginForm, RegisterForm, ProductsList, ConfirmDeletionModal.
2. Презентационные или UI компоненты. Являются "чистыми" (речь не идёт о pure-компонентах) компонентами, реализующими определенные элементы пользовательского интерфейса. Не могут обладать доступом к состоянию приложения, локализации или роутингу. Могут содержать собственное состояние. Примеры UI-компонентов: PrimaryButton, DropDown, Modal, InputField.

Доменные компоненты являются непереиспользуемой частью приложения. UI компоненты, напротив, не завязаны на предметную область и могут переиспользоваться. 

Доменные компоненты находятся в папке ```view``` соответствующей им фичи:
```
features/catalog/view
features/app/view
features/sign-in/view
```

Все презентационные компоненты находятся в папке UI. Это ваша библиотека компонентов. При необходимости (а также при условии того что библиотека компонентов получилась хорошо) они могут быть вынесены в отдельный репозиторий. 

При использовании сторонней библиотеки компонентов, здесь стоит располагать кастомные компоненты + врапперы и адаптеры над компонентами библиотеки. 

Структура библиотеки компонентов может быть различной. В большинстве случаев вполне подойдет одноуровневая структура:
```
src/ui
--PrimaryButton
--Dropdown
--Cart
```

Структура же директории view внутри фичи жестко определена:
```
someFeature/view
--parts
--containers
--entries
--index.ts - точка входа во "view" модели, реэкспортит компоненты из entries
```

В директории parts располагаются любые вспомогательные компоненты, которые нужны исходя из потребностей стилизации, макета или удобства организации верстки. Это лэйауты, шаблоны, строительные блоки. 

В директории containers располагаются компоненты имеющие доступ к состоянию и событиям. 
В папке entries располагаются компоненты, которые экспортируются во внешний мир. 

Таким образом, образуется следующая иерархия (для удобства миграции с atomic design в скобках приводится название соответствующего вида компонентов в atomic):
1. Компоненты внутри parts (atoms, molecules, templates) импортируют UI компоненты прокидывая в них захардкоженные лэйблы, плейсхолдеры и т.п. или связывая их с локализацией. Данные в parts компоненты передаются через props.
2. Компоненты-контейнеры (organisms) импортируют parts компоненты и прокидывают в них состояние и события из модели. При этом, конейнеры вполне могут содержать верстку или импортировать UI компоненты напрямую, если это удобно. Такого запрета нет. 
3. Компоненты entries (organisms/pages) импортируют компоненты из containers и parts собирая их в цельный монолитный кусок интерфейса (некоторая панелька, список, etc) и отдают внешнему миру. Entries компоненты также могут обладать собственной версткой, если это удобно в конкретном случае.

В завершение, дадим еще одну рекомендацию: не бойтесь создавать большое количество контейнеров, каждый из которых присоединяет свой кусочек состояния. Зачастую это лучше, чем расположить все данные внутри одного огромного контейнера (подробнее см. пункт "Оптимизации производительности")

Не создавайте пустые папки только "Ради структуры". Если в данном view нет parts или containers - не создавайте такую директорию.

### Стили. 

Для стилизации и верстки мы используем популярную библиотеку styled-components, реализующую подход css-in-js. 

Хорошей практикой является выделение темы и стилистических переменных. В идеальном мире в переменные следует выносить всё, включая цвета, отступы (соблюдая иерархию отступов), шрифты. В реальном мире тех макетов с которыми мы имеем дело, хорошо бы не хардкодить цвета. 

Пример организации темы можно посмотреть в src/ui/theming.

## DAL 

Слой взаимодействия с внешними данными мы в дальнейшем будем называть DAL (Data Access Layer). 

Данный термин позаимствован из мира серверной разработки (если еще точнее - то из .NET). Однако, весьма удачно описывает роль этого слоя приложения. 

> Источники данных - вещь изменчивая. 

Всем знакома ситуация, когда даже на небольших промежутках времени в живом проекте меняется формат эндпоинтов HTTP-API, добавляются новые источники данных (например в дополнение к HTTP-API появляется socket.io соденинение, или сторонеее HTTP-API) и так далее. 

При этом, типы основных сущностей, как правило, обладает большей стабильностью, так как являются репрезентацией предментной области. 

Наша главная задача - минимизация числа изменений, которые нам потребуется внести при каких-либо изменениях внешних источников данных или их интерфейсов. 

Поэтому, все знание об источниках данных и их интерфейсах инкапсулирует DAL. 

Для внешнего приложения он предоставляет прозрачное API для получения и мутации данных (коллекция эффектов и эвентов)

Самое важное здесь в том, чтобы внешнее приложение ничего не знало даже о том, откуда эти данные приходят. Именно поэтому, соответствующий каталог в демонстрационном приложении назван именно dal, а не "rest-api" или "http". 

DAL может хранить внутри себя состояние, которое непосредственно относится к внешнему источнику данных, например jwt access token. 

Рассмотрим реализацию слоя DAL и его взаимодействие с остальным приложением на нашем демо примере. 

В каталоге ```dal/request``` находится модель: 
1. Cтор ```$accessToken```
2. Cобытия для инициализации и перезагрузки состояния аутентификации ```initAuthState, resetAuthState```
3. События для аутентификации и изменения токена ```authenticate``` и ```tokenChanged``` (на случай если нам понадобится поддерживать механизм рефреша токена)
4. Эффекты-обертки над http-запросами ```requestFx``` и ```authRequestFx```

Вся основная логика расположена в [init.ts](examples/react/src/dal/request/init.ts)
Как видно, здесь связывается стор $accessToken с эвентами аутентификации, предоставляется имплементация для ```requestFx``` и ```authRequestFx```, а также обеспечивает сохранение и чтение токена из localStorage.

Эффекты с внешним API, оборачивающие http-эндпоинты находятся в корне точки входа в файлах [auth.ts](examples/react/src/dal/auth.ts) и [products.ts](examples/react/src/dal/products.ts).

Для маппинга параметров запроса и ответа мы используем attachWrapper из библиотеки [@42px/effector-extra](
https://www.npmjs.com/package/@42px/effector-extra).



Тут стоит обратить внимание на forward в auth.ts:
```typescript
forward({
  from: signInReqFx.doneData.map(({ token }) => token),
  to: authenticate,
})
```

Этот forward автоматически установит ```$accessToken``` при успешном резолве эффекта ```signInFx```, внешнему приложению не нужно об этом беспокоиться.

Все что остается внешнему приложению:
1. Инициализировать состояние аутентификации в тот момент, когда инициализируется само приложение. Это происходит в [features/app/model/init.ts](examples/react/src/features/app/model/init.ts).
2. Импортировать эффекты для получения/мутации данных и присоединять к ним пользовательский ввод. Пример можно посмотреть в модели [sign-in](examples/react/src/features/sign-in/model/private.ts)


Данная схема является лишь одной из возможных. Конкретная реализация внутренностей слоя DAL и его API зависит от задач конкретного приложения, его источников данных и способов аутентификации и авторизации. 

Помимо методов для получения и мутации данных, слой DAL также может предоставлять внешнему приложению типы основных сущностей (в демо примере это ```src/dal/entities.ts```) и моки данных для тестирования. 

*Подытожим:*

> Слой DAL предоставляет внешнему приложению абстрактное, не зависящее от источников данных и их интерфейсов API для получения и мутации данных, типы основных сущностей и моки.

## Библиотеки и хелперы

В процессе работы над проектом, очень часто приходится писать много вспомогательных инструментов, хелперов и утилит. 

Практика показывается, что если вы помещаете их в один файл utils.ts или даже в папку utils - она очень быстро становится свалкой для кучи логически несвязанных функций. 

Вместо этого, мы предлагаем оранизовывать ваш вспомогательные код в тематические библиотеки, которые располагаются в каталоге lib. Хотите написать функцию для специфического форматирования даты? Создайте файл lib/dates.ts и поместите ее туда. Впоследствие, весьма вероятно там появятся новые функции, а может быть когда-нибудь оно превратится в легковесный аналог moment.js. Кто знает. Впоследствие, если библиотека оказываается хороша, ее можно будет вынести в отдельный репозиторий/npm пакет для переиспользования в других проектах

> Не создавайте хелперы, создавайте библиотеки. 


# Работа с формами. 
Для работы с формами мы рекомендуем использовать библиотеку [effector-forms](https://www.npmjs.com/package/effector-forms)

# Общая структура проекта
```
dal
declarations
features
--some-feature
---init.ts
---model
----public.ts
----private.ts
----reducers.ts
----init.ts
----index.ts
---view
----parts
----containers
----entries
----index.ts

pages
--some-page
---init.ts
---model
----public.ts
----private.ts
----reducers.ts
----init.ts
----index.ts
---view
----parts
----containers
----entries
----index.ts


ui
--PrimaryButton.tsx
--Dropdown
--index.ts

lib
```


# Тестирование

Для unit-тестов рекоменуется использовать jest + @testing-library/react (если нужны тесты на компоненты или хуки).

Так как в данной архитектуре компоненты никогда не содержат бизнес-логики и состояния, в большинстве случаев, покрытия тестами моделей достаточно (однако, ничто не мешает тестировать также рендеринг компонентов).

При тестировании модели ОЧЕНЬ важно форкать корневой домен приложения в каждом тесте (или в хуке beforeEach, если параметры форка во всех тестах идентичны) и проверять состояния в рамках заданного скоупа. Это позволяет не думать о сайд-эффектах, а так же значительно облегчает создание мок. Для типобезонасных мок рекомендуется использовать хелперы mockEffects и mockStores из библиотеки [@42px/effector-extra](https://www.npmjs.com/package/@42px/effector-extra):

```ts
const mockCartStorage = () => {
  let cartStorage: CartItem[] = [] 

  return mockEffects()
    .set(writeCartFx, (cart) => {
      cartStorage = cart
    })
    .set(readCartFx, () => cartStorage)
}

let scope: Scope


test('add to cart', async () => {
  scope = fork(root, {
    handlers: mockCartStorage(),
  })
})
```

При тестировании моделей вы просто императивно вызываете события, так как будто бы они являются пользовательским вводом, проверяете значения сторов и количество вызовов эффектов (через jest.fn). 

Обращения к внешнему API подменяются на моки.

Пример юнит-теста на модель можно посмотреть в [features/cart/model/model.spec.ts](examples/react/src/features/cart/model/model.spec.ts)

Покрывать тестами элементарные модели зачастую слишком затратно. Однако, если в модели имеются нетривиальные вычисления, всегда лучше написать тест, чем накликивать в браузере (это действительно экономит время).

Разумеется, тестами следует покрывать создаваемые в процессе работы над проектом библиотеки.

Помните, что какие-то тесты всегда лучше чем никаких. 


# Оптимизация производительности.

Вопросу оптимизации производительности посвещена отдельная [статья](performance.md)




















