## Задача №1
Дано элементарное приложение на nodejs: https://github.com/AnastasiyaGapochkina01/node-app

Необходимо
1) Запустить его в docker
- доступ к приложению должен осуществляться через nginx
2) С помощью terraform подготовить для него ВМ типа t3.small
3) С помощью ansible подготовить окружение на этой ВМ
- установить docker
- создать пользователя deployer с правами на запуск команд docker без sudo
- установить контейнер с node-exporter
- установить контейнер с cadvisor-exporter
- подключить экспортеры к prometheus
4) Создать дашборды для метрик ВМ (node-exporter) и контейнеров (cadvisor)
5) Написать Jenkinsfile для деплоя приложения на созданную ВМ
- сборка docker image и пуш его в docker hub или свой registry
- деплой нового image
- оповещение о результате сборки в telegram
6) Настроить сбор логов с контейнера приложения и nginx

## Задача №2
Дано элементарное приложение на python: https://github.com/AnastasiyaGapochkina01/flask-poetry

Необходимо
1) Запустить его в docker
- доступ к приложению должен осуществляться через nginx
2) С помощью terraform подготовить для него ВМ типа t3.small
3) С помощью ansible подготовить окружение на этой ВМ
- установить docker
- создать пользователя deployer с правами на запуск команд docker без sudo
- установить контейнер с node-exporter
- установить контейнер с cadvisor-exporter
- подключить экспортеры к prometheus
4) Создать дашборды для метрик ВМ (node-exporter) и контейнеров (cadvisor)
5) Написать Jenkinsfile для деплоя приложения на созданную ВМ
- сборка docker image и пуш его в docker hub или свой registry
- деплой нового image
- оповещение о результате сборки в telegram
6) Настроить сбор логов с контейнера приложения и nginx

## Задача №3
Дано приложение на python, реализующее простое API: https://github.com/AnastasiyaGapochkina01/bookshop

Необходимо
1) Запустить его в docker
- доступ к приложению должен осуществляться через nginx
- экземпляров api должно быть два
- приложению требуется postgres
2) С помощью terraform подготовить для него ВМ типа t3.small
3) С помощью ansible подготовить окружение на этой ВМ
- установить docker
- создать пользователя deployer с правами на запуск команд docker без sudo
- установить контейнер с node-exporter
- установить контейнер с cadvisor-exporter
- подключить экспортеры к prometheus
4) Создать дашборды для метрик ВМ (node-exporter) и контейнеров (cadvisor)
5) Написать Jenkinsfile для деплоя приложения на созданную ВМ
- сборка docker image и пуш его в docker hub или свой registry
- деплой нового image
- оповещение о результате сборки в telegram
6) Настроить сбор логов с контейнера приложения, postgres и nginx

## Задача №4
Дано приложение на golang: https://gist.github.com/AnastasiyaGapochkina01/472f54eddb8efc8a3397a9949d54c2bb

Необходимо
1) Запустить его в docker
- доступ к приложению должен осуществляться через nginx
- приложению требуется postgres
- использовать multistage build
2) С помощью terraform подготовить для него ВМ типа t3.small
3) С помощью ansible подготовить окружение на этой ВМ
- установить docker
- создать пользователя deployer с правами на запуск команд docker без sudo
- установить контейнер с node-exporter
- установить контейнер с cadvisor-exporter
- подключить экспортеры к prometheus
4) Создать дашборды для метрик ВМ (node-exporter) и контейнеров (cadvisor)
5) Написать Jenkinsfile для деплоя приложения на созданную ВМ
- сборка docker image и пуш его в docker hub или свой registry
- деплой нового image
- оповещение о результате сборки в telegram
6) Настроить сбор логов с контейнера приложения, postgres и nginx

### Задача 4.1
1) С помощью terraform подготовить ВМ для хранения бэкапов и 2 ВМ для кластера postgres
2) Для запущенного приложения https://gist.github.com/AnastasiyaGapochkina01/472f54eddb8efc8a3397a9949d54c2bb поднять отказоустойчивый кластер postgres (master-slave) НЕ в docker. 
3) Настроить резервное копирование по расписанию на удаленный сервер
4) Переключить приложение на кластер и проверить работоспособность

## Задача №5
Дано приложение на python: https://github.com/AnastasiyaGapochkina01/monitoring-app

Необходимо
1) Запустить его в docker
- доступ к приложению должен осуществляться через nginx
2) С помощью terraform подготовить для него ВМ типа t3.small
3) С помощью ansible подготовить окружение на этой ВМ
- установить docker
- создать пользователя deployer с правами на запуск команд docker без sudo
- установить контейнер с node-exporter
- установить контейнер с cadvisor-exporter
- подключить экспортеры к prometheus
4) Создать дашборды для метрик ВМ (node-exporter) и контейнеров (cadvisor)
5) Создать дашборды метрик приложения
6) Написать Jenkinsfile для деплоя приложения на созданную ВМ
- сборка docker image и пуш его в docker hub или свой registry
- деплой нового image
- оповещение о результате сборки в telegram
7) Настроить сбор логов с контейнера приложения и nginx
