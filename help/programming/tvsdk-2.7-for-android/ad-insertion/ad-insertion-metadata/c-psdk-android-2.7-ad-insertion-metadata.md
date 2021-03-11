---
description: Pour que le résolveur d’annonces puisse fonctionner, les fournisseurs d’annonces, tels que la prise de décision d’annonces Adobe Primetime, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
title: Métadonnées d’insertion publicitaire
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---


# Aperçu {#ad-insertion-metadata-overview}

Pour que le résolveur d’annonces puisse fonctionner, les fournisseurs d’annonces, tels que la prise de décision d’annonces Adobe Primetime, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.

TVSDK inclut la bibliothèque de prise de décision et Primetime. Pour que votre contenu comprenne des publicités provenant du serveur de prise de décision et Primetime, votre application doit fournir les `AuditudeSettings` informations  requises suivantes :

* `mediaID`, qui est un identifiant unique pour la vidéo à lire.

   L’éditeur affecte l’ID de média lors de l’envoi de contenu vidéo et d’informations publicitaires au serveur de prise de décision publicitaire Adobe Primetime. Cet identifiant est utilisé par Primetime pour la prise de décision publicitaire afin de récupérer les informations publicitaires associées pour la vidéo sur le serveur.

* (Facultatif) `defaultMediaId`, qui spécifie les publicités diffusées lorsque les conditions suivantes sont remplies :

   * Votre demande au serveur d’annonces n’est pas valide ou le contenu est mal configuré.
   * La prise de décision publicitaire Primetime entraîne des retards dans la propagation des données.
   * L’un des processus principaux de prise de décision et de Primetime fonctionne mal ou n’est pas disponible.

   >[!TIP]
   >
   >L&#39;Adobe recommande d&#39;utiliser `defaultMediaId`.

* Votre `zoneID`, qui est attribué par Adobe, identifie votre société ou votre site Web.
* Domaine du serveur d’annonces affecté.
* Autres paramètres de ciblage.

   Vous pouvez inclure ces paramètres en fonction de vos besoins et des besoins du fournisseur d’annonces.