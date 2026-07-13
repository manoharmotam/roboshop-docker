FROM node:20.20-alpine AS builder
WORKDIR /app
COPY package.json /app
COPY *.js /app
RUN npm install

FROM node:20.20-alpine
WORKDIR /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
COPY --from=builder /app /app/
USER roboshop
CMD ["node", "server.js"]
