---
title: Listes autorisées des applications SWF
description: Listes autorisées des applications SWF
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Listes autorisées des applications SWF {#swf-application-allowlisting}

Pour mettre en liste autorisée une application de SWF, vous pouvez suivre l’une des deux stratégies suivantes :

* Vous pouvez spécifier une URL pour un SWF. Il s’agit d’une approche très flexible, en particulier dans un environnement de développement dans lequel vous reconstruisez régulièrement votre SWF.
* Vous pouvez spécifier un HACHAGE SWF. Il s’agit d’une valeur de condensé cryptographique de votre SWF. Cette approche est moins flexible (mais beaucoup plus stricte), puisque le SWF HASH change lorsque l’application change et est recréée. Dans ce cas, tout le contenu lié au HASH précédent ne sera pas lu sur le nouveau lecteur et devra être recompilé. La variable [!DNL PolicyManager.jar] calcule automatiquement le hachage si vous spécifiez une [!DNL .swf] fichier .

  D’un autre côté, si vous utilisez Primetime DRM via Flash/Adobe Media Server (FMS/AMS), vous pouvez indiquer le chemin d’accès à votre ou vos SWF, et FMS/AMS hachera automatiquement les SWF pour que vous puissiez les insérer dans la stratégie DRM utilisée pour regrouper le contenu diffusé par FMS/AMS.

Voir `policy.allowedSWFApplication.n` in *Propriétés de configuration* pour plus d’informations.
