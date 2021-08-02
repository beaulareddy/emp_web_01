FROM node:12-alpine as builder
RUN mkdir -p /app
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build --prod

FROM nginx:1.17.1-alpine
COPY --from=builder /app/dist/app /usr/share/nginx/html
RUN rm -rf /etc/nginx/conf.d/default.conf
COPY default.conf /etc/nginx/conf.d

