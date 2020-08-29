# SQLiCrawler

**sqlicrawler** - это утилита, созданная для автоматизации поиска sql-инъекций. Она запускает экземпляр браузера Chromium Headless и посещает ссылки на сайте, выполняя скрипты на JavaScript и отправляя формы. Это моя 100500 реализация сканнера уязвимостей.

С целью ускорения загрузки страниц загрузка стилей и изображений блокируется.

![image](https://user-images.githubusercontent.com/12753171/91443290-cd3a6880-e87b-11ea-8ac1-703880a5ebee.png)

Такой паук "видит" страницу выше:

![image](https://user-images.githubusercontent.com/12753171/91443491-168ab800-e87c-11ea-8faf-1f0da95eb987.png)

## Usage

```zsh
# install the package into a virtual environment and create an executable in the ~/.local/bin directory
$ pipx install sqlicrawler
$ sqlicrawler --help
```

В качестве значения флага `-i` используется путь до файла, в котором содержится список ссылок (каждая с новой строки) на сайты для сканирования. С помощью флага `-o` задается имя файла в котором будут храниться результаты сканирования. этот файл имеет формат JSONL. Каждая его строка представляет собой сериализованный в JSON объект. Для парсинга файлов такого типа рекомендуется использовать утилиту **jq**.

Если Вы хотите заблокировать нежелательные запросы к определенным сайтам, например, к скриптам, собирающим статистику поситетилей сайта, то нужно создать файл `~/.config/sqlicrawler/blacklist.txt`, содержащий шаблоны запрещенных ссылок. Часть имени, содержащую произвольное количество символов можно заменить на `*`.

## Development

```zsh
$ poetry run pytest -s tests
```
