---
description: Pour permettre au résolveur d’annonces de fonctionner, les fournisseurs d’annonces, tels qu’Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
seo-description: Pour permettre au résolveur d’annonces de fonctionner, les fournisseurs d’annonces, tels qu’Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
seo-title: Métadonnées d’insertion publicitaire
title: Métadonnées d’insertion publicitaire
uuid: ee4dd8b8-4c41-4f01-be50-60f4c7dc962d
translation-type: tm+mt
source-git-commit: 0eaf0e7e7e61d596a51d1c9c837ad072d703c6a7

---


# Présentation {#ad-insertion-metadata-overview}

Pour permettre au résolveur d’annonces de fonctionner, les fournisseurs d’annonces, tels qu’Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.

TVSDK inclut la bibliothèque de décisions et de décisions Primetime. Pour que votre contenu comprenne des publicités provenant du serveur Primetime et de prise de décision, votre application doit fournir les `AuditudeSettings` informations requises suivantes :

* `mediaID`, qui est un identifiant unique pour la vidéo à lire.

   L’éditeur affecte le mediaID lors de l’envoi du contenu vidéo et des informations publicitaires au serveur Adobe Primetime de prise de décision publicitaire. Cet identifiant est utilisé par Primetime pour la prise de décision publicitaire afin de récupérer les informations publicitaires associées à la vidéo sur le serveur.

* (Facultatif) `defaultMediaId`, qui spécifie les publicités diffusées lorsque les conditions suivantes sont remplies :

   * Votre requête au serveur d’annonces n’est pas valide ou le contenu est mal configuré.
   * La prise de décision publicitaire Primetime entraîne des retards dans la propagation des données.
   * L’un des processus principaux de prise de décision et de Primetime fonctionne mal ou n’est pas disponible.
   >[!TIP]
   >
   >Adobe recommande l’utilisation `defaultMediaId`.

* Votre `zoneID`compte, qui est attribué par Adobe, identifie votre ou votre site Web.
* Domaine du serveur d’annonces affecté.
* Autres paramètres de ciblage.

   Vous pouvez inclure ces paramètres en fonction de vos besoins et des besoins du fournisseur d’annonces.