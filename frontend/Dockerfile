FROM node:14.2.0-slim as build
LABEL maintainer="Oleg Pavlov p_oleg@mail.ru" version="1.0.0"
ENV NODE_ENV production
USER node
WORKDIR /app
COPY --chown=node:node package*.json ./

RUN npm install

COPY --chown=node:node . .
RUN npm run build

FROM nginx:1.17
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
RUN apt-get update  && apt-get -y install curl
HEALTHCHECK CMD curl -f http://localhost:80/ || exit 1
EXPOSE 80
