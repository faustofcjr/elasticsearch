
#Criando um docker container
docker run -d --name elasticsearch --network elasticsearch_network  -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:7.9.2

#Copiar pasta elasticsearch-in-action para dentro do container

``` bash
git clone https://github.com/dakrone/elasticsearch-in-action.git -b 7.x
docker cp /home/faustofcjr/Desenvolvimento/elasticsearch/elasticsearch-in-action elasticsearch:/home/
```

# Run script populate.sh to recreate index get-together

``` bash
docker exec -it elasticsearch bash
cd /home/elasticsearch
./populate.sh
```
