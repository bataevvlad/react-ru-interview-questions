## Вопросы на собеседовании React.js

Здесь собраны самые популярные вопросы, задаваемые на русскоязычных собеседованиях front-end разработчиков на React.js.  Тематика вопросов включает в себя как основы JavaScript так и глубокое понимание работы React.js.

**JavaScript**:

<details>
<summary>Какие типы данных существуют в JavaScript?</summary>
<div>
  <ul>
    <li>
      Число <b>«number»</b> - Единый тип число используется как для целых, так и для дробных чисел. Существуют специальные числовые значения Infinity (бесконечность) и NaN (ошибка вычислений). Например, бесконечность Infinity получается при делении на ноль. Ошибка вычислений NaN будет результатом некорректной математической операции.
    </li>
    <li>
      Строка <b>«string»</b>
    </li>
    <li>
      Булевый (логический) тип <b>«boolean»</b>
    </li>
    <li>
      Специальное значение <b>«null»</b> - В JavaScript null не является «ссылкой на несуществующий объект» или «нулевым указателем», как в некоторых других языках. Это просто специальное значение, которое имеет смысл «ничего» или «значение неизвестно».
    </li>
    <li>
       Специальное значение <b>«undefined»</b> - Значение undefined, как и null, образует свой собственный тип, состоящий из одного этого значения. Оно имеет смысл «значение не присвоено». Если переменная объявлена, но в неё ничего не записано, то её значение как раз и есть undefined.
    </li>
    <li>
      Объекты <b>«object»</b> - Первые 5 типов называют «примитивными». Особняком стоит шестой тип: «объекты». Он используется для коллекций данных и для объявления более сложных сущностей. Объявляются объекты при помощи фигурных скобок {...}
    </li>
  </ul>
  <p><i>Источник: <a href ="https://learn.javascript.ru/types-intro">learn.javascript.ru</a></i></p>
</div>
</details>

<details>
<summary>Что такое цикл событий (event loop) и как он работает?</summary>
<div>
  <p>Движок браузера выполняет JavaScript в одном потоке. Для потока выделяется область памяти — стэк, где хранятся фреймы (аргументы, локальные переменные) вызываемых функций.</p>
  <p>Список событий, подлежащих обработке формируют очередь событий. Когда стек освобождается, движок может обрабатывать событие из очереди. Координирование этого процесса и происходит в event loop.</p>
  <p>Это по сути бесконечный цикл, в котором выполняются многочисленные обработчики событий. Если очередь пустая — движок браузера ждет, когда поступит событие. Если непустая — первое в ней событие извлекается и его обработчик начинает выполняться. И так до бесконечности.</p>
   <img src="https://cdn-images-1.medium.com/max/1600/1*quyTIOs2hioCx1jRQ7-ojw.png" />
   <p><i>Источник: <a href ="https://medium.com/@pavelbely/javascript-event-loop-%D0%B2-%D0%BA%D0%B0%D1%80%D1%82%D0%B8%D0%BD%D0%BA%D0%B0%D1%85-%D1%87%D0%B0%D1%81%D1%82%D1%8C-1-a19e4d99f242">Pavel Bely, medium.com</a></i></p>
</div>
</details>

<details>
<summary>Что такое замыкание?</summary>
<div>
  <p>Замыкание — это комбинация функции и лексического окружения, в котором эта функция была объявлена. Это окружение состоит из произвольного количества локальных переменных, которые были в области действия функции во время создания замыкания.</p>
  <p><i>Источник: <a href ="https://developer.mozilla.org/ru/docs/Web/JavaScript/Closures">developer.mozilla.org</a></i></p>
</div>
</details>

<details>
<summary>Что такое прототип объекта в JavaScript?</summary>
<div>
  <p>Объекты в JavaScript можно организовать в цепочки так, чтобы свойство, не найденное в одном объекте, автоматически искалось бы в другом. Связующим звеном выступает специальное свойство __proto__</p>
  <p>Если один объект имеет специальную ссылку __proto__ на другой объект, то при чтении свойства из него, если свойство отсутствует в самом объекте, оно ищется в объекте __proto__. Недостаток этого подхода – он не работает в IE10-.</p>
  <p>К счастью, в JavaScript с древнейших времён существует альтернативный, встроенный в язык и полностью кросс-браузерный способ. Чтобы новым объектам автоматически ставить прототип, конструктору ставится свойство prototype.</p>
  <p>При создании объекта через new, в его прототип __proto__ записывается ссылка из prototype функции-конструктора.</p>
  <p>Значением Person.prototype по умолчанию является объект с единственным свойством constructor, содержащим ссылку на Person.</p>
  <p><i>Источник: <a href ="https://learn.javascript.ru/prototype">learn.javascript.ru</a></i></p>
