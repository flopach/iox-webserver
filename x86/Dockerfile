#
# Dockerfile for file hosting IOx Cisco platforms
#

# ARM or x86
FROM alpine:latest
#FROM arm64v8/alpine:latest

# Install
RUN apk update
RUN apk add --no-cache nginx

# Nginx configuration
RUN mkdir -p /run/nginx
RUN mkdir /www
RUN adduser -D -g 'www' www
RUN chown -R www:www /var/lib/nginx
RUN chown -R www:www /www
RUN mkdir -p /data/logs
RUN chown -R www:www /data/logs
RUN chmod -R 755 /data/logs

# copy files
COPY nginx.conf /etc/nginx/nginx.conf
COPY index.html /www/index.html
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

# open ports
EXPOSE 8000/TCP

ENTRYPOINT "/entrypoint.sh"