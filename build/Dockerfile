FROM python:3.9-slim-buster

LABEL Name="Python Flask Demo App" Version=1.4.2
LABEL org.opencontainers.image.source = "https://github.com/benc-uk/python-demoapp"

ARG srcDir=src
WORKDIR /app
COPY $srcDir/requirements.txt .
RUN apt-get update && apt-get install -y ncurses-base=6.1+20181013-2+deb10u5 util-linux=2.33.1-0.1+deb10u1
RUN pip install --no-cache-dir -r requirements.txt

COPY $srcDir/run.py .
COPY $srcDir/app ./app

EXPOSE 80

CMD ["gunicorn", "-b", "0.0.0.0:80", "run:app"]
