# 멀티 스테이지 도커 파일 구성

# 소스코드 빌드
# 빌드의 결과물 jar -> 가동
# 실습, 위의 목적을 달성하는 도커 파일 생성

# 스테이지 1 -> jar를 생성(빌드)
# 그레이들 빌드 도구와 자바가 세팅된 이미지로부터 이미지 구성 
FROM gradle:7.6-jdk AS builder

# 워킹 디렉토리 지정
WORKDIR /app

# 호스트 os에서 백엔드 원소스 전체 카피
COPY . .

# 빌드
RUN chmod +x ./gradlew
RUN ./gradlew clean build --no-daemon

# 최종 산출물: /app/build/libs/*SNAPSHOT.jar

# 슽테이지 2 -> jar 가동 -> 경량 -> 배포속도 빨라짐
# jdk17이 설치된 경량 버전의 리눅스 준비
FROM openjdk:17-jdk-slim

# 컨테이너 내부에 작업 디렉토리 지정
WORKDIR /app

# jar 카피
# 스테이지 1으로부터 특정 위치에ㅔ 존재하는 산출물을 현재 컨테이너의 작업 디렉토리 루트에 복사
# /app/app.jar
COPY --from=builder /app/build/libs/*SNAPSHOT.jar ./app.jar

# 포트 지정
EXPOSE 8080

 # 서버 가동
CMD ["java","-jar","app.jar"]





