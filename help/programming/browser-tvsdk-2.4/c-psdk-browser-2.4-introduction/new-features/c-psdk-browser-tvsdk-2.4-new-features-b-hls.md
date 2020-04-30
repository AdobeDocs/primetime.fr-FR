---
description: Le navigateur TVSDK prend en charge un certain nombre de fonctionnalités HLS que vous pouvez mettre en oeuvre pour ajouter des fonctionnalités à vos applications vidéo.
seo-description: Le navigateur TVSDK prend en charge un certain nombre de fonctionnalités HLS que vous pouvez mettre en oeuvre pour ajouter des fonctionnalités à vos applications vidéo.
seo-title: Fonctionnalités HLS prises en charge
title: Fonctionnalités HLS prises en charge
uuid: 033d81f8-cea4-4687-b2fb-1524d9164d39
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Fonctionnalités HLS prises en charge {#supported-hls-features}

Le navigateur TVSDK prend en charge un certain nombre de fonctionnalités HLS que vous pouvez mettre en oeuvre pour ajouter des fonctionnalités à vos applications vidéo.

* [Lecture principale HLS](#hls-core-playback)
* [Fonctionnalités de lecture avancées HLS](#hls-advanced-playback)
* [Fonctionnalités de protection du contenu HLS](#hls-content-protection)
* [Fonctionnalités d&#39;insertion des publicités HLS Core](#hls-core-ad-insertion)
* [Fonctionnalités d&#39;insertion de publicités HLS avancées](#hls-advanced-ad-insertion)
* [Intégrations HLS](#hls-integrations)

>[!TIP]
>
>Dans les tableaux de la matrice des fonctionnalités ci-dessous, une icône ![](assets/supported15.png) prise en charge signifie que la fonctionnalité est prise en charge dans la version actuelle.

>[!TIP]
>
>Dans la colonne Safari, &quot;Limitation des plateformes&quot; signifie que le cas d’utilisation n’est pas pris en charge car cette plateforme n’autorise pas l’implémentation de la prise en charge. En cas d’insertion, utilisez SSAI. S’il existe des limitations de lecture importantes pour vous, forcez la reprise vers Flash sur Safari jusqu’à ce que la plate-forme prenne en charge le cas d’utilisation de l’insertion d’annonces.

<!--<a id="section_9FB9193D5763448CB228B96164661738"></a>-->

Les fonctionnalités suivantes sont prises en charge :

<!-- 

Removed Nielsen row 
<table id="table_D9E2D82992554905A0A551CC71AFA189"> 
 <title>HLS integrations</title> 
 <tgroup cols="6"> 
  <colspec colnum="1" colname="col1" colwidth="*" /> 
  <colspec colnum="2" colname="col2" colwidth="*" /> 
  <colspec colnum="3" colname="col3" colwidth="*" /> 
  <colspec colnum="4" colname="col4" colwidth="*" /> 
  <colspec colnum="5" colname="col5" colwidth="*" /> 
  <colspec colnum="6" colname="col7" colwidth="*" /> 
  <thead> 
   <tr> 
    <th colname="col1" morerows="1" class="entry"> Category </th> 
    <th colname="col2" morerows="1" class="entry"> Content type </th> 
    <th colname="col3" morerows="1" class="entry"> Feature </th> 
    <th colname="col4" morerows="1" class="entry"> Flash </th> 
    <th namest="col5" nameend="col7" class="entry"> HTML5 </th> 
   </tr> 
   <tr> 
    <th colname="col5" class="entry"> FF, IE, Chrome, Android Chrome </th> 
    <th colname="col7" class="entry"> Safari, iOS Safari </th> 
   </tr> 
  </thead> 
  <tbody> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Adobe Analytics VHL integration </td> 
    <td colname="col4">![supported icon](assets/supported15.png) </td> 
    <td colname="col5">![supported icon](assets/supported15.png) </td> 
    <td colname="col7">![supported icon](assets/supported15.png) </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Nielsen support </td> 
    <td colname="col4">![supported icon](assets/supported15.png) </td> 
    <td colname="col5">![supported icon](assets/supported15.png) </td> 
    <td colname="col7">![supported icon](assets/supported15.png) </td> 
   </tr> 
  </tbody> 
 </tgroup> 
</table>

 -->

## Intégrations HLS {#hls-integrations}

| Catégorie | Type de contenu | Fonction | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Intégrations | VOD + Live | Intégration d’Adobe Analytics VHL | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |

## Fonctions avancées d’insertion d’annonces HLS (CSAI) {#hls-advanced-ad-insertion}

| Catégorie | Type de contenu | Fonction | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Insertion d&#39;annonce | VOD | Publicité uniquement | Non pris en charge | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Insertion d&#39;annonce | VOD + Live | Paramètres de ciblage | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Insertion d&#39;annonce | VOD + Live | Stratégie publicitaire personnalisée | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation des plateformes |
| Insertion d&#39;annonce | VOD + Live | Chargement de publicités différé | ![icône prise en charge](assets/supported15.png) | Non pris en charge | Limitation des plateformes |
| Insertion d&#39;annonce | VOD | Publicités d’accompagnement, bannières publicitaires et publicités cliquables | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Insertion d&#39;annonce | VOD | VPAID 2.0 | SWF | JavaScript | JavaScript |

## Fonctions d’insertion d’annonces principales HLS (CSAI) {#hls-core-ad-insertion}

| Catégorie | Type de contenu | Fonction | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Insertion d&#39;annonce | VOD + Live | Pré-roll | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Insertion d&#39;annonce | VOD + Live | Mid-roll | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation des plateformes |
| Insertion d&#39;annonce | VOD + Live | Post-roll | VOD uniquement | VOD uniquement | VOD uniquement |
| Insertion d&#39;annonce | FER VOD | Résolution et comportements des publicités | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation des plateformes |
| Insertion d&#39;annonce | VOD + Live | Stratégie publicitaire par défaut | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation des plateformes |
| Insertion d&#39;annonce | VOD + Live | VAST 2.0/3.0 | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Insertion d&#39;annonce | VOD + Live | VMAP 1.0 | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Insertion d&#39;annonce | VOD + Live | CRS v3.1 | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |

## Fonctionnalités de protection du contenu HLS {#hls-content-protection}

| Catégorie | Type de contenu | Fonction | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Protection du contenu | VOD + Live | AES-128 | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Protection du contenu | VOD + Live | Sample-AES | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Protection du contenu | VOD | DRM | Adobe Access | Non pris en charge | FairPlay |

## Fonctions de lecture avancées HLS {#hls-advanced-playback}

| Catégorie | Type de contenu | Fonction | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Lecture | VOD | Lecture au décalage | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD | Lecture audio uniquement | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD | Jeu de cartes | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD | Lecture lisse | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation des plateformes |
| Lecture | VOD + Live | Analyse ID3 | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Non pris en charge |
| Lecture | VOD + Live | Prise en charge des marqueurs de discontinuité | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD + Live | Flux jetés | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation des plateformes |
| Lecture | VOD + Live | Facturation | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD + Live | Naviguer | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |

## Lecture noyau HLS {#hls-core-playback}

| Catégorie | Type de contenu | Fonction | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Lecture | VOD + Live | Lecture générale (Lecture, Pause, Recherche) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | FER VOD | Lecture générale (Lecture, Pause, Recherche) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD + Live | Débit adaptatif | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD + Live | Légendes 608/708 | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD + Live | WebVTT | ![icône prise en charge](assets/supported15.png) | VOD uniquement | VOD uniquement |
| Lecture | VOD + Live | Basculement du manifeste | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD + Live | Basculement avancé | ![icône prise en charge](assets/supported15.png) | VOD uniquement | Limitation des plateformes |
| Lecture | VOD + Live | Notifications de la qualité de service et du lecteur | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Prise en charge limitée de la qualité de service |
| Lecture | VOD + Live | Prise en charge des en-têtes de cookie | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation des plateformes |
| Lecture | VOD + Live | Définition des paramètres de contrôle du tampon | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation des plateformes |
| Lecture | VOD + Live | Définition des commandes de débit binaire adaptatif | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation des plateformes |
| Lecture | VOD + Live | Balises personnalisées | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation des plateformes |
| Lecture | VOD + Live | Audio à liaison tardive | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation des plateformes |
| Lecture | VOD + Live | 302 redirection | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation des plateformes |