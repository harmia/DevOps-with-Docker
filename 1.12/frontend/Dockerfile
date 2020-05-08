FROM node:alpine

WORKDIR /usr/app

COPY ./package*.json ./

RUN npm install

COPY ./src ./src
COPY ./util ./util
COPY ./config.js ./config.js
COPY ./webpack.config.js ./webpack.config.js

ENV API_URL=http://localhost:8000

RUN npm run build

RUN npm install -g serve

CMD serve -s -l 5000 dist

EXPOSE 5000
