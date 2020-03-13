---
description: Pour permettre au résolveur d’annonces de fonctionner, les fournisseurs d’annonces, tels qu’Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
seo-description: Pour permettre au résolveur d’annonces de fonctionner, les fournisseurs d’annonces, tels qu’Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
seo-title: Métadonnées d’insertion publicitaire
title: Métadonnées d’insertion publicitaire
uuid: f40ed53b-eba1-4f70-a29c-90cac51e8a9a
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# Présentation {#ad-insertion-metadata}

Pour permettre au résolveur d’annonces de fonctionner, les fournisseurs d’annonces, tels qu’Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.

TVSDK inclut la bibliothèque de prise de décision et Primetime. Pour que votre contenu comprenne des publicités provenant du serveur de décision publicitaire Primetime, votre application doit fournir les `AuditudeSettings` informations requises suivantes :

* `mediaID`, qui est un identifiant unique pour la vidéo à lire.

   L’éditeur affecte le `mediaID` paramètre lors de l’envoi de contenu vidéo et d’informations publicitaires au serveur Adobe Primetime de prise de décision publicitaire. Cet identifiant est utilisé par la prise de décision publicitaire Primetime pour récupérer les informations publicitaires associées à la vidéo sur le serveur.

* (Facultatif) `defaultMediaId`, qui spécifie les publicités diffusées lorsque les conditions suivantes sont remplies :

   * Votre requête au serveur d’annonces n’est pas valide ou le contenu est mal configuré.
   * La prise de décision publicitaire Primetime connaît des retards dans la propagation des données.
   * L’un des processus principaux de prise de décision et de Primetime fonctionne mal ou n’est pas disponible.
   >[!TIP]
   >
   >Adobe recommande l’utilisation `defaultMediaId`.

* Votre `zoneID`compte, qui est attribué par Adobe, identifie votre ou votre site Web.
* Domaine du serveur d’annonces affecté.
* Autres paramètres de ciblage.

   Vous pouvez inclure ces paramètres en fonction de vos besoins et des besoins du fournisseur d’annonces.