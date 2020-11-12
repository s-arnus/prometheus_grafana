# prometheus_grafana
Project to run Prometheus and Grafana with Docker Compose. Tested on a single Raspberry Pi 4.

## Requirements
 - Docker version **19.03.0 or higher** is installed
 - Docker-compose is installed


## Starting and running the services

To start in the foreground:
```
docker-compose up
```

To start in the background:
```
docker-compose up -d
```

Show status of containers:
```
docker-compose ps
```

Examples on how to push metrics to pushgateway
```
echo "some_metric 3.14" | curl --data-binary @- http://pushgateway.example.org:9091/metrics/job/some_job

cat <<EOF | curl --data-binary @- http://pushgateway.example.org:9091/metrics/job/some_job/instance/some_instance
# TYPE some_metric counter
some_other_metric{label="val1"} 42
# TYPE another_metric gauge
# HELP another_metric Just an example.
another_metric 2398.283
EOF
```

## Terminating the service
Stop and remove all containers, images, volumes:
```
docker-compose down
```

## References
Some materials that were used in the creation of content in this repository:
 - https://prometheus.io/docs/guides/cadvisor/
 - https://grafana.com/docs/grafana/latest/installation/docker/
 - https://hub.docker.com/r/zcube/cadvisor
 - https://github.com/vegasbrianc/prometheus
 - https://grafana.com/grafana/dashboards/11600
 - https://prometheus.io/docs/prometheus/latest/getting_started/
 - https://github.com/prometheus/pushgateway
