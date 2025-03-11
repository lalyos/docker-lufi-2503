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
```