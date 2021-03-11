---
description: Lorsque le navigateur TVSDK demande une publicité qui ne se trouve pas sur votre serveur d’annonces Principal, le lecteur doit la demander au serveur secondaire. Le modèle de diffusion d’annonces vidéo (VAST) définit la norme de communication entre les serveurs d’annonces et les lecteurs vidéo. Il s’agit de la réponse envoyée par le serveur d’annonces secondaires lorsque la publicité est demandée.
title: Annonces VAST
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# Publicités VAST {#vast-ads}

Lorsque le navigateur TVSDK demande une publicité qui ne se trouve pas sur votre serveur d’annonces Principal, le lecteur doit la demander au serveur secondaire. Le modèle de diffusion d’annonces vidéo (VAST) définit la norme de communication entre les serveurs d’annonces et les lecteurs vidéo. Il s’agit de la réponse envoyée par le serveur d’annonces secondaires lorsque la publicité est demandée.

Pour plus d’informations sur VAST, voir [Modèle de diffusion d’annonces vidéo numérique (VAST) 3.0](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf).

Le navigateur TVSDK prend en charge les éléments publicitaires VAST suivants :

## Enveloppe et publicités intégrées {#section_11B8A1A8F52F4F77981C6AAC02185087}

Les éléments suivants sont pris en charge :

* **`wrapper`** Lorsque le lecteur doit contacter un serveur d’annonces secondaire pour demander une publicité, l’élément wrapper fournit les informations de redirection. Un élément wrapper peut pointer vers plusieurs wrappers qui pointent en fin de compte vers une publicité VAST.

* **`inline`** Les éléments requis suivants sont pris en charge :

* `AdSystem`
* `AdTitle`
* `Impression`

   Les éléments facultatifs suivants sont pris en charge :

* `Description`
* `Survey`
* `Error`

## Créatifs {#section_0121F948CB074E49A8132D202786CAA4}

Cet élément est un fichier qui fait partie d&#39;une publicité VAST et qui contient un élément `creative` qui peut prendre en charge une publicité linéaire, une publicité non linéaire ou une publicité connexe. Dans l’élément `creative`, les éléments `id`, `sequence` et `adId` sont pris en charge.

Pour plus d&#39;informations sur les types d&#39;annonces, consultez :

* **** Publicités linéairesLes éléments suivants sont pris en charge :

   * `TrackingEvent`, qui contient l’ `Tracking` élément.
      * `Duration`
      * `AdParameters`
      * `VideoClicks`, notamment :

      * `ClickThrough`
      * `ClickTracking`
      * `CustomClick`

      * `MediaFiles`

      * `MediaFile`

         >[!TIP]
         >
         >Dans cet élément, les attributs `id`, `bitrate`, `delivery`, `width`, `height`, `scalable`, `maintainAspectRatio`, `apiFramework` et `type` sont pris en charge.

* **** Publicités non linéairesLes éléments suivants sont pris en charge :

   * `Non-linear`

      >[!TIP]
      >
      >Dans cet élément, les attributs `id`, `width`, `height`, `apiFramework`, `expandedWidth`, `expandedHeight`, `scalable`, `maintainAspectRatio` et `minSuggestedDuration` sont pris en charge.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `NonLinearClickThrough`
      * `AdParameters`

* **Publicités complémentairesLes éléments suivants sont pris en charge :** 

   * `Companion`

      >[!TIP]
      >
      >Dans cet élément, les attributs `id`, `width`, `height`, `apiFramework`, `expandedWidth` et `expandedHeight` sont pris en charge.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `TrackingEvents`

## Extensions {#section_17401C75F419453BAE83637EEB6E1E60}

>[!TIP]
>
>Seules les extensions spécifiques à Auditude sont prises en charge.

* `Extension`
