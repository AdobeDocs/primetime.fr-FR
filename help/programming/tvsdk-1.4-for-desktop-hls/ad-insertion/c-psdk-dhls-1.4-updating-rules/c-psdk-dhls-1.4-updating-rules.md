---
description: Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection créative publicitaire sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation des URL sources pour les créatifs publicitaires.
title: Mise à jour des règles de sélection créative
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Présentation {#updating-ad-creative-selection-rules}

Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection créative publicitaire sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation des URL sources pour les créatifs publicitaires.

Lorsque votre lecteur vidéo envoie une requête à un serveur de publicités, la réponse VAST/VMAP comprend généralement plusieurs créations publicitaires ( `MediaFile` ), chacun fournissant une URL vers une version de conteneur-codec différente. Dans certains cas, les créatifs publicitaires dans la réponse VAST/VMAP fournissent chacun un débit différent pour la publicité. Si vous souhaitez définir vos propres priorités et règles de transformation pour ces créatifs publicitaires, vous pouvez le faire dans la variable [!DNL AdobeTVSDKConfig.json] fichier de configuration.

>[!IMPORTANT]
>
>* Ne modifiez pas le nom du fichier de configuration TVSDK. Le nom doit rester [!DNL AdobeTVSDKConfig.json].
>* Ce fichier doit être hébergé sur votre réseau de diffusion de contenu (CDN).
>

Vous pouvez spécifier deux types de règles dans [!DNL AdobeTVSDKConfig.json]: *Priorité* règles et *Normaliser* règles.
