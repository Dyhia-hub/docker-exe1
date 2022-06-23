# docker-exe1
exo1_tp git docker

## Commandes à exécuter  

## lancer un docker en mode interactif et avec un tty pour le display à partir d'une image alpine
## le nom de conteneur **myalpes**
## on défini /MountPoint comme point de montage des données de conteneur
## passer la commande /bin/ash


docker run -v /MountPoint -it --name myalpes alpine /bin/ash
## créer une image depuis le conteneur myalpes avec la méthode commit
docker commit myalpes myalpine:v12

## vérifier que l'image a été bien crée
213  docker images
## vérifier les métadata de l'image crée

docker history myalpine:v12
## Créer une nouvelle image à partir de conteneur myalpes avec la méthode Export/Import pour supprimer la métadata
docker export myalpes > myalpes.tar
cat myalpes.tar | docker import - my_alpine:v12
## vérifier que l'image a bien été crée
docker images
## vérifier les métadata de la nouvelle image my_alpine
docker history my_alpine:v12

## Se connecter au compte Docker_hub
docker login -u  -p 
## tager l'image qu'on va exporter sur le compte docker-hub en myalpino:v12
docker image tag my_alpine:v12 chabane7/myalpino:v12
## pusher l'image sur docker hub
docker push chabane7/myalpino:v12
