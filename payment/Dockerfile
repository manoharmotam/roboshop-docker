FROM  python:3.9.25-alpine3.22 AS builder
WORKDIR /app
COPY requirements.txt .
RUN apk add --no-cache --virtual .build-deps gcc musl-dev linux-headers python3-dev \
    && pip3 install --prefix=/install -r requirements.txt \
    && apk del .build-deps


FROM  python:3.9.25-alpine3.22
WORKDIR /app
EXPOSE 8080
RUN addgroup -S roboshop && adduser -S -G roboshop roboshop && \
    chown -R roboshop:roboshop /app
COPY --from=builder /install /usr/local/
COPY *.py payment.ini requirements.txt .
USER roboshop
CMD [ "/usr/local/bin/uwsgi", "--ini", "payment.ini"]