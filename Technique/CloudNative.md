# Avantages Cloud Native

## Vitesse
Rapidité de provisionner de nouveaux serveurs applicatifs, BDD,
Rapidité pour déployer de nouvelles versions
Moins de grosses erreurs car déploiements plus fréquents
Plus d'évolution micro car déploiements plus fréquents
Autonomie pour déployer : les équipes de Dev deviennent DevOps et prennent la main sur les serveurs via call d'API

## Sécurité
### Visibility
Tout est mesuré, monitoré , en cas de failure c'est immédiatement signalé

### Fault Isolation
Grâce aux micro-services, on isole chaque pan fonctionnel / produit en petits modules déployables indépendamment.
Par conséquent, si une brique est non fonctionnelle, elle n’empêchera pas le reste de fonctionner car chaque brique doit être indépendante des autres


###Fault tolerance
Circuit breaker
###Automated Tests

### Automated Recovery
A chaque fois qu'une erreur fatale se déclenche, les serveurs se redémarrent et suivent une procédure automatisée sans action humaine et à n'importe quelle heure


## Scale
Capacité à augmenter, diminuer le nombre de serveurs rapidement grâce aux système de pods déployables
> Demande d'avoir des applications stateless cependant : plus de clustered sessions, shared filesystems...
> Demande d'avoir des states managers (memcache par exemple) pour gérer de manière externe les sessions etc

## Mobile First

Grâce à l'imposition d'exposition des services via API, on peut facilement faire du mobile first.

## Environnements homogènes
Tous les environnements tournent sur la même stack technique 


## Logs
Logs centralisés, aggrégés, indexés.

##Antifragility