</div>
</details>

<details>
<summary>Как работает ключевое слово this?</summary>
<div>
  <p>В глобальном контексте выполнения (за пределами каких-либо функций), this ссылается на глобальный объект вне зависимости от использования в строгом или нестрогом режиме.</p>
  <p>В пределах функции значение this зависит от того, каким образом вызвана функция:</p>
  <ul>
  <li>Простой вызов - В этом случае значение this не устанавливается вызовом. Так как этот код написан не в строгом режиме, значением this всегда должен быть объект, по умолчанию - глобальный объект. В строгом режиме, значение this остается тем значением, которое было установлено в контексте исполнения. Если такое значение не определено, оно остается undefined. Для того что бы передать значение this от одного контекста другому необходимо использовать call или apply</li>
  <li>В стрелочных функциях, this привязан к окружению, в котором была создана функция. В глобальной области видимости, this будет указывать на глобальный объект. </li>
  <li>Когда функция вызывается как метод объекта, используемое в этой функции ключевое слово this принимает значение объекта, по отношению к которому вызван метод.</li>
  </ul>
  <p><i>Источник: <a href ="https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Operators/this">developer.mozilla.org</a></i></p>
</div>
</details>

<details>
<summary>Как работают методы apply(), call() и bind()?</summary>
<div>
  <p>Функции в JavaScript никак не привязаны к своему контексту this, с одной стороны, здорово – это позволяет быть максимально гибкими, одалживать методы и так далее.</p>
  <p>Но с другой стороны – в некоторых случаях контекст может быть потерян. Способы явно указать this  - методоы bind, call и apply.</p>
  <ul>
    <li>
      <p>Синтаксис метода call: func.call(context, arg1, arg2, ...)</p>
      <p>При этом вызывается функция func, первый аргумент call становится её this, а остальные передаются «как есть». Вызов func.call(context, a, b...) – то же, что обычный вызов func(a, b...), но с явно указанным this(=context).</p>
    </li>
    <li>
      <p>Если нам неизвестно, с каким количеством аргументов понадобится вызвать функцию, можно использовать более мощный метод: apply. Вызов функции при помощи func.apply работает аналогично func.call, но принимает массив аргументов вместо списка.</p>
      <p>
        func.call(context, arg1, arg2) идентичен вызову func.apply(context, [arg1, arg2]);
      </p>
    </li>
    <li>
      <p>Синтаксис встроенного bind: var wrapper = func.bind(context[, arg1, arg2...])</p>
      <p>Методы bind и call/apply близки по синтаксису, но есть важнейшее отличие. Методы call/apply вызывают функцию с заданным контекстом и аргументами. А bind не вызывает функцию. Он только возвращает «обёртку», которую мы можем вызвать позже, и которая передаст вызов в исходную функцию, с привязанным контекстом.</p>
    </li>
  </ul>
  <p>
    <i>Источник:
      <br/>
      <a href ="https://learn.javascript.ru/call-apply#metod-apply">javascript.ru - call и apply</a>
      <br/>
      <a href ="https://learn.javascript.ru/bind#bind">javascript.ru - bind</a>
    </i>
  </p>
</div>
</details>

