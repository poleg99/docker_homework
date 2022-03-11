FROM python:3.9

ENV NODE_ENV production
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN mkdir /app
ADD . /app
WORKDIR /app
RUN /usr/local/bin/pip install --upgrade pip setuptools wheel
RUN pip install -r requirements.txt

EXPOSE 8000
RUN chmod +x /app/docker-entrypoint.sh
ENTRYPOINT ["/bin/sh", "/app/docker-entrypoint.sh"]
