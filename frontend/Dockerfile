FROM node:14.15.0-alpine

RUN apk update && \
    npm install && \
    npm install -g npm && \
    npm install -g vue-cli

WORKDIR /app

ADD ./src/package.json /app
ADD ./src/package-lock.json /app
RUN npm update

ADD ./src /app

EXPOSE 80

CMD ["npm", "run", "dev"]
