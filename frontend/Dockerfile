FROM node:alpine as builder
WORKDIR /tmp
COPY package.json .
RUN npm install
COPY . .

RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /tmp/build /usr/share/nginx/html