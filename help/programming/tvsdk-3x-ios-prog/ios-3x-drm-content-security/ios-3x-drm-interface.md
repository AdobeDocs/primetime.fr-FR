---
description: Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour fournir un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces comme alternative à la solution DRM intégrée de Primetime d’Adobe.
keywords: DRM;DASH;HLS
title: Présentation de l’interface DRM Primetime
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Présentation de l’interface DRM Primetime {#primetime-drm-interface-overview}

Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour fournir un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces comme alternative à la solution DRM intégrée de Primetime d’Adobe.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Consultez le représentant de votre Adobe pour obtenir les informations les plus récentes sur la disponibilité de solutions DRM tierces.

Le DRM est l’élément clé du système de gestion des droits numériques (DRM) de Primetime côté client.

Primetime DRM fournit un workflow évolutif et efficace pour mettre en oeuvre la protection du contenu dans les applications TVSDK. Vous protégez et gérez les droits sur votre contenu vidéo en créant une licence pour chaque fichier multimédia numérique.

TVSDK prend en charge l’intégration DRM Primetime en tant que processus DRM personnalisés. Cela signifie que votre application doit mettre en oeuvre les processus d’authentification DRM avant de lire le flux à l’aide du Flash DRMManager. Pour l’activer, le lecteur multimédia vous fournit le gestionnaire DRM pour l’authentification.

Reportez-vous à l’exemple de code du lecteur DRM inclus dans le package TVSDK.

Voici les éléments d’API les plus importants pour travailler avec DRM :

* Référence dans le lecteur multimédia à l’objet du gestionnaire DRM qui implémente le sous-système DRM :

  ```
  @property (readonly, nonatomic) DRMManager *drmManager
  ```

<!--<a id="section_F986DB1EDD6F44CD8E57419CCA0921E8"></a>-->

TVSDK émet un `PTMediaPlayerItemDRMMetadataChanged` lorsque les métadonnées DRM changent. Ces métadonnées sont utilisées comme entrée pour presque toutes les fonctions de la fonction `DRMManager` classe .

<!--<a id="section_223DCF63BAB6438792A85352A79044CC"></a>-->

Si le flux protégé par DRM est encodé à plusieurs débits (MBR), les métadonnées DRM utilisées pour la liste de lecture de la variante doivent être identiques aux métadonnées utilisées dans tous les flux de débit binaire.

>[!TIP]
>
>Lors du référencement des URL de ressources protégées par DRM dans votre application iOS, le paramètre de chaîne de requête `?faxs=1` doit être ajouté à l’URL de niveau fixe M3U8 (MBR). Par exemple :

```
https://your.domain.com/hls/[...]/index.m3u8?faxs=1
```

La variable `faxs=1` le paramètre de chaîne de requête signale que le contenu est protégé par DRM et déclenche le processus de décryptage DRM en conséquence dans le TVSDK iOS. Vous pouvez également ajouter la variable `faxs=1` balise sur les URL de ressources HLS protégées par DRM qui sont destinées à d’autres plateformes ; elles sont observées selon les besoins sur iOS ou traitées comme non-op dans les lecteurs sur d’autres plateformes.

## Mise en oeuvre de Primetime DRM dans une application TSVDK {#implement-primetime-drm-in-a-tsvdk-application}

Primetime DRM est intégré à TVSDK, ce qui simplifie la mise en oeuvre de la protection de contenu dans une application TVSDK.

Pour obtenir un aperçu et des détails sur l’utilisation de Primetime DRM pour mettre en oeuvre la protection de contenu dans une application TVSDK, voir :

* [Workflow Adobe Primetime TVSDK-DRM (PDF)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_tvsdk_drm_workflow.pdf)
