# 1단계: 빌드
FROM openjdk:17-alpine AS build

WORKDIR /app
COPY . .

RUN chmod +x ./gradlew
RUN ./gradlew clean build -x test

# 2단계: 실행 - JRE만 남기기
FROM openjdk:17-alpine

WORKDIR /app
COPY --from=build /app/build/libs/*.jar app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]
