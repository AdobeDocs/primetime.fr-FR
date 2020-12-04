---
title: Notes de mise à jour de DRM 5.3.1
seo-title: Notes de mise à jour de DRM 5.3.1
description: Les Notes de mise à jour de DRM 5.3.1 décrivent les nouvelles fonctionnalités et les problèmes connus de DRM 5.3.1.
seo-description: Les Notes de mise à jour de DRM 5.3.1 décrivent les nouvelles fonctionnalités et les problèmes connus de DRM 5.3.1.
uuid: bb61b79f-a5b3-42ed-8016-495b1ac99ea6
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---


# Notes de mise à jour de DRM 5.3.1 {#drm-release-notes}

Les Notes de mise à jour de DRM 5.3.1 décrivent les nouvelles fonctionnalités et les problèmes connus de DRM 5.3.1.

## Nouvelles fonctionnalités de la version 5.3 {#new-features}

* **Arrêt sécurisé :** vous pouvez indiquer si la lecture s’arrête ou continue à la fin d’une fenêtre de lecture.
* **RBOP (Resolution Based Output Protection) :** vous pouvez spécifier les contraintes de sortie en fonction des résolutions de pixels.
* **Mise en oeuvre du MDP -** Afin de prendre en charge le format HTML5, l’Adobe a mis à jour le serveur de licences de mise en oeuvre de référence inclus dans le SDK Java DRM Adobe Primetime DRM (anciennement Adobe Access DRM) afin de pouvoir consommer tous les messages de protocole DRM à un seul point de terminaison d’URL. Cette consolidation des méthodes d’URL HTTP est nécessaire pour se conformer à la spécification HTML5 EME (Encrypted Media Extension) qui doit à son tour être mise en oeuvre par les fournisseurs DRM du MDP (Content Decryption Module). Auparavant, il s’agissait des seuls points de terminaison d’URL exposés par le serveur de licences d’implémentation de référence :

   * /flashaccess/i15n/v3 (Individualisation)
   * /flashaccess/license/v5 (Demande de licence)
   * /flashaccess/licenseRet/v5 (retour de licence)
   * /flashaccess/getServerVersion/v5 (Get Server Version)

Désormais, toutes les requêtes (provenant d’un MDP HTML5) peuvent être dirigées vers un seul point de terminaison : /req

Cette modification est rétrocompatible avec les plates-formes non MDP, telles que Flash Player, Android, iOS.

* **Réduction de la mise à l’échelle RBOP -** Spécifique à l’espace HTML5, RBOP contient une fonctionnalité de réduction automatique de la mise à l’échelle. Si un débit supérieur au débit autorisé spécifié dans la stratégie DRM, le contenu est réduit à la résolution maximale autorisée. Par exemple, si un flux 1080p est diffusé en continu sur un client qui affiche le contenu sur un moniteur non compatible HDCP, la stratégie DRM peut indiquer que la résolution maximale doit être de 720p. Primetime DRM décodera le flux 1080p, puis le réduira à 720p avant de le rendre à l&#39;écran. Si le navigateur qui lit la vidéo est alors déplacé vers un moniteur qui prend en charge HDCP, Primetime DRM arrête alors de réduire la mise à l&#39;échelle du contenu et lui permet de lire à 1080.

## Problèmes connus dans la version 5.3 {#known-issues}

* `Hasher.bat (flashaccess-hasher.jar)` envoie les messages du journal à  `flashaccess-global.log.`Vous devez vous assurer que le  `flashaccess-global.log` fichier se trouve dans le même répertoire que Hasher.bat.

* La sortie de certains appels `toJSON()`renvoie `Strings` qui ne sont pas entièrement conformes à JSON ou entièrement conformes de manière autonome (c&#39;est-à-dire sans composition de structures JSON).

* Le serveur de clés Xbox accepte les demandes de clés dont la valeur de version n&#39;est pas égale à 1.

Le serveur de clés Xbox ne doit prendre en charge que les requêtes clés dont la version est égale à 1, mais, pour l&#39;instant, le serveur accepte les requêtes clés lorsque la version n&#39;est pas 1.

* Le serveur de clé Xbox ne valide pas correctement une stratégie.

Le serveur de clés Xbox ne doit pas accepter les stratégies qui ne sont pas en dehors de la date de validité, mais le serveur les accepte actuellement indépendamment.

* Le serveur de clé Xbox doit rejeter une requête de clé qui contient des métadonnées créées avec un certificat de packager incorrect.
* La valeur renvoyée de certaines structures JSON n’est pas correctement formatée pour les classes liées à la protection de sortie basée sur la résolution.

Plusieurs classes implémentent une méthode toJSON() qui doit renvoyer une représentation JSON conforme de cet objet en tant que chaîne, mais actuellement la valeur renvoyée n’est pas entièrement compatible JSON.

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à la [page Apprentissage et support Adobe Primetime](https://helpx.adobe.com/support/primetime.html).
