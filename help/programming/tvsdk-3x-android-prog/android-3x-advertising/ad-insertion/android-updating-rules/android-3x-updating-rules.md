---
description: Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection créative publicitaire sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation des URL sources pour les créatifs publicitaires.
keywords: règles de sélection créative;AdobeTVSDKConfig;priorités créatives;règles de transformation
title: Mise à jour des règles de sélection créative
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Présentation {#update-ad-creative-selection-rules-overview}

Vous pouvez utiliser le fichier de configuration TVSDK (AdobeTVSDKConfig.json) pour mettre à jour les priorités de la sélection créative publicitaire sur les réponses VAST/VMAP. Vous pouvez également utiliser ce fichier de configuration pour définir les règles de transformation des URL sources pour les créatifs publicitaires.

Lorsque votre lecteur vidéo envoie une requête à un serveur de publicités, la réponse VAST/VMAP comprend généralement plusieurs créations publicitaires ( `MediaFile` ), chacun fournissant une URL vers une version de conteneur-codec différente. Dans certains cas, les créatifs publicitaires dans la réponse VAST/VMAP fournissent chacun un débit différent pour la publicité. Si vous souhaitez définir vos propres priorités et règles de transformation pour ces créatifs publicitaires, vous pouvez le faire dans la variable [!DNL AdobeTVSDKConfig.json] fichier de configuration.

>[!IMPORTANT]
>
>* Ne modifiez pas le nom du fichier de configuration TVSDK. Le nom doit rester [!DNL AdobeTVSDKConfig.json].
>* Ce fichier doit être placé dans la variable [!DNL assets/] du projet.
>* La modification du suivi audio en cours de lecture de la publicité ne modifie pas la piste audio. Un lecteur ne doit pas autoriser les utilisateurs à modifier la piste audio lorsqu’une publicité est en cours de lecture.
>

Vous pouvez spécifier deux types de règles dans [!DNL AdobeTVSDKConfig.json]: *Priorité* règles et *Normaliser* règles.

**[!UICONTROL Ad Rules change]**

<!--<a id="section_EDCE7C94156D4A47AA2FBAE9BE0390CE"></a>-->

Les règles publicitaires sont spécifiées à l’aide d’un fichier JSON. Le format du fichier JSON reste le même dans les deux versions de TVSDK. Toutefois, dans TVSDK v3.0, le fichier JSON des règles publicitaires doit être hébergé sur un emplacement accessible via une URL HTTP. L’application peut utiliser une instance de AuditudeSettings :

```
//TVSDK v3.0 AuditudeSettings result = new AuditudeSettings(); 
result.setCRSRulesJsonURL(<http url of 
AdobeTVSDKConfig.json>);  
```
