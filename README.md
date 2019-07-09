# Краткая ремарка по размещению небольших [React](https://ru.reactjs.org/ "JavaScript-библиотека для создания пользовательских интерфейсов") демо-приложений на GitHub Pages, созданных с помощью утилиты [create-react-app](https://github.com/facebook/create-react-app)
---

Originals: 
[Deploying a React App to GitHub Pages](https://github.com/gitname/react-gh-pages/tree/master),

[So you want to host your Single Page React App on GitHub Pages?](https://itnext.io/so-you-want-to-host-your-single-age-react-app-on-github-pages-a826ab01e48)


# Действия:

**1**. Скачать и установить [Node.js](https://nodejs.org/) (в комплекте с ним установится менеджер пакетов `npm`). Инструкции: [раз](http://webupblog.ru/kak-ustanovit-node-js-na-windows/) и [два](https://medium.com/devschacht/node-hero-chapter-1-239f7afeb1d1);

**2**. Скачать и установить [Git](https://git-scm.com/);

**3**. Создать аккаунт на [GitHub](https://github.com/) (далее - название аккаунта `you-name`, которое, естественно, должно быть своё). Инструкции по Git/GitHub: [раз](https://habr.com/ru/post/125799/) и [два](https://github.com/andreiled/mipt-cs-4sem/wiki/%D0%9F%D0%BE%D1%88%D0%B0%D0%B3%D0%BE%D0%B2%D0%B0%D1%8F-%D0%B8%D0%BD%D1%81%D1%82%D1%80%D1%83%D0%BA%D1%86%D0%B8%D1%8F-%D0%BF%D0%BE-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D0%B5-%D1%81-git-%D0%B8-github-%D0%B4%D0%BB%D1%8F-%D1%81%D1%82%D1%83%D0%B4%D0%B5%D0%BD%D1%82%D0%BE%D0%B2);

**4**. Создать новый пустой репозиторий `my-awesome-app` (инициализировать его `README.md` и др. файлами не нужно!);

**5**. В файловой системе ОС перейти в то место, где предполагается расположение папки с проектом и посредством вызова контекстного меню, выбрать пункт `Git Bash Here`;

**6**. Выполнить команду установки утилиты `create-react-app`:

```Bash
$ npm install -g create-react-app
```

**7**. Далее, создать, собственно, само приложение (заготовку), выполнив команду:

```Bash
$ create-react-app my-awesome-app
```

  где `my-awesome-app` - название проекта. В результате будет создана директория `my-awesome-app` с проектом-заготовкой. Папку `.git` с первым атоматически созданным утилитой коммитом можно удалить;

**8**. Установить пакет `gh-pages` (именно он позволит деплоить скомпилированный проект на GitHub Pages):

```Bash
$ npm install gh-pages --save-dev
```

**9**. В корне папки с проектом найти и открыть на редактирование файл `package.json` и:
  - в самом верху где `name` и `version` вписать URL-адрес, по которому будет доступно готовое приложение
  ```
  {
    "homepage": "https://you-name.github.io/my-awesome-app",
    "name": "my-awesome-app",
    "version": "0.1.0",
    //...
  ```
  - в разделе `scripts` вписать
  ```
  "scripts": {
    //...
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"
  }
  ```

**10**. В папке с проектом (`my-awesome-app`) последовательно выполнить:

```bash
$ git init
$ git add .
$ git commit -m "First commit. My Awesome Application."
$ git remote add origin https://github.com/you-name/my-awesome-app.git
$ git push origin master
```

**11**. Далее, необходимо собрать продакшн билд и задеплоить, собственно, на сервер GitHub`а:

```bash
$ npm run deploy
```

Если все сделано правильно и не было никаких ошибок, то по окончанию этого процесса будет выведено `Published` и приложение станет доступно по ссылке `https://you-name.github.io/my-awesome-app`.

По сути, в репозитории создается новая ветка `gh-pages`, куда и деплоится собранное приложение, а исходники остаются в основной master-ветке.
