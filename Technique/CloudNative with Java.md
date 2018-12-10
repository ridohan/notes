# Pyxies

### Codebase:
Le code est il bien centralisé dans un repo git ?

Est ce bien github ?

### Dependencies:
Les dépendances sont elles bien isolées et déclarées ?

Utilisation de maven ? Pas de jar en mode sauvage ?


### Configuration:
La configuration doit être stockée en variable d'environnement. Elle ne doit pas être dans le code sous quelque forme qu'il soit...

Quid de Consul, Peut on vraiment utiliser Consul pour centraliser les éléments de configuration tout en respectant ce facteur ? 
-- C'est compliqué car une release est censée être la constellation d'une build et d'une configuration à un instant T. Si la configuration change par exemple, alors une nouvelle release devrait être créée...


### Backing Services:
Les ressources sont elles attachées à l'application et non comprise dans l'application ? Peut on y accéder par un port spécifique ? Est ce déjà dockerisé ?


### Build, release, run:
Faire le point sur le CI / CD. A t on bien les différents processus d'isolés 
 
### Processes:
Faire en sorte que les applications soient bien stateless : rien n'est persisté dans l'application, typiquement les fichiers récupérés d'un serveur FTP par exemple ne doivent que transiter et non sauvegardés.

Elle ne doit pas dépendre non plus d'une structure de dossiers / fichiers ( typiquement ce qu'on faisait avant pour traiter des fichiers de données qu'on déposait dans un dossier local) 
Elle ne doit pas non plus dépendre de session locale dans la JVM par exemple, pas de stickysession, utiliser Redis / Memcached à la place

### Port binding:
Pas de war à deployer ensuite sur un tomcat par exemple, l'appli est autosuffisante dans le sens où elle expose elle même son port et qu'il est évidemment configurable


De maniere plus global, tout doit être dockerisé


### Concurrency:
Pas trop d'utilisation des Threads dans la JVM si possible, éviter tout ce qui est multithreading géré par du code custo.

L'idée est d'éviter de scaler en vertical ( plusieurs threads qui font la même chose sur la même machine ) mais plutôt d'utiliser du scaling horizontal (un thread pour récupérer les requêtes http , un autre pour gérer les batchs etc )

### Disposability:
Rapide à démarrer, rapide à arrêter
Cela sous entend aussi une facilité en cas de tiers ne repondant pas ( Hystrix ! )

Garder les requetes HTTP avec une durée de vie extremement rapide ( suivant le REST on va dire )
Dans le cas de websockets, c'est au client de tenter de se reconnecter.

L'idée est d'apporter surtout de la résilience.

 
### Dev/prod parity:
Keep development, staging, and production as similar as possible

Utiliser Docker pour avoir la meme stack en prod et en local par exemple, sans avoir forcément les mêmes volumes de données.

### Logs:
Logs en STDOUT pas de management de fichier comme des rolling appender ou autre.

Typiquement mettre une stack ELK / graylog pour centraliser les logs.
Penser a rendre les niveaux de logs configurables afin qu'en prod ou en local on ait pas le meme niveau d'infos si besoin.


### Admin processes:
Run admin/management tasks as one-off processes
‌
## Beyond the Twelve-factor Application:
### API first:
API as a first-class artifact of the development process

Pensez API First - Documentation / Contrat API / API Gateway / Securité 
### Telemetry:
Comment monitorer l'état de l'appli :
- Sondes
- Alertes KPI, Alertes materielles
- Graphiques

Voir comment prometeus peut nous aider


### Authentication and authorization:
Cloud-native applications would secure all of their endpoints
API Gateway ?
‌
## Best practices:
### Automated testing:
Makes good use of test automation
TDD, Tests d'inté, tests d'interface en cas de front
Comment automatiser l'execution de ces tests, en récupérer les rapports, déclencher des go / nogo automatiquement ?

### Continuous integration:
Automation of the tests running, build and quality check.
### Continuous delivery:
Release software rapidly get a tighter feedback loop

