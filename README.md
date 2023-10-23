# playwright_project
В переводе с английского - драматург
Playwright — это библиотека для автоматизации Chromium, Firefox и WebKit с помощью одного API.

## Генератор тестов
### Создавайте тесты с помощью Playwright
Playwright имеет возможность создавать тесты для вас, когда вы выполняете действия в браузере,
и это отличный способ быстро приступить к тестированию.
Драматург посмотрит на вашу страницу и определит лучший локатор, расставив приоритеты по ролям,
тексту и локаторам тестовых идентификаторов.
Если генератор найдет несколько элементов, соответствующих локатору, он улучшит локатор,
чтобы сделать его устойчивым и однозначно идентифицировать целевой элемент.
Ввести в терминал:
`
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="codegen demo.playwright.dev/todomvc"
`
### Эмуляция
Playwright открывает окно браузера с заданной шириной и высотой области просмотра и не отвечает, поскольку тесты необходимо запускать в тех же условиях. Используйте --viewportопцию для создания тестов с другим размером области просмотра.
Ввести в терминал:

```
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="codegen --viewport-size=800,600 playwright.dev"
```

Эмулировать
Записывайте скрипты и тесты во время эмуляции мобильного устройства, используя --deviceопцию,
которая среди прочего устанавливает размер окна просмотра и пользовательский агент.
Ввести в терминал:
`
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args='codegen --device="iPhone 13" playwright.dev'
`

### Эмулировать цветовую схему
Записывайте сценарии и тесты, эмулируя цветовую схему с опцией --color-scheme.
Ввести в терминал:
`
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="codegen --color-scheme=dark playwright.dev"
`
### Эмуляция геолокации, языка и часового пояса
Записывайте сценарии и тесты, эмулируя часовой пояс, язык и местоположение, используя --timezoneпараметры --geolocationи --lang. Как только страница откроется:

1. Принять файлы cookie
2. В правом верхнем углу нажмите кнопку «Найти меня», чтобы увидеть геолокацию в действии.
   Ввести в терминал:
`
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args='codegen --timezone="Europe/Rome" --geolocation="41.890221,12.492348" --lang="it-IT" bing.com/maps'
`

### Сохранить аутентифицированное состояние
Запустите codegenс --save-storage, чтобы сохранить файлы cookie и localStorage в конце сеанса.
Это полезно для отдельной записи шага аутентификации и последующего повторного использования при записи дополнительных тестов.
Ввести в терминал:
`
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="codegen github.com/microsoft/playwright  --save-storage=auth.json"
`
После выполнения аутентификации и закрытия браузера auth.json будет содержаться состояние хранилища,
которое вы сможете повторно использовать в своих тестах.

### Загрузить аутентифицированное состояние
Запустите с помощью --load-storage, чтобы использовать ранее загруженное хранилище из файла auth.json.
Таким образом, все файлы cookie и localStorage будут восстановлены,
что приведет большинство веб-приложений в состояние аутентификации без необходимости повторного входа в систему.
Это означает, что вы можете продолжать генерировать тесты из состояния входа в систему.
`
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="codegen --load-storage=auth.json github.com/microsoft/playwright"
`



