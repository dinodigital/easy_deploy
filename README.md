Bash скрипт для быстрого деплоя Python-приложения на сервер. Работает только с pipenv! 

###Как работает:
1. Скрипт устанавляет соединение с сервером
2. Клонирует репозиторий в заданную папку
3. Синхронизирует pipenv
4. Создает конфиг для supervisor
5. Переходит в папку с проектом
6. Приложение нужно запускать отдельно через супервизор (supervisorctl start folder_name)

###Настройка скрипта:
1. В файле deploy заполнить ip сервера и username (имя пользователя на сервере). Опционально можно настроить название скрипта на сервере, если сохраняете его под другим именем.
2. Скопировать (или создать новый) файл deploy_on_server в /usr/bin на сервере
3. Скопировать (или создать новый) файл deploy в /usr/bin на локальной машине

###Запуск скрипта:
```
deploy <server_username> <git_repository_link> <folder_and_process_name> <run_file_name>
```
Команда deploy принимает на вход 4 переменные:
1. Имя пользователя на сервере
2. Ссылка на репозиторий (если репозиторий приватный — настройте ssh ключи)
3. Название папки, куда будет склонирован репозиторий. Она же название процесса в supervisorctl
4. Имя запускаемого файла вашего приложения (например, run.py)

###Пример:
```
deploy root git@github.com:me/my_repo.git open_business run.py
```
