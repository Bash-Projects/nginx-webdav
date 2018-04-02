Nginx WebDAV
============

Simple Nginx WebDAV host configuration for attached docker volume.

## Usage

Create a volume:

```
docker volume create --driver "local" davtest
```

Start nginx webdav server:

```
docker run -p 127.0.0.1:8080:80 -v davtest:/data --name dav lostintime/nginx-webdav:1.12.2-alpine
```

Where `davtest` is the name of 

### Create/Update

```
curl -X PUT \
  http://127.0.0.1:8080/hello.json \
  -H 'Content-Type: application/json' \
  -d '{
	"message": "Hello world!"
}'
```

### Get

```
curl -X GET http://127.0.0.1:8080/hello.json
```

### Copy

```
curl -X COPY http://127.0.0.1:8080/hello.json \
  -H 'Destination: /hello2.json'
```

### Move

```
curl -X MOVE http://127.0.0.1:8080/hello2.json \
  -H 'Destination: /hello3.json'
```

### Delete

```
curl -X DELETE http://127.0.0.1:8080/hello3.json
```
