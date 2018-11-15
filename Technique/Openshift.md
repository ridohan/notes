# Openshift

### Capacités
####  Déployer des images directement
####  Déployer un projet directement depuis git
####  Exposer son application via une route
####  Ajouter un pod ou en retirer à la volée
####  Transferer des fichiers depuis le container vers le local et vice versa
> Possibilité de synchroniser également les changements automatiquement entre la local et le container, pratique pour les devs
####  Créer des volumes persistants 
> Demande cependant de créer une fausse application pour tenir le volume

>``oc run dummy --image centos/httpd-24-centos7``
####  Port forwarding pour les devs 
####  Créer des BDDs en tant que ressource et les utiliser dans son container avec son application

####  Autoscale : Possibilité d'augmenter le nombre de pods en fonction des ressources utilisées

> HPA :  Horizontal Pod Autoscaler