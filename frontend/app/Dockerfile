FROM node:alpine as builder
WORKDIR '/build'
COPY app ./app
COPY resources ./resources
COPY third_party ./third_party

WORKDIR '/build/app'

RUN npm config set registry https://registry.npm.taobao.org
RUN npm install --unsafe-perm node-sass
RUN npm rebuild node-sass
RUN npm run build

RUN ls /build/app/dist

FROM nginx
EXPOSE 80
COPY --from=builder /build/app/dist /usr/share/nginx/html


