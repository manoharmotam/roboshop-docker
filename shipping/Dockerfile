FROM maven:3.9.16-eclipse-temurin-21-alpine AS builder
WORKDIR /app
COPY ./src /app/src/
COPY pom.xml /app/
RUN mvn clean package
RUN mv target/shipping-1.0.jar shipping.jar 

FROM maven:3.9.16-eclipse-temurin-21-alpine
WORKDIR /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
COPY --from=builder /app /app/
USER roboshop
CMD [ "java", "-jar", "shipping.jar" ]