<details>
<summary>Что такое Promise (Промис)?</summary>
<div>
  <br/>
  <p>Promise – это специальный объект, который содержит своё состояние. Вначале pending («ожидание»), затем – одно из: fulfilled («выполнено успешно») или rejected («выполнено с ошибкой»).</p>
  <p>
    Синтаксис создания Promise:

    var promise = new Promise(function(resolve, reject) {
      // Эта функция будет вызвана автоматически

      // В ней можно делать любые асинхронные операции,
      // А когда они завершатся — нужно вызвать одно из:
      // resolve(результат) при успешном выполнении
      // reject(ошибка) при ошибке
    })
  </p>
  <p>
    Универсальный метод для навешивания обработчиков:
    
    promise.then(onFulfilled, onRejected)
    
  <ul>
    <li>onFulfilled – функция, которая будет вызвана с результатом при resolve.</li>
    <li>onRejected – функция, которая будет вызвана с ошибкой при reject.</li>
  </ul>
    Для того, чтобы поставить обработчик только на ошибку, вместо .then(null, onRejected) можно написать .catch(onRejected) – это то же самое.
  </p>
  <p>
    Возьмём setTimeout в качестве асинхронной операции, которая должна через некоторое время успешно завершиться с результатом «result»:
  
    // Создаётся объект promise
    let promise = new Promise((resolve, reject) => {

      setTimeout(() => {
        // переведёт промис в состояние fulfilled с результатом "result"
        resolve("result");
      }, 1000);

    });

    // promise.then навешивает обработчики на успешный результат или ошибку
    promise
      .then(
        result => {
          // первая функция-обработчик - запустится при вызове resolve
          alert("Fulfilled: " + result); // result - аргумент resolve
        },
        error => {
          // вторая функция - запустится при вызове reject
          alert("Rejected: " + error); // error - аргумент reject
        }
      );
   В результате запуска кода выше – через 1 секунду выведется «Fulfilled: result».
  </p>
  <p><i>Источник: <a href ="https://learn.javascript.ru/promise">javascript.ru</a></i></p>
</div>
</details>

<br/>

**React**:

<details>
<summary>Какие методы жизненного цикла компонента существуют в React?</summary>
<div>
  <ul>
     <li>
       <b>render()</b> — единственный обязательный метод в классовом компоненте.
       <br>
       При вызове он проверяет this.props и this.state и возвращает один из следующих вариантов: Элемент React, Массивы и фрагменты, Порталы, Строки и числа, Booleans или null
     </li>
    <br/>
    <li>
      <b>constructor()</b> - Конструктор компонента React вызывается до того, как компонент будет примонтирован. В начале конструктора необходимо вызывать super(props). Если это не сделать, this.props не будет определён. Это может привести к багам.
      <br>
      Конструкторы в React обычно используют для двух целей: Инициализация внутреннего состояния через присвоение объекта this.state. Привязка обработчиков событий к экземпляру.
      <br>
      Конструктор — единственное место, где можно напрямую изменять this.state. В остальных методах необходимо использовать this.setState().
    </li>
    <br/>
    <li>
      <b>componentDidMount()</b> - вызывается сразу после монтирования (то есть, вставки компонента в DOM). В этом методе должны происходить действия, которые требуют наличия DOM-узлов. Это хорошее место для создания сетевых запросов.
      <br/>
      Этот метод подходит для настройки подписок. Но не забудьте отписаться от них в componentWillUnmount().
    </li>
    <br/>
    <li>
      <b>componentDidUpdate(prevProps, prevState, snapshot)</b> - вызывается сразу после обновления. Не вызывается при первом рендере. Метод позволяет работать с DOM при обновлении компонента. Также он подходит для выполнения таких сетевых запросов, которые выполняются на основании результата сравнения текущих пропсов с предыдущими. Если пропсы не изменились, новый запрос может и не требоваться.
    </li>
    <br/>
    <li>
      <b>componentWillUnmount()</b> - вызывается непосредственно перед размонтированием и удалением компонента. В этом методе выполняется необходимый сброс: отмена таймеров, сетевых запросов и подписок, созданных в componentDidMount().
    </li>
    <br/>
    <li>
      <b>shouldComponentUpdate(nextProps, nextState)</b> - вызывается перед рендером, когда получает новые пропсы или состояние. Значение по умолчанию равно true. Этот метод нужен только для повышения производительности.. Но не опирайтесь на его возможность «предотвратить» рендер, это может привести к багам. Вместо этого используйте PureComponent, который позволяет не описывать поведение shouldComponentUpdate() вручную. PureComponent поверхностно сравнивает пропсы и состояние и позволяет не пропустить необходимое обновление.
    </li>
    <br/>
    <li>
      <b>static getDerivedStateFromProps(props, state)</b> - вызывается непосредственно перед вызовом метода render, как при начальном монтировании, так и при последующих обновлениях. Он должен вернуть объект для обновления состояния или null, чтобы ничего не обновлять.
      <br/>
      Этот метод существует для редких случаев, когда состояние зависит от изменений в пропсах. 
    </li>
    <br/>
    <li>
      <b>getSnapshotBeforeUpdate(prevProps, prevState)</b> - вызывается прямо перед этапом «фиксирования» (например, перед добавлением в DOM). Он позволяет вашему компоненту брать некоторую информацию из DOM (например, положение прокрутки) перед её возможным изменением. Любое значение, возвращаемое этим методом жизненного цикла, будет передано как параметр componentDidUpdate().
    </li>
    <br/>
    <li>
      <b>static getDerivedStateFromError(error)</b> - Этот метод жизненного цикла вызывается после возникновения ошибки у компонента-потомка. Он получает ошибку в качестве параметра и возвращает значение для обновления состояния. getDerivedStateFromError() вызывается во время этапа «рендера». Поэтому здесь запрещены любые побочные эффекты, но их можно использовать в componentDidCatch().
    </li>
    <br/>
    <li>
      <b>componentDidCatch(error, info)</b> - Этот метод жизненного цикла вызывается после возникновения ошибки у компонента-потомка. Он получает два параметра: error — перехваченная ошибка, info — объект с ключом componentStack, содержащий информацию о компоненте, в котором произошла ошибка. Метод можно использовать для логирования ошибок.
    </li>
  </ul>
  <img src='https://cdn-images-1.medium.com/max/1600/1*cPwvUhZrnB1dtZnjBEfXfA.png' />
  <p><i>Источник: <a href ="https://ru.reactjs.org/docs/react-component.html#render">ru.reactjs.org</a></i></p>
