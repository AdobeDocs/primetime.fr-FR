---
title: Notes de mise à jour de DRM 5.3.1
description: Les notes de mise à jour de DRM 5.3.1 décrivent les nouvelles fonctionnalités et les problèmes connus de DRM 5.3.1.
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 0%

---

# Notes de mise à jour de DRM 5.3.1 {#drm-release-notes}

Les notes de mise à jour de DRM 5.3.1 décrivent les nouvelles fonctionnalités et les problèmes connus de DRM 5.3.1.

## Nouvelles fonctionnalités de la version 5.3 {#new-features}

* **Secure Stop -** Vous pouvez indiquer si la lecture s’arrête ou se poursuit à la fin d’une fenêtre de lecture.
* **Résolution basée sur la protection de sortie (RBOP) -** Vous pouvez spécifier les contraintes de sortie en fonction de la résolution des pixels.
* **Point de contrôle du MDP -** Pour prendre en charge HTML5, Adobe a mis à jour le serveur de licence de mise en oeuvre de référence inclus dans le SDK Java Adobe Primetime DRM (anciennement Adobe Access DRM) afin de pouvoir consommer tous les messages de protocole DRM à un seul point de terminaison URL. Cette consolidation des méthodes d’URL HTTP est nécessaire pour se conformer à la spécification EME HTML5 (Encrypted Media Extension) qui doit à son tour être mise en oeuvre par les fournisseurs DRM du MDP (Content Decryption Module). Auparavant, il s’agissait des seuls points de terminaison d’URL exposés par le serveur de licence de mise en oeuvre de référence :

   * /flashaccess/i15n/v3 (Individualisation)
   * /flashaccess/license/v5 (demande de licence)
   * /flashaccess/licenseRet/v5 (retour de licence)
   * /flashaccess/getServerVersion/v5 (Obtenir la version du serveur)

Désormais, toutes les demandes (provenant d’un MDP HTML5) peuvent être dirigées vers un point de terminaison unique : /req

Cette modification est rétrocompatible avec les plateformes non MDP, telles que Flash Player, Android, iOS.

* **Réduction de la ligne de commande -** Spécifique à l’espace HTML5, la RBOP contient une fonctionnalité de réduction automatique. Si un débit qui dépasse le débit autorisé spécifié dans la stratégie DRM, le contenu est réduit à la résolution maximale autorisée. Par exemple, si un flux 1 080p est diffusé en continu à un client qui affiche le contenu sur un moniteur non conforme au HDCP, la stratégie DRM peut indiquer que la résolution maximale doit être de 720p. Primetime DRM décodera le flux 1080p, puis le réduira à 720p avant de le rendre à l’écran. Si le navigateur qui lit la vidéo est ensuite déplacé vers un moniteur qui prend en charge HDCP, Primetime DRM arrête de réduire le contenu et lui permet de le lire à 1080.

## Problèmes connus dans la version 5.3 {#known-issues}

* `Hasher.bat (flashaccess-hasher.jar)` génère les messages du journal vers `flashaccess-global.log.`Vous devez vous assurer que la variable `flashaccess-global.log` se trouve dans le même répertoire que Hasher.bat.

* La sortie de certains des `toJSON()`retour des appels `Strings` qui ne sont pas entièrement conformes à JSON ou entièrement conformes de manière autonome (c’est-à-dire sans composition de structures JSON).

* Le serveur de clé Xbox accepte les demandes clés dont la valeur de version est différente de 1.

Le serveur de clé Xbox ne doit prendre en charge que les demandes clés dont la version est égale à 1, mais actuellement, le serveur accepte les demandes clés pour lesquelles la version n’est pas 1.

* Le serveur Xbox key ne valide pas correctement une stratégie.

Le serveur de clé Xbox ne doit pas accepter de stratégies qui ne sont pas à la date de validité, mais le serveur les accepte actuellement, indépendamment de cela.

* Le serveur Xbox key doit rejeter une requête de clé contenant une métadonnée qui a été créée avec un certificat de package incorrect.
* La valeur renvoyée de certaines structures JSON n’est pas correctement formatée pour les classes liées à la protection de sortie basée sur la résolution.

Plusieurs classes implémentent une méthode toJSON() qui doit renvoyer une représentation compatible JSON de cet objet en tant que chaîne, mais la valeur actuellement renvoyée n’est pas entièrement compatible avec JSON.

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://helpx.adobe.com/support/primetime.html) page.
