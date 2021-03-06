# Event Sourcing + CQRS

평소에 관심을 가지고 있던 Event Sourcing + CQRS를 구현중(잠시 보류).

참고: https://cla9.tistory.com/2?category=814447

- Command 부분만 구현(snapshot은 구현하지 않음).
- Query는 추후에 구현 예정
- 기존에 데이터를 저장하던 방식과 많이 다르고 이벤트를 어떻게 가져가야 고민을 많이 해봐야 할듯.

### Axon server 실행 

원할한 테스트를 위해 dev mode 설정

```bash
docker run --rm \
    --name axonserver \
    -e AXONIQ_AXONSERVER_DEVMODE_ENABLED=true \
    -p 8024:8024 \
    -p 8124:8124 axoniq/axonserver
```

- Axon Dashboard

![axonserver-dashboard](./image/image1.png)

- Axon Dashboard overview

![axonserver-dashboard-overview](./image/image2.png)


### spring boot 실행

![spring-boot](./image/image3.png)

### api.http 실행

[api-http](src/main/kotlin/com/nnobs/api/api.http)

```http request
POST http://localhost:8080/users
Content-Type: application/json

{
  "email" : "logan@gmail.com"
}

# response
POST http://localhost:8080/users

HTTP/1.1 200 
Content-Type: text/plain;charset=UTF-8
Content-Length: 36
Date: Wed, 18 Nov 2020 03:46:08 GMT
Keep-Alive: timeout=60
Connection: keep-alive

31673fc3-0462-4596-bd45-bf5c8723109f

Response code: 200; Time: 450ms; Content length: 36 bytes
```

- Axon Dashboard search
![axonserver-dashboard-search](./image/image4.png)

