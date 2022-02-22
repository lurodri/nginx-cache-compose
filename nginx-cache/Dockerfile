FROM nginx:alpine

# nginx:alpine contains NGINX_VERSION environment variable, like so:
ENV NGINX_VERSION 1.21.6

# Install base to compile nginx and redis2-module
RUN apk update
RUN apk upgrade

EXPOSE 80

# Copy original configuration from the builder
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/nginx.conf
COPY localhost.conf /etc/nginx/conf.d/localhost.conf
