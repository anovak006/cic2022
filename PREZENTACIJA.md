---
marp: true
theme: default
---
# CIC 2022
## Vodič za brzi početak - Python API u kontejneru
Albert Novak https://github.com/anovak006/cic2022

---
# Kontejneri nasuprot virtualnim poslužiteljima
![Kontejneri nasuprot virtualnim poslužiteljima](https://www.docker.com/wp-content/uploads/Blog.-Are-containers-..VM-Image-1-1024x435.png)
Izvor: https://www.docker.com/blog/containers-replacing-virtual-machines/

---
# Kontejner u virtualnom poslužitelju

![w:700](https://www.docker.com/wp-content/uploads/Are-containers-..-vms-image-2-1024x759.png)
Izvor: https://www.docker.com/blog/containers-replacing-virtual-machines/

---
# Instalirajmo potrebne alate
### VS Code - https://code.visualstudio.com/docs/setup/linux
```shell
sudo apt install ./code_*.deb
```

### Docker
```shell
# sudo apt install docker.io
```
Ne koristiti snap verziju!

---
# Podesiti adresni prostor

```shell
# vi /etc/docker/daemon.json
{
  "default-address-pools":
  [
    {"base":"172.18.0.0/16","size":24}
  ]
}
# systemctl restart docker
```

---
### Docker Compose - https://docs.docker.com/compose/install/
```shell
$ DOCKER_CONFIG=$DOCKER_CONFIG:-$HOME/.docker}
$ mkdir -p $DOCKER_CONFIG/cli-plugins
$ curl -SL https://github.com/docker/compose/releases/download/v2.4.1/docker-compose-linux-x86_64 \
-o $DOCKER_CONFIG/cli-plugins/docker-compose
```
```shell
 $ chmod +x $DOCKER_CONFIG/cli-plugins/docker-compose
 # Ako je umjesto $HOME /usr/local/lib/
 $ sudo chmod +x /usr/local/lib/docker/cli-plugins/docker-compose
 ```
---
# Preuzmimo projektnu razvojnu okolinu
```shell
> git clone https://github.com/anovak006/cic2022.git
```
## I vratimo se na početak
```shell
$ git checkout b6886455799
```
---
# Visual Studio Code - remote plugin
![alt](https://code.visualstudio.com/assets/docs/remote/containers/architecture-containers.png)

---
# Podesiti remote plugin
Urediti potrebne postavke u datoteci `.devcontainer/devcontainer.json`

### Ostale postavke VS Code
Nalaze se u dirketoriju `.vscode`

<!-- footer: `git checkout 096a2076cdc`-->
---
# Slojevi slike kontejnera
![alt](https://cdn.buttercms.com/CLQJN3yRRcS7oGqm7yKb)
Izvor: https://www.metricfire.com/blog/how-to-build-optimal-docker-images/

---
# Višestupanjska (multi-stage) slika kontejnera
![alt](https://cdn.buttercms.com/PpIR4HUFTuSMirdt5pxC)
Izvor: https://www.metricfire.com/blog/how-to-build-optimal-docker-images/

---
# Priprema kontejnera

## Kroz terminal
```shell
# Napravi novi kontejner
$ docker build -t cic2022:latest -f Dockerfile.cic2022 .
# Napravi novi kontejner specifičnog stupnja (stage)
$ docker build --target cic2022-dev -t cic2022-dev:latest -f Dockerfile.cic2022 .
```

## Kroz VS Code

F1 pa odabrati `Remote-Containers: Rebuild and Reopen in Container `
Izvor: https://code.visualstudio.com/docs/remote/create-dev-container

<!-- footer: `git checkout b52d22a9755`-->
---
# FastAPI - RESTful API u par linija koda
![HTTP Methods](https://ws.apms.io/api/_files/WScS4PCt2atRRbGB8YUCE8/download/)
Izvor: https://appmaster.io/blog/what-rest-api-and-how-it-differs-other-types
<!-- footer: `git checkout c3053a403a9`-->

---
# I malo složeniji primjer s elementima CRUD-a
## Dodat ćemo i jedan FastAPI router da bude zanimljivije

<!-- footer: `git checkout 3b99c73f3cc`-->

---
# Naglasci
- Sav kod možemo izvršavati u kontejneru potpuno izoliran
- VS Code Remote-Containers omogućava nam jednostavno debugiranje
- Multi-stage kod izrade slike kontejnera omogućava nam uštede resursa u produkciji
- FastAPI omogućava nam brz razvoj dokumentiranog API-a s validacijom ulaznih podataka

<!-- footer: ''-->
---
# Post-credits
---
![VS Code Remote Containers arhitecture](https://code.visualstudio.com/assets/docs/remote/containers/architecture-containers.png)
Izvor: https://code.visualstudio.com/docs/remote/containers

---
![Traefik architecture w:860](https://traefik.io/static/83ea42c9e8101dcf2a16f380fe3aac08/053ba/diagram.webp)
Izvor: https://traefik.io/traefik/