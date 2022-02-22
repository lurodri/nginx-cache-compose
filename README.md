# nginx-cache-compose
Example of nginx used as reverse proxy with cache for a backend app running on docker compose.

## Steps to run Docker Compose
### Compile Backend Java App
`cd java-app`<br>
`mvn clean install`<br>
`docker build . -t docker-java-hello-world-app`
<br>
<br>
### Configure nginx as a reverse proxy with cache
`cd nginx-cache`<br>
`docker build . -t nginx-cache`
<br>
<br>
docker-compose up
