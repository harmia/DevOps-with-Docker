FROM node:alpine

WORKDIR /usr/app

COPY ./package*.json ./

RUN npm install

COPY ./server ./server
COPY ./config.js ./config.js
COPY ./index.js ./index.js
VOLUME ./logs.txt

ENV FRONT_URL=http://localhost:5000

CMD npm start

EXPOSE 8000
