FROM node:14 as build
#USER node
WORKDIR /app
#COPY --chown=node:node package*.json ./
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:1.17
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
