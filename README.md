# yamdb_final

## Описание проекта
Проект yamdb_final служит для отработки навыков работы с workflow, а 
конкретно - github actions.
Основной файл конфигурации github actions находится в /.github/workflows/ и 
называется yamdb_workflow.yml.

## Автоматизация всего и вся
За основу взят репозиторий https://github.com/dvkonstantinov/api_yamdb
К нему прикручена автоматизация:
- Тестирования pytest. Тесты находятся в каталоге /tests/
- Создание docker-образа и пуш этого образа на https://hub.docker.com/
- Разворачивание проекта на сервере (деплой) в случае успешного прохождения 
  тестов и пуш проекта в master-ветку.
  
## Разворачивание образа локально
Предполагается наличие docker на локальной машине.
1. Перейти в каталог infra
```sh
cd infra
```
2. Запустить установку из файла docker-compose. Ключ -d для того чтобы 
   работать в фоне.
```sh
sudo docker-compose up -d
```
3. В случае успешной установки в браузере открыть адрес http://127.0.0.1/

## Разворачивание проекта на сервере.
1. Нажать кнопку fork, тем самым продублировать себе этот репозиторий.
2. Сделать git clone <ваш_репозиторий> к себе на компьютер
3. В файле /api_yamdb/api_yamdb/settings.py добавить в ALLOWED_HOSTS ip 
   адрес или домен вашего сервера
4. В файле /infra/nginx/default.conf в server_name добавить ip 
   адрес или домен вашего сервера
5. Скопировать файлы docker-compose.yaml в 
   home/<ваш_username>/docker-compose.yaml, а файл default.conf - в home/<ваш_username>/nginx/default.conf
6. Прописать в настройках репозитория гитхаба secrets - их можно посмотреть 
   в /.github/workflows/yamdb_workflow.yml
7. Сделать телеграм бота, ваш ID и TOKEN телеграм тоже добавить в secrets
8. Закоммитить и запушить на гитбах измененный код
9. Перейти во вкладку actions вашего репозитория и посмотреть правильность 
   workflow
10. Увидеть у себя в телеграме сообщение что все прошло успешно. Заходить 
    на сайт по адресу ваш_домен/admin
    
Главная страница сайта недоступна, поскольку проект нацелен исключительно 
на взаимодейтсвие по API

##Пример работающего сайта:
Главная страница - http://test3.dvkonstantinov.ru/
Страница админки - http://test3.dvkonstantinov.ru/admin/

Конец.

![example workflow](https://github.
com/dvkonstantinov/yamdb_final/actions/workflows/yamdb_workflow/badge.svg)