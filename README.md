# remix-ide-docker
Dockerfile for building remix-ide docker image

After building the image (`$ docker build . --tag mnxzyw/remix-ide`), the container can be started as follows:
`$ docker run -itd -p8080:8080 -p65520:65520 -v/path/to/your/solidity/files/:/app mnxzyw/remix-ide`

When the container is successfully started the remix IDE can be accessed through the browser, using url:
`http://localhost:8080` 

Remixd is automatically started in the same container, so it can be used right away (to make your local files available in the browser).

## attention：
- *http://127.0.0.1:8080 is not allowed to connect local filesystem[port 65520] , Only the domain localhost is allowed to access*

## docker-compose
```
version: '3'
services:
  remix-ide:
    image: mnxzyw/remix-ide:latest
    container_name: remix-ide
    restart: unless-stopped
    ports:
      - 8080:8080
      - 65520:65520
    volumes:
      - $FILE_PATH:/app
```
