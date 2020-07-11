---
seo-title: Application SWF permettant la mise en vente
title: Application SWF permettant la mise en vente
uuid: e3021ae9-54f4-4bcf-a274-515ae765f74b
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Application SWF permettant la mise en vente {#swf-application-allowlisting}

Pour liste autorisée d’une application SWF, vous pouvez suivre l’une des deux stratégies suivantes :

* Vous pouvez spécifier une URL pour un fichier SWF. Il s&#39;agit d&#39;une approche très flexible, particulièrement dans un environnement de développement dans lequel vous reconstruisez régulièrement votre fonds de développement.
* Vous pouvez spécifier un HASH SWF. Il s’agit de la valeur digest cryptographique de votre fichier SWF. Cette approche est moins flexible (mais beaucoup plus stricte), puisque le SWF HASH changera lorsque l&#39;application sera modifiée et reconstruite. Dans ce cas, tout le contenu lié au HASH précédent ne pourra pas jouer sur le nouveau lecteur et devra être reconditionné. L&#39; [!DNL PolicyManager.jar] outil calcule automatiquement le hachage si vous spécifiez un [!DNL .swf] fichier.

   D’autre part, si vous utilisez Primetime DRM via Flash/Adobe Media Server (FMS/AMS), vous pouvez indiquer le chemin d’accès à vos fichiers SWF particuliers et FMS/AMS hachera automatiquement les fichiers SWF que vous pouvez insérer dans la stratégie DRM utilisée pour regrouper le contenu diffusé par FMS/AMS.

Voir `policy.allowedSWFApplication.n` dans Propriétés *de* configuration pour plus d’informations.
