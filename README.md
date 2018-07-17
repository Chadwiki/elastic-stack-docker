# docker-elastic
elastic stack on docker

### Pull the required docker images:
```
docker pull docker.elastic.co/elasticsearch/elasticsearch:6.3.1
docker pull docker.elastic.co/kibana/kibana:6.3.1
docker pull docker.elastic.co/logstash/logstash:6.3.1
```

### Add images to your local repo

```
docker push <the name of repository>/<the name of image>:<the name of tag>
```

1) First create the certs for the environment - from elasticsearch_tls
`docker-compose up`
2) Start elasticsearch: `docker-compose up`
3) Enable the trial license: `curl -k -XPOST https://localhost:9200/_xpack/license/start_trial?acknowledge=true`
4) Start kibana: `docker-compose up`

*********

#### Test