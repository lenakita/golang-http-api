# golang-http-api

*Shamlessly* taken from [this](https://go.dev/doc/tutorial/web-service-gin) tutorial.

## Setup

```shell
go get
```

## Usage

### Server

```shell
go run *.go
```

```shell
$ go run *.go
[GIN-debug] [WARNING] Creating an Engine instance with the Logger and Recovery middleware already attached.

[GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
 - using env:   export GIN_MODE=release
 - using code:  gin.SetMode(gin.ReleaseMode)

[GIN-debug] GET    /albums                   --> main.getAlbums (3 handlers)
[GIN-debug] GET    /albums/:id               --> main.getAlbumByID (3 handlers)
[GIN-debug] POST   /albums                   --> main.postAlbums (3 handlers)
```

### Client

* Get all albums

```shell
curl http://localhost:8080/albums
```

```shell
$ curl http://localhost:8080/albums
[
    {
        "ID": "1",
        "Title": "Blue Train",
        "Artist": "John Coltrane",
        "Price": 56.99
    },
    {
        "ID": "2",
        "Title": "Jeru",
        "Artist": "Gerry Mulligan",
        "Price": 17.99
    },
    {
        "ID": "3",
        "Title": "Sarah Vaughan and Clifford Brown",
        "Artist": "Sarah Vaughan",
        "Price": 39.99
    }
]
```

* Get specific album

```shell
curl http://localhost:8080/albums/2
```

```shell
$ curl http://localhost:8080/albums/2
{
    "ID": "2",
    "Title": "Jeru",
    "Artist": "Gerry Mulligan",
    "Price": 17.99
}
```

* Add an album

```shell
curl http://localhost:8080/albums
    -H "Content-Type: application/json"
    --request "POST"
    --data '{"id": "4","title": "The Modern Sound of Betty Carter","artist": "Betty Carter","price": 49.99}'
```

```shell
$ curl http://localhost:8080/albums
    -H "Content-Type: application/json"
    --request "POST"
    --data '{"id": "4","title": "The Modern Sound of Betty Carter","artist": "Betty Carter","price": 49.99}'
{
    "ID": "4",
    "Title": "The Modern Sound of Betty Carter",
    "Artist": "Betty Carter",
    "Price": 49.99
}
```
