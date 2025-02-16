FROM node:14-slim
WORKDIR /usr/src/app
COPY package.json yarn.lock ./
RUN yarn install
COPY . .
RUN yarn build
RUN yarn global add serve
CMD ["serve", "-s", "build", "-l", "3000"]
