FROM python:3.10.20-alpine AS builder
WORKDIR /app
COPY *.py .
COPY payment.ini .
COPY requirements.txt .
RUN pip3 install -r requirements.txt

FROM python:3.10.20-alpine
WORKDIR /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
COPY --from=builder /app /app/
USER roboshop
CMD [ "/usr/local/bin/uwsgi", "--ini", "payment.ini"]