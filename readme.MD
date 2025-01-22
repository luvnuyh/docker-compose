# 구조

```
L backend
    L  소스 코드 (제공)
    L Dockerfile 구성
L frontend     
    L  소스 코드 (제공)
    L Dockerfile 구성
L nginx
    L default.conf (제공): 프록시 관련 내용

```

# docker-compose 구조

```
L database - mysql 이미지 사용 (ㅇㄷ ㄹㄴㅅ ㄱㅂ)

L server - java 빌드 -> jdk 기반 구동(리눅스 기반) -> 백엔드 담당, 디비랑 통신, 비즈니스 로직 처리

L frontend - nginx 기반(얘도 리눅스 기반) react 빌드 결과 세팅 -> html/css/js 실제 처리 담당

L nginx - nginx기반(ㅇㄷ ㄹㄴㅅ ㄱㅂ) 단독 구성, 프록시 담당, 모든 요청 담당. 맨 앞단에서. -> web이다!

```

# 도커 컴포즈 구성

```
# 기존 자원 삭제
docker compose down

# 컴포즈 기반 구성  -> docker-compose.yml 읽어서 구성
docker compose up -d

```
