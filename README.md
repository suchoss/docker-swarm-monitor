# docker-swarm-monitor
simple configurations to run docker swarm monitor componentes including prometheus server and pre-configured scraping

## run
```bash
$ git clone https://github.com/opvizordz/docker-swarm-monitor.git
$ cd docker-swarm-monitor
docker stack deploy -c docker-compose.stack.yml docker-swarm-monitor
```

### check status
```bash
docker stack ls # show swarm stack deployments and status
docker service ls # show services
docker service logs -f <service> # check logs for debugging purpose
docker stack rm docker-swarm-monitor # remove the project
```

The following components are part of this project

* cAdvisor
* node Exporter
* dockerd-exporter
* Prometheus
* Grafana

### Grafana dashboard
First we need to add Prometheus as main metrics data source. Go to Configuration > Data source menu and click on Add data source. Select Prometheus and set the internal docker prometheus URL, which should be http://prometheus:9090. A successful message should appear when saving.

Then go to Create > Import, load 11939 as dashboard ID, and select Prometheus source and woha!

(source https://blog.okami101.io/2022/02/setup-a-docker-swarm-cluster-part-v-monitoring/)
