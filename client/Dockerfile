FROM node:14.10 as builder

WORKDIR /var/www

COPY ./package.json ./

RUN npm install

COPY ./ ./

RUN npm run build

FROM nginx:latest

EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

COPY --from=builder /var/www/build /usr/share/nginx/html

# CMD