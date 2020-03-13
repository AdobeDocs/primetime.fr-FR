---
title: Notes de mise à jour de DRM 5.3.1
seo-title: Notes de mise à jour de DRM 5.3.1
description: Les notes de mise à jour de DRM 5.3.1 décrivent les nouvelles fonctionnalités et les problèmes connus de DRM 5.3.1.
seo-description: Les notes de mise à jour de DRM 5.3.1 décrivent les nouvelles fonctionnalités et les problèmes connus de DRM 5.3.1.
uuid: bb61b79f-a5b3-42ed-8016-495b1ac99ea6
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Notes de mise à jour de DRM 5.3.1 {#drm-release-notes}

Les notes de mise à jour de DRM 5.3.1 décrivent les nouvelles fonctionnalités et les problèmes connus de DRM 5.3.1.

## Nouvelles fonctionnalités de la version 5.3 {#new-features}

* **Arrêt sécurisé -** Vous pouvez spécifier si la lecture s’arrête ou continue à la fin d’une fenêtre de lecture.
* **RBOP (Resolution Based Output Protection) : vous pouvez** spécifier les contraintes de sortie en fonction des résolutions de pixels.
* **Gestion du MDP -** Afin de prendre en charge le langage HTML5, Adobe a mis à jour le serveur de licences d’implémentation des références inclus dans le SDK Java DRM d’Adobe Primetime (anciennement Adobe Access DRM) afin de pouvoir consommer tous les messages de protocole DRM à un seul point de terminaison d’URL. Cette consolidation des méthodes d’URL HTTP est nécessaire pour se conformer à la spécification HTML5 EME (Encrypted Media Extension) qui doit être mise en oeuvre par les fournisseurs DRM du MDP (Content Decryption Module). Auparavant, il s’agissait des seuls points de fin d’URL exposés par le serveur de licences d’implémentation de référence :

   * /flashaccess/i15n/v3 (Individualisation)
   * /flashaccess/license/v5 (Demande de licence)
   * /flashaccess/licenseRet/v5 (Retour de licence)
   * /flashaccess/getServerVersion/v5 (Obtenir la version du serveur)

Désormais, toutes les demandes (provenant d’un MDP HTML5) peuvent être dirigées vers un seul point de terminaison : /req

Cette modification est rétrocompatible avec les plates-formes non MDP, telles que Flash Player, Android et iOS.

* **Réduction de la mise à l’échelle RBOP -** Spécifique à l’espace HTML5, RBOP contient une fonctionnalité de réduction automatique de la mise à l’échelle. Si un débit supérieur au débit autorisé spécifié dans la stratégie DRM, le contenu sera réduit à la résolution maximale autorisée. Si, par exemple, un flux 1080p est diffusé en continu sur un client qui affiche le contenu sur un moniteur non compatible HDCP, la stratégie DRM peut indiquer que la résolution maximale doit être de 720p. Primetime DRM décodera le flux 1080p, puis le réduira à 720p avant de le rendre à l’écran. Si le navigateur qui lit la vidéo est alors déplacé vers un moniteur qui ne prend pas en charge HDCP, Primetime DRM arrête alors de réduire la taille du contenu et lui permet de lire le contenu à 1080.

## Problèmes connus dans la version 5.3 {#known-issues}

* `Hasher.bat (flashaccess-hasher.jar)` envoie des messages du journal à `flashaccess-global.log.`Vous devez vous assurer que le `flashaccess-global.log` fichier se trouve dans le même répertoire que Hasher.bat.

* La sortie de certains des `toJSON()`appels retournent `Strings` qui ne sont pas entièrement conformes à JSON ou complètement conformes de manière autonome (c.-à-d. sans la composition des structures JSON).

* Le serveur de clés Xbox accepte les demandes de clés dont la valeur de version n’est pas égale à 1.

Le serveur de clé Xbox ne doit prendre en charge que les requêtes de clé dont la version est égale à 1, mais il accepte actuellement les requêtes de clé lorsque la version n&#39;est pas 1.

* Le serveur de clé Xbox ne valide pas correctement une stratégie.

Le serveur de clé Xbox ne doit pas accepter les stratégies qui ne sont pas à la date de validité, mais le serveur les accepte actuellement.

* Le serveur de clé Xbox doit rejeter une requête de clé qui contient des métadonnées créées avec un certificat de packager incorrect.
* La valeur renvoyée de certaines structures JSON n’est pas correctement formatée pour les classes liées à la protection de sortie basée sur la résolution.

Plusieurs classes implémentent une méthode toJSON() qui doit renvoyer une représentation JSON de cet objet en tant que chaîne, mais actuellement la valeur renvoyée n’est pas entièrement compatible JSON.

## Ressources utiles {#helpful-resources}

* Reportez-vous à la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.
