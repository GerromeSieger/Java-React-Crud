FROM node:13.12.0-alpine as build

WORKDIR /app

COPY package.json ./

COPY package-lock.json ./

RUN npm install

COPY . /app

RUN npm run build 

FROM ubuntu/apache2:2.4-20.04_beta

COPY --from=build /app/build /var/www/html:rx

RUN rm /etc/apache2/sites-available/000-default.conf

RUN rm /etc/apache2/apache2.conf

COPY 000-default.conf /etc/apache2/sites-available/

COPY apache2.conf /etc/apache2/

COPY .htaccess /var/www/html/build



