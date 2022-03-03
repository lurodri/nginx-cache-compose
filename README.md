# Nginx Reverse Proxy with Cache
Pretty simple sample of nginx used as reverse proxy with cache for a backend app, all running on docker compose.

## Architecture
![image](https://user-images.githubusercontent.com/6126997/156385635-821d42c3-c7ad-422d-aa7a-61cdcc362b11.png)

### 1) Request coming from a caller
All HTTP requests coming from the callers will go thru Ngnix.
### 2) Nginx is used as Reverse Proxy
Nginx checks for cached responses on the instance receiving the request, if it is available on the cached, it will contest the request with appropriate chace entry based on its $key.
### 2) Backend in case of a Cache Miss
Otherwise, if the data is still not cached, Nginx will pass the request as-is to the backend and will store the backend's response on the cache, for the next requests, before sending it back to the caller.

#### Important to keep in mind that this is not using a distributed cached, so if you have multiple instances of your application and the reverse proxy in front of it, each Nginx instance will have its own cached data, therefore you could have a higher incidence of cache miss compared to the architecture using a [distributed cache](https://github.com/lurodri/nginx-redis2).

## Steps to run locally with docker-compose
### 1) Compile Backend Java App & Nginx Reverse Proxy
`docker-compose build`
<br>
### 2) Run docker compose running both containers
`docker-compose up`

## Test it locally
`curl -v http://localhost/cached`
