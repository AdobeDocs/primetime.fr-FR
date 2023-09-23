---
description: Lorsque le navigateur TVSDK demande une publicité qui ne se trouve pas sur votre serveur de publicités principal, le lecteur doit demander la publicité au serveur secondaire. Le modèle de diffusion de publicités vidéo (VAST) définit la norme de communication entre les serveurs d’annonces et les lecteurs vidéo. Il s’agit de la réponse envoyée par le serveur d’annonces secondaires lorsque la publicité est demandée.
title: Publicités VAST
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# Publicités VAST {#vast-ads}

Lorsque le navigateur TVSDK demande une publicité qui ne se trouve pas sur votre serveur de publicités principal, le lecteur doit demander la publicité au serveur secondaire. Le modèle de diffusion de publicités vidéo (VAST) définit la norme de communication entre les serveurs d’annonces et les lecteurs vidéo. Il s’agit de la réponse envoyée par le serveur d’annonces secondaires lorsque la publicité est demandée.

Pour plus d’informations sur VAST, voir [Modèle de diffusion de publicités vidéo numériques (VAST) 3.0](https://www.iab.com/wp-content/uploads/2015/06/VASTv3_0.pdf).

Le navigateur TVSDK prend en charge les éléments publicitaires VAST suivants :

## Nettoyage et publicités intégrées {#section_11B8A1A8F52F4F77981C6AAC02185087}

Les éléments suivants sont pris en charge :

* **`wrapper`** Lorsque le lecteur doit contacter un serveur de publicités secondaire pour demander une publicité, l’élément wrapper fournit les informations de redirection. Un élément wrapper peut pointer vers plusieurs éléments wrapper qui pointent finalement vers une publicité VAST.

* **`inline`** Les éléments requis suivants sont pris en charge :

* `AdSystem`
* `AdTitle`
* `Impression`

  Les éléments facultatifs suivants sont pris en charge :

* `Description`
* `Survey`
* `Error`

## Créatifs {#section_0121F948CB074E49A8132D202786CAA4}

Cet élément est un fichier qui fait partie d’une publicité VAST et qui contient une variable `creative` élément pouvant prendre en charge une publicité linéaire, une publicité non linéaire ou une publicité compagnon. Dans le `creative` , l’élément `id`, `sequence`, et `adId` sont pris en charge.

Pour plus d’informations sur les types d’annonces, voir :

* **Publicités linéaires** Les éléments suivants sont pris en charge :

   * `TrackingEvent`, qui contient la variable `Tracking` élément .
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
        >Dans cet élément, la variable `id`, `bitrate`, `delivery`, `width`, `height`, `scalable`, `maintainAspectRatio`, `apiFramework`, et `type` Les attributs sont pris en charge.

* **Publicités non linéaires** Les éléments suivants sont pris en charge :

   * `Non-linear`

     >[!TIP]
     >
     >Dans cet élément, la variable `id`, `width`, `height`, `apiFramework`, `expandedWidth`, `expandedHeight`, `scalable`, `maintainAspectRatio`, et `minSuggestedDuration` Les attributs sont pris en charge.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `NonLinearClickThrough`
      * `AdParameters`

* **Publicités d&#39;accompagnement** Les éléments suivants sont pris en charge :

   * `Companion`

     >[!TIP]
     >
     >Dans cet élément, la variable `id`, `width`, `height`, `apiFramework`, `expandedWidth`, et `expandedHeight` Les attributs sont pris en charge.

      * `StaticResource`
      * `IFrameResource`
      * `HTMLResource`
      * `TrackingEvents`

## Extensions {#section_17401C75F419453BAE83637EEB6E1E60}

>[!TIP]
>
>Seules les extensions spécifiques aux Auditude sont prises en charge.

* `Extension`
