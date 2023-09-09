FROM python:alpine

WORKDIR /app

COPY . /app/

RUN pip install --upgrade pip

RUN apk add --no-cache --virtual build-deps python3-dev mariadb-dev musl-dev gcc libc-dev make \
    && pip install --no-cache-dir -r requirements.txt

EXPOSE 8080

CMD python /app/app.py
