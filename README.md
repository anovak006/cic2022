# CIC 2022: Vodič za brzi početak - Python API u kontejneru

Trebate složiti API u par dana, a da je skalabilan, da ga od početka razvijate u kontejneru i pripremate za kasniju produkciju, da se magično stvori i dokumentacija? Bez obzira jeste li samo radoznali ili volite programirati kao ja ova prezentacija bi vam trebala pomoći da preskočite neke korake i brzo pohvatate što je to [FastAPI](https://fastapi.tiangolo.com/), kako koristiti [docker-compose](https://docs.docker.com/compose/), kako povezati kontejnere putem [Treafik proxya](https://traefik.io/) i uspostaviti razvojnu okolinu u [VS Code](https://code.visualstudio.com/) kojom možete direktno [debugirati svoj API u kontejneru](https://code.visualstudio.com/docs/containers/debug-common).

# Postavljanje razvojne okoline

## Razvojna okolina

Razvojna okolina prilagođena je razvoju u kontejnerima. Za razvoj se koristiti Visual Studio Code zajedno s ekstenzijom Remote-Containers koja olakšava razvoj i testiranje u kontejnerima. Više o Remote-Container ekstenziji i razvoju koda u kontejneru možete naći u članku [Developing inside a Container](https://code.visualstudio.com/docs/remote/containers).

### Priprema kontejnerske okoline

Za razvoj se koriste kontejneri i docker. Da bi se uspostavila razvojna okolina potrebno je instalirati docker ili sličan kontejnerski sustav. Ovdje je **važno** napomenuti da nije podržana snap verzija dockera zbog nemogućnosti pristupa [home direktoriju](https://github.com/microsoft/vscode-remote-release/issues/2817). Docker dolazi s početno definiranim opsegom mreža /16 što je previše za razvojnu okolinu te je preporuka da istu smanjimo na /24. Na linux sustavima treba kreirati ili urediti datoteku /etc/docker/daemon.json u kome će se postaviti željeni mrežni raspon.

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

Ukoliko imate od ranije kreirane docker mreže potrebno je iste obrisati prije promjene ospega adresnog prostora zbog mogućih preklapanja istih što će dovesti do poteškoća prilikom podizanja docker servisa.

```shell
$ docker network ls
NETWORK ID     NAME      DRIVER    SCOPE
baf620f8f015   bridge    bridge    local
ec40fa749265   host      host      local
0937386ff5c7   none      null      local
9ce001177c4e   proxy     bridge    local
$ docker network rm proxy
```
