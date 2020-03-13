---
description: Lorsque le navigateur TVSDK demande une publicité qui ne se trouve pas sur votre serveur d’annonces principal, le lecteur doit la demander au serveur secondaire. Le modèle VAST (Video Ad Serving Template) définit la norme de communication entre les serveurs d’annonces et les lecteurs vidéo. Il s’agit de la réponse envoyée par le serveur d’annonces secondaire lorsque la publicité est demandée.
seo-description: Lorsque le navigateur TVSDK demande une publicité qui ne se trouve pas sur votre serveur d’annonces principal, le lecteur doit la demander au serveur secondaire. Le modèle VAST (Video Ad Serving Template) définit la norme de communication entre les serveurs d’annonces et les lecteurs vidéo. Il s’agit de la réponse envoyée par le serveur d’annonces secondaire lorsque la publicité est demandée.
seo-title: Annonces VAST
title: Annonces VAST
uuid: 052dae0c-2425-456c-aebe-531f68bb5aa8
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Annonces VAST {#vast-ads}

Lorsque le navigateur TVSDK demande une publicité qui ne se trouve pas sur votre serveur d’annonces principal, le lecteur doit la demander au serveur secondaire. Le modèle VAST (Video Ad Serving Template) définit la norme de communication entre les serveurs d’annonces et les lecteurs vidéo. Il s’agit de la réponse envoyée par le serveur d’annonces secondaire lorsque la publicité est demandée.

Pour plus d’informations sur VAST, voir [Digital Video Ad Serving Template (VAST) 3.0](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf).

Le SDK du navigateur prend en charge les éléments publicitaires VAST suivants :

## Enveloppe et publicités intégrées {#section_11B8A1A8F52F4F77981C6AAC02185087}

Les éléments suivants sont pris en charge :

* **`wrapper`** Lorsque le lecteur doit contacter un serveur de publicité secondaire pour demander une publicité, l’élément wrapper fournit les informations de redirection. Un élément wrapper peut pointer vers plusieurs wrappers qui pointent finalement vers une publicité VAST.

* **`inline`** Les éléments requis suivants sont pris en charge :

* `AdSystem`
* `AdTitle`
* `Impression`

   Les éléments facultatifs suivants sont pris en charge :

* `Description`
* `Survey`
* `Error`

## Créatifs {#section_0121F948CB074E49A8132D202786CAA4}

Cet élément est un fichier qui fait partie d’une publicité VAST et qui contient un `creative` élément qui peut prendre en charge une publicité linéaire, une publicité non linéaire ou une publicité connexe. Dans l’ `creative` élément, les éléments `id`, `sequence`et `adId` sont pris en charge.

Pour plus d&#39;informations sur les types de publicité, procédez comme suit :

* **Publicités** linéaires Les éléments suivants sont pris en charge :

   * `TrackingEvent`, qui contient l’ `Tracking` élément .
      * `Duration`
      * `AdParameters`
      * `VideoClicks`, notamment :

      * `ClickThrough`
      * `ClickTracking`
      * `CustomClick`

      * `MediaFiles`

      * `MediaFile`
         [!TIP]
Dans cet élément, les attributs `id`, `bitrate`, `delivery`, `width`, `height`, `scalable`, `maintainAspectRatio`,  et  sont pris en charge.`apiFramework``type`

* **Publicités** non linéaires Les éléments suivants sont pris en charge :

   * `Non-linear`
      [!TIP]
Dans cet élément, les attributs `id`, `width`, `height`, `apiFramework`, `expandedWidth`, `expandedHeight`, `scalable`,  et  sont pris en charge.`maintainAspectRatio``minSuggestedDuration`

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `NonLinearClickThrough`
      * `AdParameters`

* **Publicités** complémentaires Les éléments suivants sont pris en charge :

   * `Companion`
      [!TIP]
Dans cet élément, les attributs `id`, `width`, `height`, `apiFramework`, `expandedWidth`et `expandedHeight` sont pris en charge.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `TrackingEvents`

## Extensions {#section_17401C75F419453BAE83637EEB6E1E60}

[!TIP]
Seules les extensions spécifiques à Auditude sont prises en charge.

* `Extension`