# Monitor docker compose logs

## Usage
* copy this repository

* [use an include](https://docs.docker.com/compose/multiple-compose-files/include/) to add to your existing compose file

* grafana is exposed on port 3000. A datasource is already configured to get logs by containers

### Architecture

This docker compose contains only grafana, loki and logtail

```mermaid
graph TD

subgraph docker compose
subgraph log monitoring
g[grafana]
loki[(loki)]
lt[logtail]
end
c1[container 1]
c2[container 2]
end

g --datasource--> loki
lt --push logs--> loki
lt --collect logs--> c1
lt --collect logs--> c2

```
