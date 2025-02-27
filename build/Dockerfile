FROM python:3.9-alpine

LABEL Name="Python Flask Demo App" Version="1.4.2"
LABEL org.opencontainers.image.source="https://github.com/benc-uk/python-demoapp"

ARG srcDir=src
WORKDIR /app

COPY $srcDir/requirements.txt .

# Fix: Install `ncurses` instead of `ncurses-base`
RUN apk update && apk add --no-cache ncurses util-linux

RUN pip install --no-cache-dir -r requirements.txt

COPY $srcDir/run.py .
COPY $srcDir/app ./app

EXPOSE 80

CMD ["gunicorn", "-b", "0.0.0.0:80", "run:app"]
