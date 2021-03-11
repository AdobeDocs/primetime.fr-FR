---
description: Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection publicitaire créative sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation de l’URL source pour les créatifs publicitaires.
keywords: règles de sélection créative ; Adobe TVSDKConfig ; priorités créatives ; règles de transformation
title: Mettre à jour les règles de sélection publicitaire
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# Aperçu {#update-ad-creative-selection-rules-overview}

Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection publicitaire créative sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation de l’URL source pour les créatifs publicitaires.

Lorsque votre lecteur vidéo envoie une requête à un serveur d’annonces, la réponse VAST/VMAP comprend généralement plusieurs éléments créatifs d’annonces ( `MediaFile` éléments), chacun d’eux fournissant une URL vers une version de conteneur-codec différente. Dans certains cas, les créatifs publicitaires dans la réponse VAST/VMAP fournissent chacun un débit différent pour la publicité. Si vous souhaitez définir vos propres règles de priorité et de transformation pour ces créatifs publicitaires, vous pouvez le faire dans le fichier de configuration [!DNL AdobeTVSDKConfig.json].

>[!IMPORTANT]
>
>* Ne modifiez pas le nom du fichier de configuration TVSDK. Le nom doit rester [!DNL AdobeTVSDKConfig.json].
>* Ce fichier doit être placé dans le dossier [!DNL assets/] de votre projet.
>* La modification des pistes audio en cours de lecture de la publicité ne modifie pas la piste audio. Un lecteur ne doit pas permettre aux utilisateurs de modifier la piste audio en cours de lecture d’une publicité.

>



Vous pouvez spécifier deux types de règles dans [!DNL AdobeTVSDKConfig.json] : *Règles de priorité* et *Normaliser* règles.

**[!UICONTROL Ad Rules change]**

<!--<a id="section_EDCE7C94156D4A47AA2FBAE9BE0390CE"></a>-->

Les règles de publicité sont spécifiées à l’aide d’un fichier JSON. Le format du fichier JSON reste identique dans les deux versions de TVSDK. Toutefois, dans TVSDK v3.0, le fichier JSON des règles publicitaires doit être hébergé sur un emplacement accessible via une URL HTTP. L’application peut utiliser une instance d’AuditudeSettings :

```
//TVSDK v3.0 AuditudeSettings result = new AuditudeSettings(); 
result.setCRSRulesJsonURL(<http url of 
AdobeTVSDKConfig.json>);  
```
