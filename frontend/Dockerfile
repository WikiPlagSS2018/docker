FROM node:8.11.0

RUN apt-get update && \
  apt-get install -qq -y git ca-certificates


RUN git clone https://github.com/WikiPlagSS2018/webapp.git frontend

WORKDIR /frontend

RUN npm i -g yarn
RUN yarn

CMD ["yarn", "start"]