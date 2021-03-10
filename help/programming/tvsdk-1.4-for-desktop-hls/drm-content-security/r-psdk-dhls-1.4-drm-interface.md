---
description: L’élément clé côté client du système de gestion des droits numériques (DRM) de Primetime est le Gestionnaire de DRM.
title: Présentation de l’interface DRM de Primetime
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Présentation de l’interface DRM Primetime{#primetime-drm-interface-overview}

L’élément clé côté client du système de gestion des droits numériques (DRM) de Primetime est le Gestionnaire de DRM.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM offre un flux de travail évolutif et efficace pour mettre en oeuvre la protection du contenu dans les applications TVSDK. Vous protégez et gérez les droits sur votre contenu vidéo en créant une licence pour chaque fichier multimédia numérique.

TVSDK prend en charge l’intégration DRM Primetime en tant que workflows DRM personnalisés. Cela signifie que votre application doit implémenter les workflows d’authentification DRM avant de lire le flux en utilisant le Flash `DRMManager`. Pour activer cette fonction, le `MediaPlayer` fournit le gestionnaire DRM pour l&#39;authentification.

Il s’agit des éléments d’API les plus importants pour travailler avec DRM :

* Référence dans le lecteur multimédia à l’objet du gestionnaire DRM qui implémente le sous-système DRM :

   ```
   public function get drmManager():DRMManager 
   ```

<!--<a id="section_4204CE2731A44F67A3664AEDE8CCCA47"></a>-->

Autres éléments d’API pertinents :

* [flash.net.drm.DRMManager](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMManager.html)
* [flash.net.drm.DRMContentData](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMContentData.html)
* [flash.net.drm.DRMVoucher](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/DRMVoucher.html)
* [flash.net.drm.AuthenticationMethod](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/net/drm/AuthenticationMethod.html)
* [flash.événements.DRMStatusEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DRMStatusEvent.html)
* [flash.événements.DRMErrorEvent](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/events/DRMErrorEvent.html)

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

Pour plus d’informations sur DRM, consultez la documentation Adobe Primetime DRM.
