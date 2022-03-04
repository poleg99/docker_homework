FROM node:14 as build
USER node
WORKDIR /app
COPY --chown=node:node package*.json ./

RUN npm install

COPY --chown=node:node . .
RUN npm run build

FROM nginx:1.17
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
HEALTHCHECK CMD curl --fail http://localhost:80 || exit 1
EXPOSE 80
