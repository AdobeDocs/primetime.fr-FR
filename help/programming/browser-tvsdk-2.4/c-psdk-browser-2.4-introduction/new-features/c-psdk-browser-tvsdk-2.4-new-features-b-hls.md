---
description: Le TVSDK du navigateur prend en charge un certain nombre de fonctionnalités HLS que vous pouvez mettre en oeuvre pour ajouter des fonctionnalités à vos applications vidéo.
title: Fonctionnalités HLS prises en charge
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---

# Fonctionnalités HLS prises en charge {#supported-hls-features}

Le TVSDK du navigateur prend en charge un certain nombre de fonctionnalités HLS que vous pouvez mettre en oeuvre pour ajouter des fonctionnalités à vos applications vidéo.

* [Lecture principale HLS](#hls-core-playback)
* [Fonctionnalités de lecture avancées HLS](#hls-advanced-playback)
* [Fonctionnalités de protection de contenu HLS](#hls-content-protection)
* [Fonctionnalités d’insertion des publicités principales HLS](#hls-core-ad-insertion)
* [Fonctionnalités d’insertion de publicités avancées HLS](#hls-advanced-ad-insertion)
* [Intégrations HLS](#hls-integrations)

>[!TIP]
>
>Dans les tableaux de la matrice des fonctionnalités ci-dessous, ![icône prise en charge](assets/supported15.png) signifie que la fonctionnalité est prise en charge dans la version actuelle.

>[!TIP]
>
>Dans la colonne Safari, &quot;Limitation de plateforme&quot; signifie que le cas d’utilisation n’est pas pris en charge, car cette plateforme n’autorise pas l’implémentation de la prise en charge. Dans le cas d&#39;une insertion, utilisez SSAI. S’il existe des limitations de lecture importantes pour vous, forcez la reprise sur le Flash sur Safari jusqu’à ce que la plateforme prenne en charge le cas d’utilisation de l’insertion de publicités.

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

| Catégorie | Type de contenu | Fonctionnalité | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Intégrations | VOD + En direct | Intégration d’Adobe Analytics VHL | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |

## Fonctionnalités avancées d’insertion de publicités HLS (CSAI) {#hls-advanced-ad-insertion}

| Catégorie | Type de contenu | Fonctionnalité | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | VOD | Publicité uniquement | Non pris en charge | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Ad Insertion | VOD + En direct | Paramètres de ciblage | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Ad Insertion | VOD + En direct | Stratégie d’annonce personnalisée | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation de la plateforme |
| Ad Insertion | VOD + En direct | Chargement différé des publicités | ![icône prise en charge](assets/supported15.png) | Non pris en charge | Limitation de la plateforme |
| Ad Insertion | VOD | Publicités d’accompagnement, bannières publicitaires et annonces cliquables | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Ad Insertion | VOD | VPAID 2.0 | SWF | JavaScript | JavaScript |

## Fonctionnalités principales d’insertion d’annonces HLS (CSAI) {#hls-core-ad-insertion}

| Catégorie | Type de contenu | Fonctionnalité | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | VOD + En direct | Pré-roll | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Ad Insertion | VOD + En direct | Mid-roll | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation de la plateforme |
| Ad Insertion | VOD + En direct | Post-roll | VOD uniquement | VOD uniquement | VOD uniquement |
| Ad Insertion | FER VOD | Résolution et comportements des publicités | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation de la plateforme |
| Ad Insertion | VOD + En direct | Stratégie de publicité par défaut | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation de la plateforme |
| Ad Insertion | VOD + En direct | VAST 2.0/3.0 | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Ad Insertion | VOD + En direct | VMAP 1.0 | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Ad Insertion | VOD + En direct | CRS v3.1 | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |

## Fonctionnalités de protection de contenu HLS {#hls-content-protection}

| Catégorie | Type de contenu | Fonctionnalité | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Protection du contenu | VOD + En direct | AES-128 | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Protection du contenu | VOD + En direct | Sample-AES | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Protection du contenu | VOD | DRM | Accès aux Adobes | Non pris en charge | FairPlay |

## Fonctionnalités de lecture avancées HLS {#hls-advanced-playback}

| Catégorie | Type de contenu | Fonctionnalité | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Lecture | VOD | Lecture au décalage | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD | Lecture audio seule | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD | Lecture de piste | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD | Lecture de l’astuce | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation de la plateforme |
| Lecture | VOD + En direct | Analyse d’ID3 | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Non pris en charge |
| Lecture | VOD + En direct | Prise en charge des marqueurs de discontinuité | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD + En direct | Flux jetés | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation de la plateforme |
| Lecture | VOD + En direct | Facturation | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD + En direct | Browserify | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |

## Lecture principale HLS {#hls-core-playback}

| Catégorie | Type de contenu | Fonctionnalité | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Lecture | VOD + En direct | Lecture générale (Lecture, Pause, Recherche) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | FER VOD | Lecture générale (Lecture, Pause, Recherche) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD + En direct | Débit adaptatif | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD + En direct | légendes 608/708 | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD + En direct | WebVTT | ![icône prise en charge](assets/supported15.png) | VOD uniquement | VOD uniquement |
| Lecture | VOD + En direct | Basculement du manifeste | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) |
| Lecture | VOD + En direct | Basculement avancé | ![icône prise en charge](assets/supported15.png) | VOD uniquement | Limitation de la plateforme |
| Lecture | VOD + En direct | Notifications QoS et du lecteur | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Prise en charge limitée de QoS |
| Lecture | VOD + En direct | Prise en charge des en-têtes de cookie | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation de la plateforme |
| Lecture | VOD + En direct | Définition des paramètres de contrôle de la mémoire tampon | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation de la plateforme |
| Lecture | VOD + En direct | Définition des contrôles de débit adaptatif | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation de la plateforme |
| Lecture | VOD + En direct | Balises personnalisées | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation de la plateforme |
| Lecture | VOD + En direct | Liaison audio tardive | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation de la plateforme |
| Lecture | VOD + En direct | 302 redirect | ![icône prise en charge](assets/supported15.png) | ![icône prise en charge](assets/supported15.png) | Limitation de la plateforme |
