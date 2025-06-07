# 6-Network Management Final Project
This repository builds upon an already  [existing GitHub repository](https://github.com/herlesupreeth/docker_open5gs#). It extends further upon this by adding metrics using two exporter repositories that provide prometheus with metric data.
- [iPerf3 exporter](https://github.com/edgard/iperf3_exporter) for packet loss, throughput metrics
- [Blackbox exporter](https://github.com/prometheus/blackbox_exporter/tree/master?tab=readme-ov-file) for packet loss, latency metrics

## Running
Navigate to the root directory of the repository.

To run the 5G core (open5gs):
```
sudo docker-compose -f sa-deploy.yaml up -d
```

To run the gNB and UE (UERANSIM):
```
sudo docker-compose -f nr-ue.yaml -f nr-gnb.yaml up -d
```

## Accessing the User Interfaces

The Web UI of Open5gs is being run on the port 9999 by the docker-compose. You can run the following command on your host machine to access this UI on http://localhost:19999.
```
ssh -L 19999:localhost:9999 s0193227@143.129.43.60
```

The Web UI of Prometheus is being run on the port 9090 by the docker-compose. You can run the following command on your host machine to access this UI on http://localhost:29999.
```
ssh -L 29999:localhost:9090 s0193227@143.129.43.60
```

The Web UI of Grafana is being run on the port 3000 by the docker-compose. You can run the following command on your host machine to access this UI on http://localhost:39999.
```
 ssh -L 39999:localhost:3000 s0193227@143.129.43.60
```

## Shutting down
To shutdown simply stop the UE and gNB containers:
```
sudo docker-compose -f nr-ue.yaml -f nr-gnb.yaml down
```

And then shut down the 5G core containers:
```
sudo docker-compose -f sa-deploy.yaml down
```
