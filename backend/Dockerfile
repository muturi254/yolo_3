FROM node:14-alpine

LABEL maintainer="muturi254"
WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 5001

ENTRYPOINT [ "npm", "start" ]