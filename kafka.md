1) Развернуть кластер Kafke из 3 брокеров и кластер ZooKeeper из 3 нод (docker/k8s/отдельные ВМ не важно)
2) Создать топик logs с 3 партициями и фактором репликации 2
3) Для Kafka создать пользователя devops-admin с правами на создание топиков
4) Запустить скрипт на python
```
from kafka import KafkaProducer
import json

producer = KafkaProducer(
    bootstrap_servers=['localhost:9092'],  # <-- ЗАМЕНИТЬ НА АДРЕС СВОЕГО КЛАСТЕРА
    value_serializer=lambda m: json.dumps(m).encode('ascii')
)

message = {"event": "log_entry", "level": "INFO", "message": "This is test message"}
future = producer.send('logs', value=message)

def on_send_success(record_metadata):
    print(f"Message send to topic {record_metadata.topic}, "
          f"partition {record_metadata.partition}, offset {record_metadata.offset}")

def on_send_error(excp):
    print(f"Error to send: {excp}")

future.add_callback(on_send_success)
future.add_errback(on_send_error)

producer.flush()
producer.close()
```
5) Запустить скрипт на python в docker-контейнере
```
from kafka import KafkaConsumer
import json

def main():
    consumer = KafkaConsumer(
        'logs',
        bootstrap_servers=['host.docker.internal:9092'], # <-- ЗАМЕНИТЬ НА АДРЕС СВОЕГО КЛАСТЕРА
        auto_offset_reset='earliest', 
        enable_auto_commit=True,
        group_id='log-consumer-group',
        value_deserializer=lambda m: json.loads(m.decode('utf-8'))
    )

    print("Start reading messages from the topic 'logs'...")

    for message in consumer:
        print(f"Message received: {message.value}")

if __name__ == '__main__':
    main()

```
6) Настроить сбор метрик Kafka через Prometheus и визуализацию в Grafana
7) Создать алерт на высокую задержку обработки сообщений (>500 мс)
8) Симулировать сбой одной ноды кластера Kafka и проверить сохранность данных после сбоя и после восстановления брокера
9) Настроить бэкапы в резервный кластер (резервный кластер поднять самостоятельно аналогично п1)
