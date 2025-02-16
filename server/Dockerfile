FROM node:18-slim

WORKDIR /usr/src/app

COPY package.json yarn.lock ./

RUN yarn install --production

COPY . .

EXPOSE 5000

CMD [ "node", "index.js" ]
