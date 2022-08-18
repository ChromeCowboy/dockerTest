FROM node:latest AS builder

RUN mkdir -p /app

WORKDIR /app

COPY . .

RUN npm install
RUN npm run build

FROM nginx:alpine

COPY src/nginx/etc/conf.d/default.conf /etc/nginx/conf/default.conf
COPY --from=builder /dist/angular_converter /usr/share/nginx/html/
