# Intégration FranceConnect dans CAS


## Pourquoi ce POC ?

L'objectif est de poursuivre le travail de la journée chez Octo pour voir les moyens d'intégrer FranceConnect dasn CAS.
 - la connexion
 - la déconnexion
 - l'usage des scopes
 - utilisation du kit FranceConnect
 
Ce POC se positionne en tant que Fournisseur de services.


## Pré-requis

Nous devez créer un compte FranceConnect. Pour cela, il faut aller à l'url suivante : 
https://doc.integ01.dev-franceconnect.fr

Après avoir créer le compte, il est nécessaire de configurer le compte (https://doc.integ01.dev-franceconnect.fr/updateClient). Pour cela, il y a notamment les callbacks à configurer

 - Url de Callcack : http://localhost:8080/franceconnect-poc/oidc_callback
 - Url de Logout (après déconnexion) : http://localhost:8080/franceconnect-poc

Il est possible de définir plusieurs urls callbacks. Dans ce cas, il faut une url par ligne.

## Initialisation

Pour faire fonctionner l'application :

- cloner le dépôt git 
- configurer le fichier /src/main/webapp/openidc/certs
- configurer le fichier /src/main/webapp/WEB-INF/spring-configuration/pac4jContext.xml
- lancer tomcat :

	mvn tomcat:run

## Scénario

### Connexion depuis cas
- accéder avec votre navigateur à l'adressse :

	http://localhost:8080/franceconnect-poc-cas-pac4j/

- Saisir le nom d'utilisateur 
- Saisir le mot de passe
- Cliquer sur le lien oidc
- Vous obtenez la page vous indiquant que l'authentification est réussie

### Connection depuis une application casifiée
- Vous basculez sur le serveur cas
- Vous vous identifiez
- Vous revenez sur la page initialement demandé.


## Reste à faire

 - Transmettre les attributs au client CAS
 - Gérer la déconnexion pour proposer la déconnexion au niveau de FranceConnect
 
 
## Ressources

Ce projet utilise pac4j (https://github.com/pac4j/pac4j/)

Le code du projet suivant a été réutilisé :

	https://github.com/leleuj/cas-pac4j-oauth-demo

Nous utilisons le client oidc de la librairie pac4j.
Cependant, FranceConnect n'a pas de service discovery comme on le trouve pour Google par exemple
Pour l'instant, l'url est statique. Il sera nécessaire de le rendre configurable
