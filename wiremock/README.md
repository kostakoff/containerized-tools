# rocky 8 wiremock 3.5.2

## Run in docker compose

- deploy application container env in docker use compose
```bash
docker-compose up
```
- destroy application env
```bash
docker-compose down
```

Local urls: 
- http://localhost:8080/__admin/recorder/
- http://localhost:8080/__admin/mappings
- http://localhost:8080/actuator/health (springboot health endpint mock)

## Deploy to kubernetes
This deploy will pull follow docker images:
- application from github: docker.io/kostakoff/containerized-tools:wiremock3.5.2

Deployment:
- go to deployment folder
```bash
cd ./Deployment
```
- render helm chart
```bash
helm template my-wiremock
```
- install helm chart
```bash
helm install my-wiremock ./my-wiremock
```
- update deploy
```bash
helm upgrade --install my-wiremock ./my-wiremock
```
- remove helm chart
```bash
helm uninstall my-wiremock
```
Link for microk8s: https://wiremock.k8s.localhost/actuator/health
