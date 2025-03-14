1) В репозитории node-app создать Dockerfile, с помощью которого будет собираться docker image этого приложения
2) В репозитории node-app создать docker-compose.yaml в котором будут описаны все сервисы (app и nginx)
3) В репозитории node-app создать папку nginx, в которой будут следующие файлы
- Dockerfile
- nginx.conf
в Dockerfile нужно
- копировать файл nginx.conf в /etc/nginx/conf.d/default.conf
- настроить правильную таймзону (в соответствии с Вашим местоположением)
