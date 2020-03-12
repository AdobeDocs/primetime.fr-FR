---
description: Pour permettre au résolveur d’annonces de fonctionner, les fournisseurs d’annonces, tels qu’Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
seo-description: Pour permettre au résolveur d’annonces de fonctionner, les fournisseurs d’annonces, tels qu’Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
seo-title: Métadonnées d’insertion publicitaire
title: Métadonnées d’insertion publicitaire
uuid: 8848c939-1f12-4145-8025-453b4fe79aae
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Présentation {#ad-insertion-metadata-overview}

Pour permettre au résolveur d’annonces de fonctionner, les fournisseurs d’annonces, tels qu’Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.

Le navigateur TVSDK inclut la bibliothèque Adobe Primetime de prise de décision publicitaire. Pour que votre contenu comprenne des publicités provenant du serveur Adobe Primetime et de prise de décision, votre application doit fournir les informations requises suivantes sur AudidattitudeSettings :

* `mediaID`, qui est un identifiant unique pour la vidéo à lire.

   L’éditeur affecte le mediaID lors de l’envoi du contenu vidéo et des informations publicitaires au serveur Adobe Primetime de prise de décision publicitaire. Cet identifiant est utilisé par la prise de décision publicitaire Adobe Primetime pour récupérer les informations publicitaires associées à la vidéo sur le serveur.

* (Facultatif) `defaultMediaId`, qui spécifie les publicités diffusées lorsque les conditions suivantes sont remplies :

   * Votre requête au serveur d’annonces n’est pas valide ou le contenu est mal configuré.
   * La prise de décision publicitaire d’Adobe Primetime est retardée dans la propagation des données.
   * L’un des processus dorsaux de prise de décision et d’Adobe Primetime fonctionne mal ou n’est pas disponible.
   >[!TIP]
   >
   >Adobe recommande l’utilisation `defaultMediaId`.

* Votre `zoneID`compte, qui est attribué par Adobe, identifie votre ou votre site Web.
* Domaine du serveur d’annonces affecté.
* Autres paramètres de ciblage.

   Vous pouvez inclure ces paramètres en fonction de vos besoins et des besoins du fournisseur d’annonces.