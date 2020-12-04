---
description: Pour que le résolveur d’annonces puisse fonctionner, les fournisseurs d’annonces, tels que la prise de décision d’annonces Adobe Primetime, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
seo-description: Pour que le résolveur d’annonces puisse fonctionner, les fournisseurs d’annonces, tels que la prise de décision d’annonces Adobe Primetime, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
seo-title: Métadonnées d’insertion publicitaire
title: Métadonnées d’insertion publicitaire
uuid: f40ed53b-eba1-4f70-a29c-90cac51e8a9a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# Aperçu {#ad-insertion-metadata}

Pour que le résolveur d’annonces puisse fonctionner, les fournisseurs d’annonces, tels que la prise de décision d’annonces Adobe Primetime, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.

TVSDK comprend la bibliothèque de prise de décision publicitaire Primetime. Pour que votre contenu comprenne des publicités provenant du serveur de prise de décision publicitaire Primetime, votre application doit fournir les `AuditudeSettings` informations &lt;a0/> requises suivantes :

* `mediaID`, qui est un identifiant unique pour la vidéo à lire.

   L’éditeur attribue le `mediaID` lors de l’envoi du contenu vidéo et des informations publicitaires au serveur de prise de décision publicitaire Adobe Primetime. Cet identifiant est utilisé par la prise de décision publicitaire Primetime pour récupérer les informations publicitaires associées à la vidéo sur le serveur.

* (Facultatif) `defaultMediaId`, qui spécifie les publicités diffusées lorsque les conditions suivantes sont remplies :

   * Votre demande au serveur d’annonces n’est pas valide ou le contenu est mal configuré.
   * La prise de décision publicitaire Primetime connaît des retards dans la propagation des données.
   * L’un des processus principaux de prise de décision et de Primetime fonctionne mal ou n’est pas disponible.

   >[!TIP]
   >
   >L&#39;Adobe recommande d&#39;utiliser `defaultMediaId`.

* Votre `zoneID`, qui est attribué par Adobe, identifie votre société ou votre site Web.
* Domaine du serveur d’annonces affecté.
* Autres paramètres de ciblage.

   Vous pouvez inclure ces paramètres en fonction de vos besoins et des besoins du fournisseur d’annonces.