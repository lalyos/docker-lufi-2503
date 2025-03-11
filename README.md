## First Container

```
docker run --interactive  --tty ubuntu
docker run -it ubuntu
```

```
apt-get update
apt-get install curl -y

curl 444.hu -L
```

html to text
```
apt-get install -y html2text
curl 444.hu -L | html2text
```

## Basic docker commands

```
docker ps
docker ps -a

docker rename 8a ubul
docker start ubul
docker attach ubul
```

start a new container
```
docker run -it --name masik ubuntu
docker rm masik
docker stop ubul
docker commit  ubul reader
```

```
#detached
docker run -d ubuntu
docker inspect ubuntu
```

overwrite CMD
```
docker run ubuntu echo hello
id=$(docker run -d ubuntu echo hello)
docker logs $id
```

## Lunch

```
docker run -it reader

apt-get install -y nginx
ps -ef
```

## Dockerfile


```
docker build -t web .
docker run -d web
docker run -d --name lunch -p 8888:80  web
```


## using start.sh as PID1

```
docker build -t web:v1 .
docker run -d --name coffee -p 8889:80  web:v1
docker run -d  -p 80  web:v1

docker run -d \
  -e TITLE="coffebreak for lalyos" \
  -p 80 \
  web:v1

```

git repo: https://github.com/lalyos/docker-lufi-2503/


docker build -t web:git https://github.com/lalyos/docker-lufi-2503.git

## poor-man automation

```
web() {
  [[ -f ${3} ]] && BODYSTR="$(cat $3)" || BODYSTR="${3:-use TITLE/COLOR/BODY env vars}"

  docker run \
    -d \
    -p 80 \
    -e TITLE="${1:-welcome}" \
    -e COLOR="${2:-hotpink}"  \
    -e BODY="${BODYSTR}" \
  web:git
}
```