FROM eclipse-temurin:17.0.11_9-jdk-jammy AS builder
WORKDIR /workspace
COPY gradlew .
COPY gradlew.bat .
COPY gradle gradle
COPY build.gradle .
COPY settings.gradle .
COPY src src
RUN chmod +x gradlew
RUN ./gradlew bootJar

FROM eclipse-temurin:17.0.11_9-jre-jammy AS runner
WORKDIR /workspace
COPY --from=builder /workspace/build/libs/*.jar catalog-service.jar
CMD java -jar catalog-service.jar
EXPOSE 8080
