---
id: quick-start-getting-started
title: Поехали!
layout: docs
category: Основы
permalink: docs/getting-started.html
next: tutorial
---

Добро пожаловать в React Native! Инструкции на этой странице помогут вам установить React Native на своей системе и вы сразу сможете создать приложение. Если вы уже установили React Native, то сразу переходите к [уроку](/react-native/docs/tutorial.html).

В зависимости от операционной системы , в которой вы ведете разработку, инструкции несколько отличаются для iOS или Android. Если вы собираетесь создавать кроссплатформенные приложения для iOS и Android, это прекрасно - просто выберите целевую ОС и ОС среды разработки ниже, так как процесс установки для разных систем имеет некоторые отличия.

<div class="toggler">
<style>
.toggler a {
  display: inline-block;
  padding: 10px 5px;
  margin: 2px;
  border: 1px solid #05A5D1;
  border-radius: 3px;
  text-decoration: none !important;
}
.display-os-mac .toggler .button-mac,
.display-os-linux .toggler .button-linux,
.display-os-windows .toggler .button-windows,
.display-platform-ios .toggler .button-ios,
.display-platform-android .toggler .button-android {
  background-color: #05A5D1;
  color: white;
}
block { display: none; }
.display-platform-ios.display-os-mac .ios.mac,
.display-platform-ios.display-os-linux .ios.linux,
.display-platform-ios.display-os-windows .ios.windows,
.display-platform-android.display-os-mac .android.mac,
.display-platform-android.display-os-linux .android.linux,
.display-platform-android.display-os-windows .android.windows {
  display: block;
}</style>
<span>Мобильная ОС:</span>
<a href="javascript:void(0);" class="button-ios" onclick="display('platform', 'ios')">iOS</a>
<a href="javascript:void(0);" class="button-android" onclick="display('platform', 'android')">Android</a>
<span>ОС разработки:</span>
<a href="javascript:void(0);" class="button-mac" onclick="display('os', 'mac')">Mac</a>
<a href="javascript:void(0);" class="button-linux" onclick="display('os', 'linux')">Linux</a>
<a href="javascript:void(0);" class="button-windows" onclick="display('os', 'windows')">Windows</a>
</div>

<!-- ######### LINUX AND WINDOWS for iOS ##################### -->

<block class="linux windows ios" />

## Не поддерживается

<div>К сожалению Apple позволяет производить разработку для iOS только на системах Mac. Если вы хотите разрабатывать мобильные приложения для iOS, но все еще не приобрели Mac, вы можете попробовать начать с инструкций для <a href="" onclick="display('platform', 'android')">Android</a>.</div>

<center><img src="img/react-native-sorry-not-supported.png" width="150"></img></center>

<!-- ######### MAC for iOS ##################### -->

<block class="mac ios android" />

## Установка зависимостей

<block class="mac ios" />

Вам понадобятся Node.js, Watchman, инструменты командной строки React Native и Xcode.

<block class="mac android" />

Вам понадобятся Node.js, Watchman, инструменты командной строки React Native и Android Studio.

<block class="mac ios android" />

### Node, Watchman

