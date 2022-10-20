# docker-compose로 kafka 설치하기
``` yml
version: '2'
services:
  zookeeper:
    container_name: my-zookeeper
    image: wurstmeister/zookeeper
    ports:
      - "2181:2181"
  kafka:
    container_name: my-kafka
    image: wurstmeister/kafka
    ports:
      - "9092:9092"
    environment:
      KAFKA_ADVERTISED_HOST_NAME: 127.0.0.1
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
```

# 실행
``` bash
docker-compose up -d
```

## bin 디렉토리 copy
``` bash
docker cp my-kafka:opt/kafka/bin bin
```
