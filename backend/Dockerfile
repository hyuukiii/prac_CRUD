# Build Stage
FROM gradle:8.5-jdk17-alpine AS builder
WORKDIR /app
COPY build.gradle settings.gradle ./
COPY src ./src
# Gradle 캐시 활용 및 빌드 (Test 제외하여 속도 향상)
RUN gradle build -x test --no-daemon

# Run Stage (실행 환경 최소화)
FROM eclipse-temurin:17-jre-alpine
WORKDIR /app
COPY --from=builder /app/build/libs/*.jar app.jar

# 컨테이너 실행 시 실행될 명령
ENTRYPOINT ["java", "-jar", "app.jar"]