# Note
 
This is a fork from [sheepkiller/kafka-manager-docker](https://github.com/sheepkiller/kafka-manager-docker) I mostly did 
in order to have some settings adjusted, dependences updated and to get latest available kafka manager and to get this 
working in a full docker compose setup that I have at my [docker-compose repository](https://github.com/mmaia/docker-compose-images/tree/master/kafka).

# Kafka Manager Dockerfile
[kafka manager](https://github.com/yahoo/kafka-manager) is a tool from Yahoo Inc. for managing [Apache Kafka](http://kafka.apache.org).

## Base Docker Image ##
* [centos:7](https://hub.docker.com/_/centos/)

## Howto
### Quick Start
```
docker run -it --rm  -p 9000:9000 -e ZK_HOSTS="your-zk.domain:2181" -e APPLICATION_SECRET=letmein sheepkiller/kafka-manager
```
(if you don't define ZK_HOSTS, default value has been set to "localhost:2181")


### Use your own configuration file
you can specify a configuration file via an environment variable.
```
docker run [...] -v /path/to/confdir:/opt -e KM_CONFIG=/opt/my_shiny.conf sheepkiller/kafka-manager
```
### Pass arguments to kafka-manager
```
docker run -it --rm  -p 9000:9000 -e ZK_HOSTS="your-zk.domain:2181" -e APPLICATION_SECRET=letmein -e KM_ARGS=-Djava.net.preferIPv4Stack=true sheepkiller/kafka-manager 
```

### Specify a revision
If you want to upgrade/downgrade this Dockerfile, edit it and set `KM_VERSION` and `KM_REVISION` to fetch the release from github.
