# Nginx Reverse Proxy with Cache
Pretty simple sample of nginx used as reverse proxy with cache for a backend app, all running on docker compose.

## Steps to run locally with docker-compose
### 1) Compile Backend Java App
`cd java-app`<br>
`mvn clean install`<br>
`docker build . -t java-app`
<br>
<br>
### 2) Configure nginx as a reverse proxy with cache
`cd nginx-cache`<br>
`docker build . -t nginx-cache`
<br>
<br>
### 3) Run docker compose running both containers
`docker-compose up`

