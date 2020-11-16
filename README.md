# Elasticsearch Study Case

How to use and configure Elasticsearch.

## Elasticsearch and Docker

### 1 - Creating Elasticsearch Container

``` bash
docker run -d --name elasticsearch --network elasticsearch-network  -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:7.9.3
```

### How to configure book's [*Elasticsearch in Action*] code examples  from the book

- First, clone repository and copy them to elasticsearch container with command below:

``` bash
git clone https://github.com/dakrone/elasticsearch-in-action.git -b 7.x
docker cp elasticsearch/elasticsearch-in-action elasticsearch:/home/
```

- Finally, Run script populate.sh to recreate index get-together

``` bash
docker container exec -it elasticsearch bash
cd /home/elasticsearch
./populate.sh
```

### Specifying a cluster name in elasticsearch.yml

``` bash
docker container exec -it elasticsearch bash
vi config/elasticsearch.yml
```

### Specifying verbose logging via logging.yml

``` bash
docker container exec -it elasticsearch bash
vi config/log4j2.properties
```

### Adjusting JVM settings

``` bash
docker container exec -it elasticsearch bash
vi config/jvm.options

change:
# Xms represents the initial size of total heap space
# Xmx represents the maximum size of total heap space
-Xms1g
-Xmx1g

```

## Cerebro and Docker

Cerebro is an open source(MIT License) elasticsearch web admin tool built using Scala, Play Framework, AngularJS and Bootstrap.

You can find the official docker images in the official [docker hub repo](https://hub.docker.com/r/lmenezes/cerebro/).

For using latest docker cerebro image, execute:

``` bash
docker run --name cerebro-elasticsearch --network elasticsearch-network -p 9000:9000 lmenezes/cerebro
```