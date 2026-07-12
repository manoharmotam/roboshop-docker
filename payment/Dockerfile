FROM python:3.12
WORKDIR /app
COPY *.py .
COPY payment.ini .
COPY requirements.txt .
RUN pip3 install -r requirements.txt
EXPOSE 8080
CMD [ "/usr/local/bin/uwsgi", "--ini", "payment.ini"]