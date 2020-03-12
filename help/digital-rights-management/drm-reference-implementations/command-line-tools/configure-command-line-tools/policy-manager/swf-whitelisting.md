---
seo-title: Liste blanche des applications SWF
title: Liste blanche des applications SWF
uuid: e3021ae9-54f4-4bcf-a274-515ae765f74b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Liste blanche des applications SWF{#swf-application-whitelisting}

Pour mettre en liste blanche une application SWF, vous pouvez suivre l’une des deux stratégies suivantes :

* Vous pouvez spécifier une URL vers un fichier SWF. Il s’agit d’une approche très flexible, particulièrement dans un  de développement  dans lequel vous reconstruisez régulièrement votre SWF.
* Vous pouvez spécifier un HASH SWF. Il s’agit d’une valeur digest cryptographique de votre fichier SWF. Cette approche est moins flexible (mais beaucoup plus stricte), puisque le SWF HASH changera lorsque l’application sera modifiée et reconstruite. Dans ce cas, tout le contenu lié au HASH précédent ne pourra pas jouer sur le nouveau lecteur et devra être reconditionné. L’ [!DNL PolicyManager.jar] outil calculera automatiquement le hachage si vous spécifiez un [!DNL .swf] fichier.

   D’un autre côté, si vous utilisez Primetime DRM via Flash/Adobe Media Server (FMS/AMS), vous pouvez indiquer le chemin d’accès à votre(s) fichier(s) SWF particulier(s), et FMS/AMS hachera automatiquement les fichiers SWF à insérer dans la stratégie DRM utilisée pour compresser le contenu diffusé par FMS/AMS.

Voir `policy.allowedSWFApplication.n` Propriétés *de* configuration pour plus d’informations.