Мы рекомендуем устанавливать Node и Watchman используя [Homebrew](http://brew.sh/). После установки Homebrew выполните следующие команды в терминале:

```
brew install node
brew install watchman
```

> [Watchman](https://facebook.github.io/watchman) это инструмент Facebook для наблюдения за изменениями в файловой системе.
Рекомендуется установить его для лучшей производительности.

### Интерфейс командной строки React Native

Node.js поставляется с npm, который позволяет вам установить интерфейс командной строки React Native. Выполните следующие команды в терминале:

```
npm install -g react-native-cli
```

> Если вы видите ошибку *отказано в доступе*, попробуйте использовать sudo: `sudo npm install -g react-native-cli`.

> Если вы видите ошибку `Cannot find module 'npmlog'`, попробуйте установить npm следующим образом: `curl -0 -L http://npmjs.org/install.sh | sudo sh`.

<block class="mac ios" />

### Xcode

Проще всего установить Xcode из [Mac App Store](https://itunes.apple.com/us/app/xcode/id497799835?mt=12). Вместе с Xcode будет установлен симулятор iOS а также все необходимые иснтрументы для сборки вашего приложения iOS.

<block class="mac android" />

### Среда разработки Android

Настройка среды разработки может оказаться непростым делом если вы новичок в разработке для Android. Если вы уже знакомы с разработкой для Android, есть некоторые вещи, которые вам потребуется настроить. В любом случае внимательно выполните следующие шаги.

#### 1. Установите Android Studio

Скачайте и установите [Android Studio](https://developer.android.com/studio/install.html).

#### 2. Убедитесь что Android SDK установлен

По умолчанию Android Studio устанавливает версию `Android 7.0 (Nougat)`. Вы сможете убедиться что SDK установлен, выбрав "Configure" на последнем шаге процесса установки Android Studio или открыв "Preferences" из меню Android Studio, а затем выбрав `Appearance and Behavior` → `System Settings` → `Android SDK`.

![Менеджер Android Studio SDK](img/react-native-android-studio-configure-sdk.png)

Выберите "SDK Platforms" в менеджере SDK и вы должны уидеть галочку рядом с "Android 7.0 (Nougat)". Если это не так, поставьте галочку а затем нажмите "Apply".

![Менеджер Android Studio SDK](img/react-native-sdk-platforms.png)

> Если вам требуется поддержка более ранних версий Android, то можете установить дополнительные Android SDK на этом же экране.

#### 3. Настройка путей

Интерфейсу командной строки React Native необходима переменная среды `ANDROID_HOME`. Вы можете установить ее в терминале с помощью следующей команды:

```
export ANDROID_HOME=~/Library/Android/sdk
```

Чтобы не делать это вручную каждый раз, откройте терминал и создайте (или отредактируйте) файл `~/.bashrc` в вашем текстовом редакторе и добавьте следующие строки:

```
export ANDROID_HOME=~/Library/Android/sdk
export PATH=${PATH}:${ANDROID_HOME}/tools
```

Вторая строка добавит инструмент `android` в переменную пути, который пригодится на следующем шаге.

> Если вы не станавливали Android SDK с помощью Android Studio, убедитесь что вы экспортируете правильный путь для `ANDROID_HOME`. Если вы устанавливали Android SDK с помощью Homebrew, он будет расположен по пути `/usr/local/opt/android-sdk`.

#### 4. Установите виртуальное устройство Android

Android Studio должна была настроить виртуальное устройство Android в процессе установки, но часто случается так что Android Studio не устанавливает AVD (Android Virtual Device).

![Менеджер виртуального устройства Android Studio](img/react-native-tools-avd.png)

Чтобы увидеть список доступных AVD, запустите "AVD Manager" из Android Studio или выполниет в терминале следующую команду:

```
android avd
```
Если вам нужно новое виртуальное устройство, воспользуйтесь [Инструкцией Android Studio](https://developer.android.com/studio/run/managing-avds.html) для его создания.

> Если вы видите ошибку CPU/ABI "No system images installed for this target.", вернитесь в "SDK Manager" и выберите "Show Package Details" из "SDK Platforms". Вы сможете установить любой из недостающих образов, например "Google APIs Intel Atom (x86)".

<!-- ######### LINUX and WINDOWS for ANDROID ##################### -->

<block class="windows linux android" />

## Установка зависимостей

<block class="linux android" />

Вам потребуются Node.js, инструменты командной строки React Native и Android Studio.

### Node

Чтобы уствновить Node.js 4 или более новую версию, следуйте [инструкциям по установке для вашего дистрибутива Linux](https://nodejs.org/en/download/package-manager/)

<block class='windows android' />

Вам потребуются Node.js, инструменты командной строки React Native и Android Studio.

### Node

Рекомендуется устанавливать Node.js и Python2 с помощью [Chocolatey](https://chocolatey.org), популярного менеджера пакетов для Windows. Откройте командную строку с правами  Администратора и выполните следующую команду:

```
choco install nodejs.install
choco install python2
```

> Вы можете найти дополнительные варианты установки на [странице загрузки Node.js](https://nodejs.org/en/download/).

<block class="windows linux android" />

### Интерфейс командной строки React Native

Node поставляется с npm, который позволяет установить интерфейс командной строки React Native.

```
npm install -g react-native-cli
```

### Среда разработки Android

Настройка среды разработки может оказаться непростым делом если вы новичок в разработке для Android. Если вы уже знакомы с разработкой для Android, есть некоторые вещи, которые вам потребуется настроить. В любом случае внимательно выполните следующие шаги.

#### 1. Установка Android Studio

Загрузите и установите [Android Studio](https://developer.android.com/studio/install.html).

#### 2. Убедитесь что Android SDK установлен

По умолчанию Android Studio устанавливает версию `Android 7.0 (Nougat)`. Вы сможете убедиться что SDK установлен, выбрав "Configure" на последнем шаге процесса установки Android Studio или открыв "Preferences" из меню Android Studio, а затем выбрав `Appearance and Behavior` → `System Settings` → `Android SDK`.

![Менеджер Android Studio SDK](img/react-native-android-studio-configure-sdk-windows.png)

Выбрав "SDK Platforms" в Менеджере SDK вы должны увидеть синюю галочку рядом с "Android 7.0 (Nougat)". Если ее нет, выберите галочку и нажмите "Apply".

![Менеджер Android Studio SDK](img/react-native-sdk-platforms.png)

> Если вам требуется поддержка более ранних версий Android, то можете установить дополнительные Android SDK на этом же экране.

#### 3. Настройте пути

Интерфейсу командной строки React Native необходима переменная среды `ANDROID_HOME`.

<block class="linux android" />

Создайте или измените файл `~/.bashrc`, добавив в него следующие пару строк:

```
export ANDROID_HOME=~/Android/Sdk
export PATH=${PATH}:${ANDROID_HOME}/tools
```

Вторая строка добавит инструмент `android` в переменную пути, который пригодится на следующем шаге.

> Если вы не станавливали Android SDK с помощью Android Studio, убедитесь что вы экспортируете правильный путь для `ANDROID_HOME`.

<block class="windows android" />

Выберите `Control Panel` → `System and Security` → `System` → `Change settings` →
`Advanced System Settings` → `Environment variables` → `New` и укажите путь к вашему Android SDK.

![переменная среды](img/react-native-android-sdk-environment-variable-windows.png)

> Если вы не станавливали Android SDK с помощью Android Studio, убедитесь что вы экспортируете правильный путь для `ANDROID_HOME`.

Перезапустите командную строку чтобы применить новую переменную среды.

<block class="linux windows android" />

#### 4. Настройка виртуального устройства Android

Android Studio должна была настроить виртуальное устройство Android в процессе установки, но часто случается так что Android Studio не устанавливает AVD (Android Virtual Device).

![Менеджер виртуального устройства Android Studio](img/react-native-tools-avd.png)

Чтобы увидеть список доступных AVD, запустите "AVD Manager" из Android Studio или выполниет в терминале следующую команду:

```
android avd
```

Если вам нужно новое виртуальное устройство, воспользуйтесь [Инструкцией Android Studio](https://developer.android.com/studio/run/managing-avds.html) для его создания.

> Если вы видите ошибку CPU/ABI "No system images installed for this target.", вернитесь в "SDK Manager" и выберите "Show Package Details" из "SDK Platforms". Вы сможете установить любой из недостающих образов, например "Google APIs Intel Atom (x86)".

<block class="linux android" />

### Watchman (необязательно)

Следуйте [инструкции по установке Watchman](https://facebook.github.io/watchman/docs/install.html#build-install) чтобы скомпилировать и установить Watchman из исходного кода.

> [Watchman](https://facebook.github.io/watchman/docs/install.html) это инструмент Facebook для наблюдения за изменениями в файловой системе. Рекомендуется установить его для максимальной производительности, но этот шаг можно пропустить если у вас возникнут серьезные сложности при установке.

<block class="mac ios android" />

## Проверка установки React Native

<block class="mac ios" />

С помощью интерфейса командной строки React Native создайте новый проект React Native под названием "AwesomeProject", а затем выполните `react-native run-ios` в созданной папке.

```
react-native init AwesomeProject
cd AwesomeProject
react-native run-ios
```

Вскоре вы должны увидеть свое приложение в симуляторе iOS.

`react-native run-ios` это только один из способов запустить ваше мобильное приложение. Вы также можете запустить его непосредственно из Xcode или Nuclide.

<block class="mac android" />

С помощью интерфейса командной строки React Native создайте новый проект React Native под названием "AwesomeProject", а затем выполните `react-native run-android` в созданной папке.

```
react-native init AwesomeProject
cd AwesomeProject
react-native run-android
```

Вскоре вы увидите приложение, запущенное в эмуляторе Android. `react-native run-android`  это только один из нескольких способой запустить ваше мобильное приложение. Вы также можете запустить его непосредственно из Android Studio или Nuclide.

<block class="mac ios android" />

### Внесение изменений в код вашего мобильного приложения

После того как вы смогли запустить мобильное приложение, можно попробовать внести изменения в его код.

<block class="mac ios" />

- Откройте `index.ios.js` в текстовом редакторе и измените какие-то строки кода.
- Чтобы изменения отобразились в симуляторе iOS, нажмите `Command⌘ + R` и мобильное приложение обновится!

<block class="mac android" />

- Откройте `index.android.js` в текстовом редакторе и измените какие-то строки кода.
- Дважды нажмите клавишу `R` или выберите `Reload` из Меню Разработчика (Developer Menu) для того чтобы внесенные изменения отобразились в эмуляторе Android!

<block class="mac ios android" />

### Готово!

Поздравляем! Вы успешно запустили и изменили мобильное приложение React Native.

<center><img src="img/react-native-congratulations.png" width="150"></img></center>

<block class="windows linux android" />

## Проверка установки React Native

Для создания проекта "AwesomeProject" используйте командную строку React Native, затем выполните `react-native run-android` в созданной папке.

```
react-native init AwesomeProject
cd AwesomeProject
react-native run-android
```

Если все было сделано верно, вы должны в скором времени увидеть ваше приложение в эмуляторе Android.

> Иногда случается так что упаковщик не запускается автоматически при выполнении
`react-native run-android`. В этом случае вы можете запустить его вручную: `react-native start`.

<block class="windows android" />

> Если, работая в ОС Windows, вы видите ошибку `ERROR  Watcher took too long to load` попробуйте увеличить значение timeout в [этом файле](https://github.com/facebook/react-native/blob/5fa33f3d07f8595a188f6fe04d6168a6ede1e721/packager/react-packager/src/DependencyResolver/FileWatcher/index.js#L16) (он находится в папке `node_modules/react-native/` вашего проекта).

<block class="windows linux android" />

### Внесение изменений в код вашего мобильного приложения

После того как вы смогли запустить мобильное приложение, можно попробовать внести изменения в его код.

- Откройте файл `index.android.js` в текстовом редакторе и измените что-нибудь в нем.
- Дважды нажмите клавишу `R` или выберите `Reload` в Меню Разработчика (Developer Menu) чтобы увидеть изменения на экране эмулятора!

### Готово!

Поздравляем! Вы успешно запустили и изменили мобильное приложение React Native.

<center><img src="img/react-native-congratulations.png" width="150"></img></center>

<block class="mac windows linux ios android" />

## Что дальше?

- Если вы хотите добавить код React Native к существующему приложению, изучите [руководство по интеграции](docs/integration-with-existing-apps.html).

- Если у вас возникли сложности, вы можете найти ответ в разделе [решения проблем](docs/troubleshooting.html#content).

- Если вы хотите узнать больше про React Native, переходите к [уроку](docs/tutorial.html).

<script>
// Convert <div>...<span><block /></span>...</div>
// Into <div>...<block />...</div>
var blocks = document.getElementsByTagName('block');
for (var i = 0; i < blocks.length; ++i) {
  var block = blocks[i];
  var span = blocks[i].parentNode;
  var container = span.parentNode;
  container.insertBefore(block, span);
  container.removeChild(span);
}
// Convert <div>...<block />content<block />...</div>
// Into <div>...<block>content</block><block />...</div>
blocks = document.getElementsByTagName('block');
for (var i = 0; i < blocks.length; ++i) {
  var block = blocks[i];
  while (block.nextSibling && block.nextSibling.tagName !== 'BLOCK') {
    block.appendChild(block.nextSibling);
  }
}
function display(type, value) {
  var container = document.getElementsByTagName('block')[0].parentNode;
  container.className = 'display-' + type + '-' + value + ' ' +
    container.className.replace(RegExp('display-' + type + '-[a-z]+ ?'), '');
}

// If we are coming to the page with a hash in it (i.e. from a search, for example), try to get
// us as close as possible to the correct platform and dev os using the hashtag and block walk up.
var foundHash = false;
if (window.location.hash !== '' && window.location.hash !== 'content') { // content is default
  var hashLinks = document.querySelectorAll('a.hash-link');
  for (var i = 0; i < hashLinks.length && !foundHash; ++i) {
    if (hashLinks[i].hash === window.location.hash) {
      var parent = hashLinks[i].parentElement;
      while (parent) {
        if (parent.tagName === 'BLOCK') {
          var devOS = null;
          var targetPlatform = null;
          // Could be more than one target os and dev platform, but just choose some sort of order
          // of priority here.

          // Dev OS
          if (parent.className.indexOf('mac') > -1) {
            devOS = 'mac';
          } else if (parent.className.indexOf('linux') > -1) {
            devOS = 'linux';
          } else if (parent.className.indexOf('windows') > -1) {
            devOS = 'windows';
          } else {
            break; // assume we don't have anything.
          }

          // Target Platform
          if (parent.className.indexOf('ios') > -1) {
            targetPlatform = 'ios';
          } else if (parent.className.indexOf('android') > -1) {
            targetPlatform = 'android';
          } else {
            break; // assume we don't have anything.
          }
          // We would have broken out if both targetPlatform and devOS hadn't been filled.
          display('os', devOS);
          display('platform', targetPlatform);      
          foundHash = true;
          break;
        }
        parent = parent.parentElement;
      }
    }
  }
}
// Do the default if there is no matching hash
if (!foundHash) {
  var isMac = navigator.platform === 'MacIntel';
  var isWindows = navigator.platform === 'Win32';
  display('os', isMac ? 'mac' : (isWindows ? 'windows' : 'linux'));
  display('platform', isMac ? 'ios' : 'android');
}
</script>
