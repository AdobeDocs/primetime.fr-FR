---
title: Présentation des mesures côté serveur
description: Présentation des mesures côté serveur
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '2205'
ht-degree: 0%

---

# Présentation des mesures côté serveur {#understanding-server-side-metrics}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.


## Introduction {#intro}

Ce document décrit les mesures côté serveur d’authentification Adobe Primetime générées par le service de surveillance du service de droits (ESM). Il ne décrit pas les mêmes événements du point de vue du client (ce que les programmeurs verraient s’ils mettaient en oeuvre un service de mesure tel qu’Adobe Analytics sur leur page/application).

## Résumé des événements {#events_summary}

Du point de vue du serveur d’authentification Adobe Primetime, les événements suivants sont générés :

* **Événements générés dans le flux d’authentification**(Une connexion réelle avec le MVPD)

   * Notification de la tentative AuthN : cette opération est générée lorsque l’utilisateur est envoyé au site de connexion MVPD.
   * Notification d’AuthN en attente : si l’utilisateur parvient à se connecter avec son MVPD, celui-ci est généré lorsque l’utilisateur est redirigé vers l’authentification Primetime.
   * Notification d’AuthN accordée : cette notification est générée lorsque l’utilisateur est de retour sur le site du programmeur et a récupéré le jeton d’authentification à partir de l’authentification Primetime.
* **Flux d’autorisation** (Juste une vérification de l’autorisation avec un MVPD)\
  *Condition préalable requise :* Jeton AuthN valide
   * Notification d’une tentative AuthZ
   * Notification d’AuthZ accordée
* **Requête de lecture réussie**\
  *Condition préalable requise :* Jetons AuthN et AuthZ valides
   * Notification d’une vérification avec l’authentification Adobe Primetime
   * Une requête de lecture nécessite une authentification accordée et une autorisation accordée.


