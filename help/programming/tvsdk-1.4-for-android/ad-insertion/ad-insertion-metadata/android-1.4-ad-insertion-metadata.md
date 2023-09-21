---
description: Pour que le résolveur de publicités fonctionne, les fournisseurs de publicités, comme Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.
title: Métadonnées d’insertion publicitaire
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Présentation {#ad-insertion-metadata}

Pour que le résolveur de publicités fonctionne, les fournisseurs de publicités, comme Adobe Primetime et la prise de décision, ont besoin de valeurs de configuration pour activer votre connexion au fournisseur.

TVSDK comprend la bibliothèque de prise de décision publicitaire Primetime. Pour que votre contenu inclue de la publicité provenant du serveur de prise de décision publicitaire Primetime, votre application doit fournir les éléments suivants : `AuditudeSettings` information :

* `mediaID`, qui est un identifiant unique de la vidéo à lire.

  L’éditeur affecte à la variable `mediaID` lors de l’envoi de contenu vidéo et d’informations publicitaires au serveur de prise de décision publicitaire Adobe Primetime. Cet identifiant est utilisé par Primetime ad Decisioning pour récupérer les informations publicitaires associées pour la vidéo du serveur.

* (Facultatif) `defaultMediaId`, qui spécifie les publicités diffusées lorsque les conditions suivantes sont remplies :

   * Votre demande au serveur d’annonces n’est pas valide ou le contenu n’est pas correctement configuré.
   * La prise de décision concernant les publicités Primetime entraîne des retards dans la propagation des données.
   * L’un des processus principaux de prise de décision et de Primetime ne fonctionne pas ou n’est pas disponible.

  >[!TIP]
  >
  >Adobe recommande d’utiliser `defaultMediaId`.

* Votre `zoneID`, qui est attribué par Adobe, identifie votre société ou votre site web.
* Domaine du serveur de publicités affecté.
* Autres paramètres de ciblage.

  Vous pouvez inclure ces paramètres en fonction de vos besoins et des besoins du fournisseur d’annonces publicitaires.