</div>
</details>

<details>
<summary>Что такое Context в React и для чего он используется?</summary>
<div>
  <br />
  <p>Контекст разработан для передачи данных, которые можно назвать «глобальными» для всего дерева React-компонентов (например, текущий аутентифицированный пользователь, UI-тема или выбранный язык).</p>
  <p>Контекст позволяет избежать передачи пропсов в промежуточные компоненты: 
    
    // Контекст позволяет передавать значение глубоко
    // в дерево компонентов без явной передачи пропсов
    // на каждом уровне. Создадим контекст для текущей
    // UI-темы (со значением "light" по умолчанию).
    const ThemeContext = React.createContext('light');

    class App extends React.Component {
      render() {
        // Компонент Provider используется для передачи текущей
        // UI-темы вниз по дереву. Любой компонент может использовать
        // этот контекст и не важно, как глубоко он находится.
        // В этом примере мы передаём "dark" в качестве значения контекста.
        return (
          <ThemeContext.Provider value="dark">
            <Toolbar />
          </ThemeContext.Provider>
        );
      }
    }

    // Компонент, который находится в середине,
    // теперь не должен явно передавать UI-тему вниз.
    function Toolbar(props) {
      return (
        <div>
          <ThemedButton />
        </div>
      );
    }

    class ThemedButton extends React.Component {
      // Определяем contextType, чтобы получить значение контекста.
      // React найдёт (выше по дереву) ближайший Provider-компонент,
      // предоставляющий этот контекст, и использует его значение.
      // В этом примере значение UI-темы будет "dark".
      static contextType = ThemeContext;
      render() {
        return <Button theme={this.context} />;
      }
    }
  </p>
  <p>Обычно контекст используется, если необходимо обеспечить доступ данных во многих компонентах на разных уровнях вложенности. По возможности не используйте его, так как это усложняет переиспользование компонентов.</p>
  <ul>
    <b>API:</b>
    <li>
      <b>React.createContext</b> - оздание объекта Context. Когда React рендерит компонент, который подписан на этот объект, React получит текущее значение контекста из ближайшего подходящего Provider выше в дереве компонентов.
    </li>
    <li>
      <b>Context.Provider</b> - Каждый объект Контекста используется вместе с Provider компонентом, который позволяет дочерним компонентам, использующим этот контекст, подписаться на его изменения.
    </li>
    <li>
      <b>Class.contextType</b> - В свойство класса contextType может быть назначен объект контекста, созданный с помощью React.createContext(). Это позволяет вам использовать ближайшее и актуальное значение указанного контекста при помощи this.context. В этом случае вы получаете доступ к контексту, как во всех методах жизненного цикла, так и в рендер методе.
    </li>
    <li>
      <b>Context.Consumer</b> - Consumer — это React-компонент, который подписывается на изменения контекста. В свою очередь, это позволяет вам подписаться на контекст в функциональном компоненте. Consumer принимает функцию в качестве дочернего компонента. Эта функция принимает текущее значение контекста и возвращает React-компонент. Передаваемый аргумент value будет равен ближайшему (вверх по дереву) значению этого контекста, а именно пропу value Provider компонента. Если такого Provider компонента не существует, аргумент value будет равен значению defaultValue, которое было передано в createContext().
    </li>
  </ul>
  <p><i>Источник: <a href ="https://ru.reactjs.org/docs/context.html">ru.reactjs.org</a></i></p>
