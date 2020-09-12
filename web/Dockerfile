FROM nginx:1.18.0-alpine

RUN apk --update add openssl

RUN mkdir -p /var/www/html

# 自己証明書SSL
RUN openssl genrsa 2048 > server.key \
 && openssl req -new -key server.key -subj "/C=JP/ST=Chiba/L=Matsudo/O=Freelance/OU=web/CN=localhost" > server.csr \
 && openssl x509 -in server.csr -days 3650 -req -signkey server.key > server.crt \
 && cp server.crt /etc/nginx/server.crt \
 && cp server.key /etc/nginx/server.key \
 && chmod 755 -R /var/www/html \
 && chmod 400 /etc/nginx/server.key