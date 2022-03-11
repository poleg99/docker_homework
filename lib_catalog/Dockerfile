FROM python:alpine3.15

ENV NODE_ENV production
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN mkdir /app
ADD . /app
WORKDIR /app
RUN apk add --update --no-cache curl g++ gcc libxslt-dev && pip install -r requirements.txt
EXPOSE 8000
RUN chmod +x /app/docker-entrypoint.sh
ENTRYPOINT ["/bin/sh", "/app/docker-entrypoint.sh"]
