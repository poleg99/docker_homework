FROM python:3.9
LABEL maintainer="Oleg Pavlov p_oleg@mail.ru" version="1.0.0"

ENV NODE_ENV production
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN mkdir /app
ADD . /app
WORKDIR /app
RUN apt-get update  && apt-get -y install curl
RUN /usr/local/bin/pip install --upgrade pip setuptools wheel
RUN pip install -r requirements.txt
RUN chmod +x /app/docker-entrypoint.sh

RUN useradd -m app
USER app

EXPOSE 8000
HEALTHCHECK CMD curl -f http://localhost:8000/admin || exit 1
ENTRYPOINT ["/bin/sh", "/app/docker-entrypoint.sh"]
