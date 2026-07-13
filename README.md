# Maticon Office DocSpace Plugins SDK

[RU](README.md) | [EN](README.en.md)

## Обзор

Maticon Office DocSpace Plugins SDK - это npm-пакет на базе TypeScript, который предоставляет интерфейсы для создания собственных плагинов, встраиваемых в портал DocSpace.

Чтобы глобально установить npm-пакет *@maticonoffice/docspace-plugin-sdk*, выполните в терминале следующую команду:

```bash
npm i -g @maticonoffice/docspace-plugin-sdk
```

## Возможности

- Создание базовых плагинов командой [npx](https://github.com/MaticonOffice/docspace-plugin-sdk/tree/master/npx).
- Встраивание плагинов в контекстное меню, информационную панель, меню профиля и главную кнопку через соответствующие [интерфейсы](https://github.com/MaticonOffice/docspace-plugin-sdk/tree/master/src/interfaces).
- Настройка интерфейса плагина с помощью [компонентов](https://github.com/MaticonOffice/docspace-plugin-sdk/tree/master/src/interfaces/components) плагинов DocSpace.

## npx

После установки npm-пакета становится доступна команда *npx create-docspace-plugin*. Она создаёт шаблон плагина с предварительно установленными типами плагинов и реализацией базовых методов.

Команда запускает диалог, в котором можно настроить параметры плагина и выбрать необходимые области действия.

Список всех вопросов диалога находится в файле [npx/dialog.js](https://github.com/MaticonOffice/docspace-plugin-sdk/blob/master/npx/dialog.js).

## Разработка плагина

* Напишите код для каждого [типа плагина](https://github.com/MaticonOffice/docspace-plugin-sdk/tree/master/src/interfaces/plugins), используя соответствующие переменные, методы и [элементы](https://github.com/MaticonOffice/docspace-plugin-sdk/tree/master/src/interfaces/items). Поместите скрипты в каталог *src*. Для каждого плагина, встраиваемого в портал, укажите требуемый интерфейс [Plugin](https://github.com/MaticonOffice/docspace-plugin-sdk/blob/master/src/interfaces/plugins/IPlugin.ts).
* Определите [сообщения плагина](https://github.com/MaticonOffice/docspace-plugin-sdk/blob/master/src/interfaces/utils/index.ts), которые будут возвращать элементы. Используйте подходящие события, обрабатываемые на стороне портала.
* Настройте пользовательский интерфейс плагина с помощью [компонентов плагина](https://github.com/MaticonOffice/docspace-plugin-sdk/tree/master/src/interfaces/components).

Примеры кода доступны в репозитории [MaticonOffice/docspace-plugins](https://github.com/MaticonOffice/docspace-plugins).

Для плагинов, созданных по старому шаблону SDK 1.1.1, замените скрипт сборки в *package.json* следующим:

```json
"build": "webpack && npx build-docspace-plugin"
```

> **Примечание.** Чтобы новая команда npx работала корректно, обновите глобально установленный пакет *@maticonoffice/docspace-plugin-sdk* до версии 2.0.0 или выше.

## Сборка плагина

Для сборки плагина требуется установленный пакетный менеджер *yarn*. После установки выполните следующие действия:

1. Откройте терминал и перейдите в корневой каталог плагина:

```bash
cd PDF-Converter
```

2. Установите все необходимые зависимости, если это не было сделано при создании шаблона:

```bash
yarn install
```

3. Соберите архив для загрузки на портал:

```bash
yarn build
```

Команда обфусцирует код проекта и с помощью npm-пакета *webpack* собирает его в файл *plugin.js*.

В корневом каталоге плагина будет создан каталог *dist*, в который помещается архив плагина. Этот готовый архив можно загрузить на портал DocSpace.

Старый скрипт *createZip* больше не требуется и может быть удалён.
