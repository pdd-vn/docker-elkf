# Elastic stack (ELK) on Docker with Filebeat
This is a fork from [docker-elk](https://github.com/deviantony/docker-elk) that is customized to use `Filebeat` as a proxy between services and `Logstash`.

All adjustments are intended for an MVP of ELK with `Filebeat`. For advanced configuration, please refer to the [original repo](https://github.com/deviantony/docker-elk) and [offical documents](https://www.elastic.co/guide/index.html)

**TODO**
- [] Deploy `Filebeat` and ELK stack to different server to reflect production use cases. 

### Usage
- Set up docker volume and user credentials:
  ```
  docker-compose up setup
  ```
- Run ELK stack with `Filebeat`:
  ```
  docker-compose -f docker-compose.yml -f extensions/filebeat/filebeat-compose.yml up -d
  ```
### Extras
- To check logs of a service, use:
  ```
    docker-compose -f docker-compose.yml -f extensions/filebeat/filebeat-compose.yml logs [SERVICE NAME]
  ```
- In production, assume that monitored services are deployed with docker, `filebeat.autodiscover` should be used to gather logs (from mounted volume).