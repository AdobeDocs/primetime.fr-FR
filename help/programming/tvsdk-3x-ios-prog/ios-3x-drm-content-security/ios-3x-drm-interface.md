---
description: Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour fournir un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces en remplacement de la solution DRM intégrée d’Adobe Primetime.
keywords: DRM;DASH;HLS
seo-description: Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour fournir un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces en remplacement de la solution DRM intégrée d’Adobe Primetime.
seo-title: Présentation de l’interface DRM de Primetime
title: Présentation de l’interface DRM de Primetime
uuid: 5e794147-cc58-448c-b8ec-065e80ef01fd
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Présentation de l’interface DRM de Primetime {#primetime-drm-interface-overview}

Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour fournir un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces en remplacement de la solution DRM intégrée d’Adobe Primetime.

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Consultez votre représentant Adobe pour obtenir les informations les plus récentes sur la disponibilité de solutions DRM tierces.

L’élément clé côté client du système de gestion des droits numériques (DRM) de Primetime est le Gestionnaire de DRM.

Primetime DRM offre un flux de travail évolutif et efficace pour mettre en oeuvre la protection du contenu dans les applications TVSDK. Vous protégez et gérez les droits sur votre contenu vidéo en créant une licence pour chaque fichier multimédia numérique.

TVSDK prend en charge l’intégration DRM Primetime en tant que workflows DRM personnalisés. Cela signifie que votre application doit mettre en oeuvre les workflows d’authentification DRM avant de lire le flux en utilisant Flash DRMManager. Pour activer cette fonction, MediaPlayer vous fournit le gestionnaire DRM pour l’authentification.

Reportez-vous à l’exemple de code du lecteur DRM inclus dans le package TVSDK.

Il s’agit des éléments d’API les plus importants pour travailler avec DRM :

* Référence dans le lecteur multimédia à l’objet du gestionnaire DRM qui implémente le sous-système DRM :

   ```
   @property (readonly, nonatomic) DRMManager *drmManager
   ```

<!--<a id="section_F986DB1EDD6F44CD8E57419CCA0921E8"></a>-->

TVSDK émet une `PTMediaPlayerItemDRMMetadataChanged` notification lorsque les métadonnées DRM changent. Ces métadonnées sont utilisées comme entrée pour presque toutes les fonctions de la `DRMManager` classe.

<!--<a id="section_223DCF63BAB6438792A85352A79044CC"></a>-->

Si le flux protégé par DRM est encodé à débit binaire multiple (MBR), les métadonnées DRM utilisées pour la liste de lecture des variantes doivent être identiques aux métadonnées utilisées dans tous les flux de débit binaire.

[!TIP] {importance=&quot;high&quot;}

Lors du référencement des URL de ressources protégées DRM dans votre application iOS, le paramètre de chaîne de requête `?faxs=1` doit être ajouté à l’URL de niveau set M3U8 (MBR). Par exemple :

```
https://your.domain.com/hls/[...]/index.m3u8?faxs=1
```

Le paramètre de chaîne de `faxs=1` requête signale que le contenu est protégé par DRM et déclenche le processus de déchiffrement DRM en conséquence dans le SDK iOS TVSDK. Vous pouvez également ajouter la `faxs=1` balise aux URL de ressources HLS protégées par DRM qui sont destinées à d’autres plateformes ; il est observé comme requis sur iOS ou traité comme non-op dans les lecteurs sur d’autres plates-formes.

## Mise en oeuvre de Primetime DRM dans une application TSVDK {#implement-primetime-drm-in-a-tsvdk-application}

Primetime DRM est intégré à TVSDK, ce qui simplifie la mise en oeuvre de la protection de contenu dans une application TVSDK.

Pour obtenir une vue d’ensemble et des détails sur l’utilisation de Primetime DRM pour mettre en oeuvre la protection de contenu dans une application TVSDK, voir :

* [Adobe Primetime TVSDK-DRM Workflow (PDF)](https://helpx.adobe.com/content/dam/help/en/primetime/drm/drm_tvsdk_drm_workflow.pdf)