</div>
</details>

<details>
<summary>Что такое Виртуальная DOM?</summary>
<div>
  <br />
  <p>
    Виртуальный DOM (VDOM) — это концепция программирования, в которой идеальное или «виртуальное» представление пользовательского интерфейса хранится в памяти и синхронизируется с «настоящим» DOM при помощи библиотеки, такой как ReactDOM. Этот процесс называется согласованием.
  </p>
  <p>
    Поскольку «виртуальный DOM» — это скорее паттерн, чем конкретная технология, этим термином иногда обозначают разные понятия. В мире React «виртуальный DOM» обычно ассоциируется с React-элементами , поскольку они являются объектами, представляющими пользовательский интерфейс. Тем не менее, React также использует внутренние объекты, называемые «волокнами» (fibers), чтобы хранить дополнительную информацию о дереве компонентов. Их также можно считать частью реализации «виртуального DOM» в React.
  </p>
  <p><i>Источник: <a href ="https://ru.reactjs.org/docs/faq-internals.html">ru.reactjs.org</a></i></p>
</div>
</details>

<details>
<summary>Для чего нужен атрибут key при рендере списков?</summary>
<div>
  <br />
  <p>
    Ключи (keys) помогают React определять, какие элементы были изменены, добавлены или удалены. Их необходимо указывать, чтобы React мог сопоставлять элементы массива с течением времени.
  </p>
  <p>
    Лучший способ выбрать ключ — это использовать строку, которая будет явно отличать элемент списка от его соседей. Чаще всего вы будете использовать ID из ваших данных как ключи. Когда у вас нет заданных ID для списка, то в крайнем случае можно использовать индекс элемента как ключ.
  </p>
  <p><i>Источник: <a href ="https://ru.reactjs.org/docs/lists-and-keys.html">ru.reactjs.org</a></i></p>
</div>
</details>


<details>
<summary>В чем разница между управляемыми (controlled) и не управляемыми (uncontrolled) компонентами?</summary>
<div>
  <br />
  <p> В HTML элементы формы, такие как input, textarea и select, обычно сами управляют своим состоянием и обновляют его когда пользователь вводит данные. В React мутабельное состояние обычно содержится в свойстве компонентов state и обновляется только через вызов setState().
  </p>
  <p>
    В управляемом компоненте с каждой мутацией состояния связана функция-обработчик. Благодаря этому валидация или изменение введённого значения становится простой задачей. Например, если мы хотим, чтобы имя обязательно было набрано заглавными буквами, можно написать такой handleChange:
    
    ```
    handleChange(event) {
      this.setState({value: event.target.value.toUpperCase()});
    }
  </p>
  <p>
    Вместо того, чтобы писать обработчик события для каждого обновления состояния, вы можете использовать неуправляемый компонент и читать значения из DOM через реф.
  
    ```
    class NameForm extends React.Component {
      constructor(props) {
        super(props);
        this.handleSubmit = this.handleSubmit.bind(this);
        this.input = React.createRef();
      }

      handleSubmit(event) {
        alert('Отправленное имя: ' + this.input.current.value);
        event.preventDefault();
      }

      render() {
        return (
          <form onSubmit={this.handleSubmit}>
            <label>
              Имя:
              <input type="text" ref={this.input} />
            </label>
            <input type="submit" value="Отправить" />
          </form>
        );
      }
    }
  </p>
  <p>
    Неуправляемые компоненты опираются на DOM в качестве источника данных и могут быть удобны при интеграции React с кодом, не связанным с React. Количество кода может уменьшиться, правда, за счёт потери в его чистоте. Поэтому в обычных ситуациях мы рекомендуем использовать управляемые компоненты.
  </p>
  <p><i>Источник: <a href ="https://ru.reactjs.org/docs/forms.html#controlled-components">ru.reactjs.org</a></i></p>
</div>
</details>

