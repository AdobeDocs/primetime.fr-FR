---
description: Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection publicitaire créative sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation de l’URL source pour les créatifs publicitaires.
title: Mise à jour des règles de sélection publicitaire
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Aperçu {#updating-ad-creative-selection-rules}

Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection publicitaire créative sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation de l’URL source pour les créatifs publicitaires.

Lorsque votre lecteur vidéo envoie une requête à un serveur d’annonces, la réponse VAST/VMAP comprend généralement plusieurs éléments créatifs d’annonces ( `MediaFile` éléments), chacun d’eux fournissant une URL vers une version de conteneur-codec différente. Dans certains cas, les créatifs publicitaires dans la réponse VAST/VMAP fournissent chacun un débit différent pour la publicité. Si vous souhaitez définir vos propres règles de priorité et de transformation pour ces créatifs publicitaires, vous pouvez le faire dans le fichier de configuration [!DNL AdobeTVSDKConfig.json].

>[!IMPORTANT]
>
>* Ne modifiez pas le nom du fichier de configuration TVSDK. Le nom doit rester [!DNL AdobeTVSDKConfig.json].
>* Ce fichier doit être hébergé sur votre réseau CDN (Content diffusion Network).

>



Vous pouvez spécifier deux types de règles dans [!DNL AdobeTVSDKConfig.json] : *Règles de priorité* et *Normaliser* règles.
