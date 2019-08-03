# DockerElasticSetup

## Step Network first

```
sudo docker network create somenetwork
```

## Step ElasticSearch
```
sudo docker run -d --name elasticsearch --net somenetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e 'xpack.security.enabled=false' -e 'xpack.monitoring.enabled=false' --restart=always -d --name elasticsearch elasticsearch:7.3.0
```

## Step Kibana
```
docker run -d --name kibana --net somenetwork -p 5601:5601 -e "XPACK_SECURITY_ENABLED=false" --restart=always --name kibana kibana:7.3.0
```
