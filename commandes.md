
# Video 1
### afficher les commandes
### liste des processus actifs sur docker
> docker ps
### droit 
> sudo chmod 666 /var/run/docker.sock
### prendre une image 
> docker pull alpine
### afficher les images sur le serveur
> docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
alpine       latest    49176f190c7e   2 weeks ago   7.05MB
### si on ne demande pas une version spécifique c'est la dernière qui est prise
### mais on peut directement charger une image en l'exécutant
> docker run alpine:latest
### pour afficher les processus en cours
> docker ps -a
CONTAINER ID   IMAGE           COMMAND     CREATED          STATUS                      PORTS     NAMES
3111f53c69f7   alpine:latest   "/bin/sh"   14 seconds ago   Exited (0) 13 seconds ago             relaxed_rosalind
### le processus n'est pas en cours d'exécution voir son statut
car pour cette image, rien ne lui a été demandée.
### pour le mettre en mode détaché
> docker run -di  --name alpine1 alpine:latest
### pour se connecter en mode interactive
> docker exec -ti alpine1 sh
### on se connecte à alpine 
docker exec -ti alpine1 sh
/ # ls
bin    dev    etc    home   lib    media  mnt    opt    proc   root   run    sbin   srv    sys    tmp    usr    var
/ # whoami
root
/ # exit
# Video 2
# lancer un serveur web nginx
> docker run -di --name web nginx:latest
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
025c56f98b67: Pull complete 
ca9c7f45d396: Pull complete 
ed6bd111fc08: Pull complete 
e25b13a5f70d: Pull complete 
9bbabac55ab6: Pull complete 
e5c9ba265ded: Pull complete 
Digest: sha256:ab589a3c466e347b1c0573be23356676df90cd7ce2dbf6ec332a5f0a8b5e59db
Status: Downloaded newer image for nginx:latest
c443a46df8df45c5e1932e6c3f65167620e23d0e11e7bcb1391b1115cb36a214
# pour arrêter le processus web
> docker stop web
# exposition des ports une application web est par défaut s'expose sur le 80, pour afficher les 8080 
# -p 8080:80  
> docker run -di -p 8080:80 --name web nginx:latest
# pour voir le serveur
http://127.0.0.1:8080
# pour afficher les informations réseaux
> docker inspect web
"IPAddress": "172.17.0.3",
http://172.17.0.3