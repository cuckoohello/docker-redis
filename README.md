## Redis Dockerfile


This repository contains **Dockerfile** of [Redis](http://redis.io/) for [Docker](https://www.docker.io/) built on debian:jessie.

This repository forks from [dockerfile/redis](https://github.com/dockerfile/redis), using debian instead of ubuntu and installing redis-server from debian repo instead of building it.

### Dependencies

* [debian/jessie](https://registry.hub.docker.com/_/debian/)


### Installation

1. Install [Docker](https://www.docker.io/).

2. Download [cuckoohello/redis](https://registry.hub.docker.com/u/cuckoohello/redis/) from public [Docker Registry](https://index.docker.io/): `docker pull cuckoohello/redis`

   (alternatively, you can build an image from Dockerfile: `docker build -t="cuckoohello/redis" github.com/cuckoohello/redis`)


### Usage

#### Run `redis-server`

    docker run -d --name redis -p 6379:6379 cuckoohello/redis

#### Run `redis-server` with persistent data directory. (creates `dump.rdb`)

    docker run -d -p 6379:6379 -v <data-dir>:/data --name redis cuckoohello/redis

#### Run `redis-server` with persistent data directory and password.

    docker run -d -p 6379:6379 -v <data-dir>:/data --name redis cuckoohello/redis redis-server /etc/redis/redis.conf --requirepass <password>

#### Run `redis-cli`

    docker run -it --rm --link redis:redis cuckoohello/redis bash -c 'redis-cli -h $REDIS_PORT_6379_TCP_ADDR'
