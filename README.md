Le refactoring, c'est bien. Le refactoring, c'est beau. Mais le refactoring, est-ce vraiment pragmatique ?

Et si on arrêtait les débats stériles ? Avec Xtreme Refactoring, la seule loi : c'est le code. Dans cet environnement hostile, toutes les techniques sont permises.

Rejoignez le temps de ce hands-on le projet "Tennis Underground" en pleine expansion où vous pourrez démontrer vos talents de codeur face aux autres en livrant le plus rapidement possible toutes les nouvelles fonctionnalités qui ne cessent de germer dans les têtes de nos Products Owners.

TDDeur, DDDeur, Crapman : imposez votre style !

#Pré-requis technique 

Ce slot est un atelier de développement. Un ordinateur pour 2 au minimum est donc nécessaire, équipé du Wifi. Ce sont les seules choses réellement nécessaires.

## Setup du poste de travail 

 
#Déroulement de l'atelier 

##Principe
Les products owner vont au fil du déroulement de l'atelier vous demander d'implémenter de nouvelles fonctionalités afin
d'agrémenter le jeu du tennis. 

##Implémentation d'une nouvelle feature 

Au départ, vous disposez d'un programme qui fonctionne, il permet de jouer au tennis, et répond à la spécification suivante :

| Player1 Score | Player2 Score | displayScore() | comments |
|---|---|---|---|---|
| 0 | 0 | love-all | |
| 0 | 1 | love-fifteen ||
| 0 | 2 | love-thirty ||
| 0 | 3 | love-forty ||
| 0 | 4 | win for player2 | or player1 if inverted |
| 1 | 1 | fifteen-all ||
| 1 | 2 | fifteen-thirty ||
| 1 | 3 | fifteen-forty ||
| 1 | 4 | win for player2 | or player1 if inverted |
| 2 | 2 | thirty-all ||
| 2 | 3 | thirty-forty ||
| 2 | 4 | win for player2 | or player1 if inverted |
| 3 | 3 | deuce ||
| 3 | 4 | advantage player2 | or player1 if inverted|
| 3 | 5 | win for player2 | or player1 if inverted |
| 4 | 4 | deuce ||
| 4 | 5 | advantage player2 | or player1 if inverted |
| 2 | 4 | win for player2 | or player1 if inverted |

Des tests automatiques existent dans la classe **TennisTest** et permettent de vérifier ces règles.

##Vérification de l'implémentation de la feature et scoring

Lorsque vous serez certains que l'implémentation que vous avez effectuée est correcte, vous aurez deux choses à faire : 

1. Démarrer votre serveur en utilisant le main présent dans la classe ChallengesApi

2. Utiliser une requête curl pour vérifier votre implémentation. 

**Attention :**

* **Votre nombre d'essais est limité à 2**. Passez ce nombre, vous ne pourrez plus récupérer de points, mais vous pourrez toujours
savoir si votre implémentation est correcte. De la même façon, la réponse à la requête vous permettras de connaître vos
erreurs s'il y en a.

* Nous vous conseillons de couper votre serveur une fois votre implémentation est terminée, afin d'être sur d'avoir les derniers
changements lors de la prochaine feature. De la même façon, pensez à vérifier qu'il est démarré avant de faire vérifier votre code.


`
curl 'http://xxx.xxx.xxx.xxx:8082/compare' -X POST -H 'Pragma: no-cache' -H 'Origin: chrome-extension://fdmmgilgnpjigdojojpjoooidkmcomcm' -H 'Accept-Encoding: gzip, deflate' -H 'Accept-Language: fr-FR,fr;q=0.8,en-US;q=0.6,en;q=0.4' -H 'User-Agent: Mozilla/5.0 (iPad; CPU OS 9_1 like Mac OS X) AppleWebKit/601.1.46 (KHTML, like Gecko) Version/9.0 Mobile/13B143 Safari/601.1' -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'Cache-Control: no-cache' -H 'Connection: keep-alive' -H 'Content-Length: 0' --compressed
`

Réponse : 

`{"success":true,"scoreInfo":{"details":{"scoresByTurn":[{"score":0}]},"total":0,"ranking":1},"trialNumberLeft":1,"errors":[]}`


##Nouvelles features

Au fil des nouvelles features qui vous serons demandées, les products owners vont pusher des modifications à la base de code. 
Pour les récupérer, il vous suffira de faire : 

`git pull --rebase`


