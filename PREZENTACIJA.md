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
# Postavimo Python razvojnu okolinu
```shell
> git clone https://github.com/anovak006/cic2022.git
> python3 -m venv venv
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

<!-- footer: `git checkout `-->

