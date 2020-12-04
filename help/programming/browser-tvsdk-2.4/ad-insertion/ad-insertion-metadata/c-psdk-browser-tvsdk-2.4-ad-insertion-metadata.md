---
description: Pour que le résolveur d’annonces puisse fonctionner, les fournisseurs d’annonces, tels que la prise de décision d’annonces Adobe Primetime, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
seo-description: Pour que le résolveur d’annonces puisse fonctionner, les fournisseurs d’annonces, tels que la prise de décision d’annonces Adobe Primetime, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
seo-title: Métadonnées d’insertion publicitaire
title: Métadonnées d’insertion publicitaire
uuid: 8848c939-1f12-4145-8025-453b4fe79aae
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---


# Aperçu {#ad-insertion-metadata-overview}

Pour que le résolveur d’annonces puisse fonctionner, les fournisseurs d’annonces, tels que la prise de décision d’annonces Adobe Primetime, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.

Le navigateur TVSDK comprend la bibliothèque de prise de décision des publicités Adobe Primetime. Pour que votre contenu comprenne des publicités provenant du serveur de prise de décision publicitaire Adobe Primetime, votre application doit fournir les informations requises suivantes pour les paramètres d’audience :

* `mediaID`, qui est un identifiant unique pour la vidéo à lire.

   L’éditeur affecte l’ID de média lors de l’envoi de contenu vidéo et d’informations publicitaires au serveur de prise de décision publicitaire Adobe Primetime. Cet identifiant est utilisé par Adobe Primetime pour la prise de décision publicitaire afin de récupérer les informations publicitaires associées pour la vidéo sur le serveur.

* (Facultatif) `defaultMediaId`, qui spécifie les publicités diffusées lorsque les conditions suivantes sont remplies :

   * Votre demande au serveur d’annonces n’est pas valide ou le contenu est mal configuré.
   * La prise de décision publicitaire en Adobe Primetime connaît des retards dans la propagation des données.
   * L’un des processus principaux de prise de décision publicitaire Adobe Primetime fonctionne mal ou n’est pas disponible.

   >[!TIP]
   >
   >L&#39;Adobe recommande d&#39;utiliser `defaultMediaId`.

* Votre `zoneID`, qui est attribué par Adobe, identifie votre société ou votre site Web.
* Domaine du serveur d’annonces affecté.
* Autres paramètres de ciblage.

   Vous pouvez inclure ces paramètres en fonction de vos besoins et des besoins du fournisseur d’annonces.