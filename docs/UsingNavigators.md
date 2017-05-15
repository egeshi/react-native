---
id: using-navigators
title: Навигаторы
layout: docs
category: Основы
permalink: docs/using-navigators.html
next: more-resources
previous: networking
---

Мобильные приложения редко состоят из единственного экрана. Поэтому, когда вы добавляете второй экран к своему приложению, необходимо учесть как пользователь будет переходить с одного экрана на другой.

Для переходов между разными экранами можно использовать навигаторы. Эти переходы могут представлять собой обычные анимации стека master/detail или вертикальные модальные попапы.

## Навигатор

У React Native есть несколько встроенных компонентов навигации, но для первого приложения вы, вероятно, захотите использовать `Navigator`. Он обеспечивает JavaScript-реализацию стека навигации, и поэтому работает под iOS и Android и достаточно прост в настройке.

![](img/NavigationStack-Navigator.gif)

### Работа со сценами

К этому моменты вы уверенно можете отобразить любые компоненты в вашем мобильном приложении, будь это простой `View`, содержащий `Text` или `ScrollView` со списком Изображений (`Image`). Вместе эти компоненты составляют сцену (синоним для экрана) в вашем мобильном приложении.

Сцена это ничто иное, как компонент React, который обычно занимает всю площадь экрана. Сцена отличается от компонента `Text` или `Image` или даже пользовательского компонента `SpinningBeachball`, которые отображаются как часть экрана. Верятно что вы уже использовали сцены, даже не зная этого: компоненты ["HelloWorldApp"](docs/tutorial.html), the ["FlexDirectionBasics"](docs/flexbox.html) и ["ListViewBasics"](docs/using-a-listview.html), описанные ранее в уроке, все являются примерами сцен.

Давайте создадим простую сцену, которая выводит на экран немного текста. Мы вернемся к ней позже, когда будем добавлять к нашему приложению навигацию. Создайте новый файл по имени "MyScene.js" со следующим содержимым:

```javascript
import React, { Component } from 'react';
import { View, Text, Navigator } from 'react-native';

export default class MyScene extends Component {
  static get defaultProps() {
    return {
      title: 'MyScene'
    };
  }

  render() {
    return (
      <View>
        <Text>Hi! My name is {this.props.title}.</Text>
      </View>
    )
  }
}
```

Обратите внимание на декларацию `export default` перед объявлением компонента. Эта декларация _экспортирует_ компонент и позволит другим компонентам _импортировать_ его позже подобным образом::

```javascript
import React, { Component } from 'react';
import { AppRegistry } from 'react-native';

import MyScene from './MyScene';

class YoDawgApp extends Component {
  render() {
    return (
      <MyScene />
    )
  }
}

AppRegistry.registerComponent('YoDawgApp', () => YoDawgApp);
```

Теперь у нас теперь есть простое приложение, которое отображает вашу сцену и больше ничего. В этом случае `MyScene` - простой пример [допускающего повторное использование компонента React](https://facebook.github.io/react/docs/reusable-components.html).

### Navigator

Довольно о сценах, давайте настроим переходы между экранами. Мы начнем с отображения Навигатора (`Navigator`), а затем `Navigator` отобразит сцену, передавая вашу функцию `render()` своему свойству `renderScene`.

```javascript
render() {
  return (
    <Navigator
      initialRoute={{ title: 'My Initial Scene', index: 0 }}
      renderScene={(route, navigator) => {
        return <MyScene title={route.title} />
      }}
    />
  );
}
```

При работе c навигацией вы будете часто встречать такое понятие как "маршрут". Маршрут это объект, который содержит информацию о сцене. Он используется для того чтобы предоставить весь контекст, который необходим функции навигатора `renderScene` для отображения сцены. Маршрут может содержать любое количество ключей для того чтобы помочь различать вашу сцену, но для нашего примера мы используем единственный ключ - `title`.

#### Добавление сцен в стек

Чтобы перейти к новой сцене, вам нужно узнать про добавление (`push`) и получение (`pop`). Оба этих метода предоставляются компонентом навигатор (`Navigator`), который ранее был передан вашей функции `renderScene`. Как вы наверняка догадались, они нужны чтобы добавлять (`push`) в стек и получать (`pop`) маршруты из стека навигации.

```javascript
navigator.push({
  title: 'Next Scene',
  index: 1,
});

navigator.pop();
```

Более полный пример, демонстрирующий работу с маршрутами. Измените ваш файл index*.j, чтобы он выглядел так:

```javascript
import React, { Component } from 'react';
import { AppRegistry, Navigator, Text, View } from 'react-native';

import MyScene from './MyScene';

class SimpleNavigationApp extends Component {
  render() {
    return (
      <Navigator
        initialRoute={{ title: 'My Initial Scene', index: 0 }}
        renderScene={(route, navigator) =>
          <MyScene
            title={route.title}

            // Функция, которая вызывается, когда мы хотим перейти к следующему экрану (сцене)
            onForward={ () => {    
              const nextIndex = route.index + 1;
              navigator.push({
                title: 'Scene ' + nextIndex,
                index: nextIndex,
              });
            }}

            // Функция для перехода на предыдущий экран
            onBack={() => {
              if (route.index > 0) {
                navigator.pop();
              }
            }}
          />
        }
      />
    )
  }
}

AppRegistry.registerComponent('SimpleNavigationApp', () => SimpleNavigationApp);
```

Также измените файл MyScene.js как в коде ниже:

```javascript
import React, { Component, PropTypes } from 'react';
import { View, Text, TouchableHighlight } from 'react-native';

export default class MyScene extends Component {
  static propTypes = {
    title: PropTypes.string.isRequired,
    onForward: PropTypes.func.isRequired,
    onBack: PropTypes.func.isRequired,
  }
  render() {
    return (
      <View>
        <Text>Current Scene: { this.props.title }</Text>
        <TouchableHighlight onPress={this.props.onForward}>
          <Text>Tap me to load the next scene</Text>
        </TouchableHighlight>
        <TouchableHighlight onPress={this.props.onBack}>
          <Text>Tap me to go back</Text>
        </TouchableHighlight>
      </View>
    )
  }
}
```

В этом примере компоненту `MyScene` передаются заголовок текущего маршрута через свойство `title`. Компонент выводит на экран два интерактивных компонента, которые вызывают функции `onForward` и `onBack` через собственные свойства, которые, в свою очередь, вызовут `navigator.push()` и `navigator.pop()`.

Если вы хотите увидеть больше примеров кода с использованием компонента `Navigator`, обратитесь к [докуменации по Navigator API](docs/navigator.html) или изучите [руководство по навигации](/react-native/docs/navigation.html) чтобы узнать как использовать весь функционал Навигатора.

## Дай пять!

Если вы добрались до этой строки с самого начала урока, то теперь вы довольно серьезный React Native кодер. Поздравляем! Теперь вы наверное захотите узнать больше из [интересных материалов, которые созданы сообществом для описания возможностей React Native](/react-native/docs/more-resources.html).
