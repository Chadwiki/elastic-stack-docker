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
1) Create your docker network:
- `docker network create esnet`

2) Create the ssl certs for the environment, from elasticsearch DIR:
- `docker-compose -f create-certs.yml up`

3) copy certs directory over to the kibana directory:
- clean up unneeded certs/host folders:

4) Update the elasticsearch/.env file with your password:
- `ELASTIC_PASSWORD=changeme`

5) Start elasticsearch from its directory with:
- `docker-compose up`

6) Enable the trial license:
- `curl -k -u elastic -XPOST https://localhost:9200/_xpack/license/start_trial?acknowledge=true`

7) Update kibana user:
- `curl -k -u elastic -XPOST "https://localhost:9200/_xpack/security/user/kibana/_password" -H 'Content-Type: application/json' -d'
{"password":"changeme"}'`

8) Update the kibana.yml with your new kibana credentials
- `elasticsearch.password: "changeme"`

9) Start kibana from its directory with:
- `docker-compose up`


``
*********

#### Informational:
- https://www.elastic.co/guide/en/elasticsearch/reference/current/security-api-change-password.html

##### Testing ssl from container
- ` curl --cacert certs/ca/ca.crt -u elastic:changeme https://es01:9200`