Le nombre d’utilisateurs uniques est présenté en détail dans la section [Utilisateurs uniques](#unique-users) ci-dessous. En règle générale, comme les réponses d’authentification et d’autorisation accordées sont généralement mises en cache, les formules suivantes s’appliquent :

* Nombre de tentatives AuthN \> Nombre de tentatives AuthN accordées
* Nombre de tentatives AuthZ \> Nombre de tentatives AuthZ accordées
* Nombre de tentatives AuthZ \> Nombre d’tentatives AuthN accordées (généralement)
* Nombre de demandes de lecture réussies \> Nombre d’AuthZ accordées


### Exemple {#example}

L’exemple suivant montre les mesures côté serveur pour un mois pour une marque :

| Mesure | MVPD 1 | MVPD 2 | … | MVPD | Total |
| -------------------------- | ------ | ------ | - | ------ | ---------------------------------------------- |
| Authentifications réussies | 1125 | 2892 |   | 2203 | SUM(MVP1+...MVPD n) |
| Autorisations réussies | 2527 | 5603 |   | 5904 | SUM(MVP1+...MVPD n) |
| Demandes de lecture réussies | 4201 | 10518 |   | 10737 | SUM(MVP1+...MVPD n) |
| Utilisateurs uniques | 1375 | 2400 |   | 2890 | SOMME de tous les utilisateurs pour tous les MVPD dédupliqués\* |
| Tentatives d’authentification | 2147 | 3887 |   | 3108 | SUM(MVP1+...MVPD n) |
| Tentatives d’autorisation | 2889 | 6139 |   | 6039 | SUM(MVP1+...MVPD n) |

</br>

Dans ce cas, la déduplication ne doit pas avoir d’effet, car les utilisateurs MVPD différents ne doivent pas recevoir le même identifiant utilisateur. Lorsque vous effectuez une somme pour deux marques différentes mais le même MVPD, l’effet de déduplication doit être beaucoup plus important.

## Déclencheurs d’événement {#event_triggers}

### Nouvel utilisateur - Flux complet {#new-user-full-flow}

Le graphique suivant décrit les événements et les étapes pour un utilisateur sans jeton d’authentification (un nouvel utilisateur ou un utilisateur dont le jeton d’authentification a expiré) :



![](assets/ae-flow-with-events.png)



Le flux implique des allers-retours vers les MVPD pour l’authentification (#5 to \#7) et l’autorisation (\#11).



Une fois le flux terminé, les jetons Authentification et Autorisation sont mis en cache sur le périphérique de l’utilisateur. Les valeurs de durée de vie (TTL) des jetons d’authentification sont comprises entre 6 heures et 90 jours. Une expiration de jeton AuthN force automatiquement une expiration de jeton AuthZ. La valeur TTL du jeton d’autorisation est généralement de 24 heures.

| Événements côté serveur déclenchés | <ul><li>Tentative d&#39;authentification, Authentification en attente, Authentification accordée</li><li>Tentative d’autorisation, autorisation accordée</li><li>Requête de lecture réussie</li></ul> |
|---|---|


### Utilisateur récurrent - Jetons AuthZ et AuthN mis en cache

Pour les utilisateurs qui disposent de jetons AuthZ et AuthN valides mis en cache, les étapes suivantes se produisent :


![](assets/ae-flow-tokens-cached-web.png)



Cela se déclenche automatiquement lors de l’appel de `getAuthorization()`et implique uniquement des vérifications avec l’authentification Adobe Primetime. Le MVPD n’est pas impliqué dans ce flux.


| Événements côté serveur déclenchés | * Requête de lecture réussie |
|---|---|


### Utilisateur récurrent - Jetons AuthN mis en cache, jeton AuthZ expiré

Pour les utilisateurs qui disposent encore de jetons AuthN valides, les étapes suivantes se produisent :

![](assets/ae-flow-authn-token-cached.png)


Ce flux implique un aller-retour au MVPD.


| Événements côté serveur déclenchés | <ul><li>Tentative d’autorisation, Autorisation OK</li><li>Requête de lecture réussie</li> |
|---|---|

## Événements d’authentification {#authn_events}

### Tentative d’authentification {#authentication-attempt}

Comme illustré dans le diagramme ci-dessus, les événements d’authentification ne sont déclenchés que lorsque l’utilisateur effectue un aller-retour vers le MVPD ; les événements d’authentification n’incluent pas les authentifications de jeton mises en cache.

L’événement de tentative d’authentification est déclenché lorsque l’utilisateur a cliqué sur un MVPD particulier dans le sélecteur.

* Le premier événement du côté MVPD qui se rapproche est le chargement de la page.
* L’authentification Adobe Primetime ne comptabilise pas les tentatives répétées de l’utilisateur de se connecter à la page MVPD (mot de passe incorrect, réessayez).
* plusieurs tentatives sont comptabilisées comme une seule tentative
* Certains MVPD effectuent également l’autorisation à l’étape Authentification et l’utilisateur n’est pas redirigé en cas d’échec de l’autorisation.

### Authentification en attente {#authentication-pending}

Cet événement se produit lorsque le processus de redirection vers l’authentification Adobe Primetime a commencé.

### Authentification accordée {#authentication-granted}

L&#39;utilisateur est un abonné connu du MVPD, généralement avec un abonnement à la télévision payante, mais parfois avec seulement un accès Internet. Une authentification réussie peut se produire soit parce que l’utilisateur a explicitement saisi des informations d’identification valides avec son MVPD, soit parce qu’il a précédemment saisi des informations d’identification valides et que l’option &quot;Mémoriser&quot; a été cochée (et que la session précédente n’avait pas expiré).

Le MVPD envoie donc une réponse positive à l’authentification Adobe Primetime à la demande d’authentification et l’authentification Adobe Primetime crée une *Jeton AuthN*.

* L’authentification est généralement mise en cache pendant une longue période (un mois ou plus). De ce fait, les événements d’authentification ne seront plus présents tant que le jeton n’expire pas et que le flux n’est pas redémarré.
* La connexion à partir d’un autre site/application par le biais de l’authentification unique ne déclenche pas d’événements d’authentification.



### Authentification Comcast {#comcast-authentication}

Comcast a un flux AuthN différent du reste des MVPD.

Les fonctions suivantes décrivent les différences :

* **Comportement du cookie de session**: cela entraîne la suppression complète des jetons d’authentification une fois que l’utilisateur a fermé le navigateur. Cette fonctionnalité est présente sur le web uniquement. L’objectif principal est de vous assurer que votre session Comcast n’est pas conservée sur les ordinateurs non sécurisés/partagés. L’impact est qu’il y aura plus de tentatives d’authentification/flux attribués que pour le reste des MVPD.

* **AuthN par requestorID**: Comcast ne permet pas que l’état AuthN soit mis en cache d’un ID de demandeur à un autre. Pour cette raison, chaque site/application doit accéder à Comcast pour obtenir un jeton d’authentification. Outre les considérations d’expérience utilisateur, l’impact, comme ci-dessus, est que davantage de tentatives d’authentification / d’événements attribués seront générés.

* **Authentification passive**: afin d’améliorer l’expérience utilisateur tout en conservant la fonctionnalité AuthN par requestorID , un flux d’authentification passive se produit dans un iFrame masqué. L’utilisateur ne voit rien, mais les événements seront toujours déclenchés comme auparavant.

Si l’utilisateur clique sur &quot;Mémoriser&quot; dans la page de connexion Comcast, les visites suivantes sur cette page (dans une période de 2 semaines) ne seront qu’une redirection rapide. Dans le cas contraire, les utilisateurs devront s’authentifier sur la page.

### Authentification non réussie {#unsuccessful-authentication}

Une authentification infructueuse n’est pas un événement en soi dans l’authentification Adobe Primetime, mais peut être considérée comme la différence entre les tentatives et les succès.

Dans la version de mai 2013, l’authentification Adobe Primetime ajoutera des codes d’erreur pour les authentifications en échec dues à des erreurs système ou réseau, y compris les erreurs DRM (échec de la liaison de jetons) et les erreurs LSO (pas d’espace pour écrire le jeton, etc.).

### Taux de conversion de l’authentification {#authenitication-conversion-rate}

Une mesure intéressante dont les programmeurs peuvent effectuer le suivi est le taux de conversion de l’authentification, calculé comme (requêtes AuthN / AuthN accordées)%.

Quelques remarques sur les mesures :

* Puisqu’il s’agit d’une mesure basée sur un événement, elle ne reflète pas vraiment le taux de conversion unique de l’utilisateur (si un utilisateur effectue huit tentatives et réussit la neuvième fois), cela se reflétera très mal dans le taux de conversion ci-dessus.
* Il n’est pas possible (encore) dans l’authentification Adobe Primetime (côté serveur) de calculer une conversion d’authentification unique basée sur .
* Si des tentatives d’authentification automatique n sont présentes dans le site/l’application, la mesure ci-dessus est également biaisée.

## Événements d’autorisation {#authorization_events}

### Tentative d’autorisation {#authorization_attempt}

Outre l’obtention d’un jeton d’authentification, les utilisateurs doivent également obtenir un jeton d’autorisation avant de lire le contenu. Cela se produit généralement après l’authentification ou si le jeton d’autorisation expire. Puisque cette vérification est effectuée côté serveur (des serveurs d’authentification Adobe Primetime aux serveurs MVPD), l’utilisateur n’est pas tenu de faire quoi que ce soit.

### Autorisation accordée {#authorization-granted}

Une &quot;autorisation accordée&quot; indique que l’abonnement de l’utilisateur authentifié inclut la programmation demandée.

Notez que tous les MVPD ne prennent pas en charge une étape d’autorisation distincte ; pour certaines authentifications, il s’agit d’une autorisation. Le MVPD envoie une réponse réussie à l’authentification Adobe Primetime à la requête AuthZ du canal principal, et l’authentification Adobe Primetime crée un jeton AuthZ.

* Le jeton AuthZ est mis en cache pendant une période donnée, généralement 24 heures. Durant cette période, aucun événement AuthZ ne sera déclenché.
* Certains MVPD fonctionnent avec les autorisations au niveau des ressources, d’autres avec les autorisations au niveau des canaux ; - selon le canal utilisé, plus ou moins d’événements AuthZ sont déclenchés. Même pour l’autorisation au niveau du canal, la mise en cache est en place. Par conséquent, si la même ressource est demandée en moins de 24 heures, aucun événement ne sera déclenché.

### Autorisation refusée {#authorization-denied}

Si une autorisation est refusée, l’utilisateur authentifié ne dispose pas d’un abonnement confirmé à la programmation demandée. La cause la plus probable est que le canal ne fait pas partie du module d’abonnement de l’utilisateur, mais cela peut également refléter un utilisateur disposant uniquement d’un accès Internet à partir du MVPD.

Pour certains MVPD, les utilisateurs sont authentifiés avec succès même s’ils ne disposent que d’un abonnement Internet du MVPD (pas d’abonnement à la télévision payante). Dans ce cas, même si le canal pour lequel l’utilisateur demande l’autorisation figure dans le package de base, l’autorisation est refusée.

Certains MVPD proposent des messages d’erreur personnalisés pour les refus AuthZ qui peuvent inclure des offres de mise à niveau de leur package.


### Taux de conversion d’autorisation {#authorization-conversion-rate}

Le taux de conversion d’authentification peut être calculé comme suit : (requêtes AuthZ / AuthZ accordées)%.

### Requête de lecture réussie {#successful-play-request}

Un utilisateur authentifié et autorisé est autorisé à afficher du contenu protégé.

Lors d’une requête de lecture réussie, l’authentification Adobe Primetime génère un jeton multimédia de courte durée affirmant que l’utilisateur est autorisé à regarder la vidéo demandée. Le programmeur utilise ce jeton multimédia pour une validation ultérieure de la visionneuse potentielle. Les jetons multimédia sont suivis en tant que requêtes de lecture réussies.

* L’authentification Adobe Primetime fonctionne *not* vérifiez si la lecture vidéo a réellement commencé après la génération du jeton multimédia. Par exemple, en cas de géolocalisation du contenu, la transaction compte toujours comme une requête de lecture réussie, même si le flux ne commence jamais réellement.
* Puisque les jetons AuthN et AuthZ mettent en cache la réponse MVPD pendant une période donnée, l’événement de requête de lecture réussi est l’événement le plus fréquent des mesures.

## Utilisateurs uniques {#unique-users}

### Définition {#definition}

Lors d’une authentification réussie, l’authentification Adobe Primetime suit l’existence d’un utilisateur unique, en fonction de la valeur d’identifiant utilisateur MVPD renvoyée.  Cette valeur est basée sur les informations de connexion de l’utilisateur, mais elle ne contient aucune information d’identification personnalisée.

Cette valeur est également transmise au site/à l’application dans le rappel sendTrackingData .

Cette valeur peut être persistante sur plusieurs périphériques (le MVPD produit la même valeur pour un utilisateur donné, quel que soit l’endroit où se produit la connexion) ou transitoire (pour chaque connexion, une nouvelle valeur est générée, que le MVPD mappe dans son serveur principal. En règle générale, les valeurs fournies par les MVPD à l’authentification Adobe Primetime sont persistantes entre les sessions et les appareils, mais, comme nous l’avons vu, la persistance n’est ni garantie ni validée.

Cette valeur sert à calculer les utilisateurs uniques. La valeur signalée (par ID/intervalle/MVPD de demandeur) est dédupliquée pour l’intervalle en question. Ainsi, la somme des utilisateurs uniques par jour est généralement différente de la valeur mensuelle, la valeur mensuelle ayant la valeur la plus faible.

Ce nombre inclut tous les événements provenant de l’authentification Adobe Primetime, moins les tentatives d’authentification (qui n’ont pas d’ID utilisateur), mais inclut les autorisations de tentative (et éventuellement d’échec).

### Exemples {#examples}

#### Jour 1 {#day1}

L&#39;utilisateur XYZ se rend sur le site pour regarder une vidéo.

Événements déclenchés :

* Tentative AuthN (aucun utilisateur unique pour l’instant)
* AuthN accordée
   * à ce stade, nous identifions l’utilisateur de manière unique en fonction de ce que le MVPD renvoie ; le nombre d’utilisateurs uniques par jour est donc augmenté de 1.
   * le jeton AuthN est mis en cache pendant 30 jours.
* Événement de tentative/accordé AuthZ
   * Jeton AuthZ mis en cache pendant 1 jour
* Événement de requête de lecture réussi

#### Jour 1 (plus tard) {#day1-later-on}

L&#39;utilisateur XYZ regarde une autre vidéo.

Événements déclenchés :

* Événement de requête de lecture réussi (les autres sont mis en cache)
* Aucune augmentation des uniques quotidiennes ou mensuelles

#### Jour 3 {#day3}

L&#39;utilisateur XYZ regarde une autre vidéo.

Événements déclenchés :

* Événement de tentative/accordé AuthZ
   * Depuis l’expiration de la mise en cache d’un jour à partir du jour 1
* Événement de requête de lecture réussi (les autres sont mis en cache)
* Nombre d’utilisateurs uniques par jour augmenté de 1 ; les uniques mensuelles restent 1

#### 31 jour {#day31}

L&#39;utilisateur XYZ regarde une autre vidéo.

Identique au jour 1 depuis l’expiration de la mise en cache AuthN.

Si l’autorisation du même utilisateur échouait, le nombre mensuel d’utilisateurs uniques serait toujours augmenté de 1, car deux événements contiennent l’ID utilisateur : l’authentification accordée et la tentative d’autorisation.

### Authentification unique (SSO) {#single-sign-on-sso}

Dans certains cas, le nombre d’utilisateurs uniques peut être supérieur au nombre d’authentifications réussies. C’est généralement le cas lorsque de nombreux utilisateurs se connectent via SSO à partir d’autres sites/applications et qu’ils doivent uniquement obtenir une autorisation sur le site/l’application actif.

### Comparaison des utilisateurs uniques côté client et côté serveur {#comparing-client-side-and-server-side-unique-users}

Si la valeur de l’ID utilisateur de `sendTrackingData()` est utilisé côté client pour comptabiliser les utilisateurs uniques, les numéros côté client et côté serveur doivent correspondre.

Si les différences sont importantes, les raisons suivantes expliquent généralement la différence :

* Valeurs uniques de lecture vidéo par rapport à tous les événements uniques. Comme mentionné, l’authentification Adobe Primetime comptabilise les utilisateurs uniques pour tous les événements, à l’exception des tentatives AuthN. En d’autres termes, si l’utilisateur s’authentifie uniquement (sur la page) mais ne regarde pas de vidéo, une augmentation du nombre d’utilisateurs uniques est toujours déclenchée.

* Comptage des utilisateurs ayant échoué à l’autorisation : l’authentification Adobe Primetime comptabilise ces utilisateurs également dans le nombre indiqué.

<!--
## Related Information {#related-information}

- [Entitlement Service Monitoring API](/help/authentication/entitlement-service-monitoring-api.md)

-->
