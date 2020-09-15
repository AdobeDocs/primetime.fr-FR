---
description: Le navigateur TVSDK prend en charge un certain nombre de fonctionnalités DASH que vous pouvez implémenter pour ajouter des fonctionnalités à vos applications vidéo.
seo-description: Le navigateur TVSDK prend en charge un certain nombre de fonctionnalités DASH que vous pouvez implémenter pour ajouter des fonctionnalités à vos applications vidéo.
seo-title: Fonctionnalités DASH prises en charge
title: Fonctionnalités DASH prises en charge
uuid: 299516a4-09ed-4b8a-b0bf-a04f204f385a
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---


# Fonctionnalités DASH prises en charge{#supported-dash-features}

Le navigateur TVSDK prend en charge un certain nombre de fonctionnalités DASH que vous pouvez implémenter pour ajouter des fonctionnalités à vos applications vidéo.

* [Fonctionnalités de lecture DASH Core](#dash-core-playback)
* [Fonctionnalités de lecture DASH Advanced](#dash-advanced-playback)
* [Fonctionnalités de protection du contenu DASH](#dash-content-protection)
* [Fonctions d’insertion des annonces DASH Core](#dash-core-ad-insertion)
* [Fonctions DASH Advanced Ad Insertion](#dash-advanced-insertion-features)
* [Intégrations DASH](#dash-integrations)

>[!TIP]
>
>Dans les tableaux de la matrice des fonctionnalités ci-dessous,  ![](assets/supported15.png)
>signifie que la fonctionnalité est prise en charge dans la version actuelle.

Les fonctionnalités suivantes sont prises en charge :

<!-- 

<table id="table_lrb_p2g_xx"> 
 <title>DASH integrations</title> 
 <tgroup cols="4"> 
  <colspec colnum="1" colname="col1" colwidth="*" /> 
  <colspec colnum="2" colname="col2" colwidth="*" /> 
  <colspec colnum="3" colname="col3" colwidth="*" /> 
  <colspec colnum="4" colname="col6" colwidth="*" /> 
  <thead> 
   <tr> 
    <th colname="col1" class="entry"> Category </th> 
    <th colname="col2" class="entry"> Content type </th> 
    <th colname="col3" class="entry"> Feature </th> 
    <th colname="col6" align="center" class="entry"> 
     <lines>
       HTML5 FF, IE, Chrome, Android Chrome
     </lines> </th> 
   </tr> 
  </thead> 
  <tbody> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Adobe Analytics VHL integration </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_14D9248BD1D8410E83AD27DB4AB3B6ED" /> </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Nielsen support </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_EFA853CB763446B3B37F2CF6BCC53EE1" /> </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Billing </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_B3A4E5937CEC4052977C08767219BC2B" /> </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Browserify </td> 
    <td colname="col6" valign="middle" align="center"><img href="assets/supported15.png" id="image_3330E81B86C84AD391AEBFDFE911A47F" /> </td> 
   </tr> 
  </tbody> 
 </tgroup> 
</table>

 -->

## Intégrations DASH {#dash-integrations}

| Catégorie | Type de contenu | Fonction | HTML5 FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Intégrations | VOD + Live | Intégration d’Adobe Analytics VHL | ![](assets/supported15.png) |
| Intégrations | VOD + Live | Facturation | ![](assets/supported15.png) |
| Intégrations | VOD + Live | Naviguer | ![](assets/supported15.png) |

## Fonctions DASH avancées d’insertion d’annonces (CSAI) {#dash-advanced-insertion-features}

| Catégorie | Type de contenu | Fonction | HTML5 FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| ad insertion | VOD | Publicité uniquement | Non pris en charge |
| ad insertion | VOD | Paramètres de ciblage | VOD uniquement |
| ad insertion | VOD | Paramètres personnalisés | VOD uniquement |
| ad insertion | VOD + Live | Stratégie publicitaire personnalisée | Non pris en charge |
| ad insertion | VOD + Live | Chargement de publicités différé | Non pris en charge |
| ad insertion | VOD | Publicités d’accompagnement, bannières publicitaires et publicités cliquables | Non pris en charge |
| ad insertion | VOD | VPAID 2.0 | Non pris en charge |

## Fonctionnalités d’insertion d’annonces principales DASH (CSAI) {#dash-core-ad-insertion}

| Catégorie | Type de contenu | Fonction | HTML5 FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| ad insertion | VOD + Live | Pré-roll | VOD uniquement |
| ad insertion | VOD + Live | Mid-roll | VOD uniquement |
| ad insertion | VOD + Live | Post-roll | VOD uniquement |
| ad insertion | FER VOD | Résolution et comportements des publicités | Non pris en charge |
| ad insertion | VOD + Live | Stratégie publicitaire par défaut | VOD uniquement |
| ad insertion | VOD + Live | VAST 2.0/3.0 | VOD uniquement |
| ad insertion | VOD + Live | VMAP 1.0 | VOD uniquement |
| ad insertion | VOD + Live | CRS v3.1 | VOD uniquement |

## Fonctionnalités de protection du contenu DASH {#dash-content-protection}

<table id="table_hrb_p2g_xx">  
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Catégorie </th> 
   <th colname="col2" class="entry"> Type de contenu </th> 
   <th colname="col3" class="entry"> Fonction </th> 
   <th colname="col6" class="entry"> HTML5 FF, IE, Chrome, Android Chrome</th>
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Protection du contenu </td> 
   <td colname="col2"> VOD + Live </td> 
   <td colname="col3"> AES-128 </td> 
   <td colname="col6"> Non pris en charge </td>
  </tr> 
  <tr> 
   <td colname="col1"> Protection du contenu </td> 
   <td colname="col2"> VOD + Live </td> 
   <td colname="col3"> Sample-AES </td> 
   <td colname="col6"> Non pris en charge </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Protection du contenu </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3"> DRM </td> 
   <td colname="col6"> 
    <ul id="ul_irb_p2g_xx"> 
     <li id="li_C4643F2978BC4C8ABDB3E6C72C75A468">Équipement sur 
      <ul id="ul_7047EA49AA3F40FE8F90E0ED6C028D83"> 
       <li id="li_B575735388D74D789D56BF373A470A6D">Chrome </li> 
       <li id="li_855146E4AC3A48E69B65F0022E1C0156">Firefox 47+ </li> 
       <li id="li_BC06B0A6EAAC4FC991C713775A8BB4DA">Chromecast </li> 
      </ul> </li> 
     <li id="li_D48B51C2208F423CB85D08886C2E1C66">PlayReady sur Internet Explorer sous Windows 8.1 et Edge </li> 
     <li id="li_2786AC19387241A296E015EE6FD07F2D">Accès aux Adobes pour Windows Firefox (vidéo uniquement) </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Fonctions de lecture avancées DASH {#dash-advanced-playback}

| Catégorie | Type de contenu | Fonction | HTML5, FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Lecture | VOD | Lecture au décalage | ![](assets/supported15.png) |
| Lecture | VOD | Lecture audio uniquement | ![](assets/supported15.png) |
| Lecture | VOD | Jeu de cartes | ![](assets/supported15.png) |
| Lecture | VOD | Lecture lisse | ![](assets/supported15.png) |
| Lecture | VOD + Live | Analyse ID3 | Non pris en charge |
| Lecture | VOD | Prise en charge sur plusieurs périodes | VOD uniquement |
| Lecture | VOD + Live | Flux jetés | Non pris en charge |
| Lecture | VOD + Live | Facturation | ![](assets/supported15.png) |
| Lecture | VOD + Live | Naviguer | ![](assets/supported15.png) |

## Fonctionnalités de lecture de base DASH {#dash-core-playback}

| Catégorie | Type de contenu | Fonction | HTML5 FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Lecture | VOD + Live | Lecture générale (Lecture, Pause, Recherche) | ![](assets/supported15.png) |
| Lecture | FER VOD | Lecture générale (Lecture, Pause, Recherche) | Non pris en charge |
| Lecture | VOD + Live | Débit adaptatif | ![](assets/supported15.png) |
| Lecture | VOD + Live | Légendes 608/708 | ![](assets/supported15.png) |
| Lecture | VOD + Live | WebVTT | VOD uniquement |
| Lecture | VOD + Live | Basculement | VOD uniquement |
| Lecture | VOD + Live | Notifications de la qualité de service et du lecteur | ![](assets/supported15.png) |
| Lecture | VOD + Live | Prise en charge des en-têtes de cookie | ![](assets/supported15.png) |
| Lecture | VOD + Live | Définition des paramètres de contrôle du tampon | ![](assets/supported15.png) |
| Lecture | VOD + Live | Définition des commandes de débit binaire adaptatif | ![](assets/supported15.png) |
| Lecture | VOD + Live | Balises personnalisées (EventStream) | VOD uniquement (intégré) |
| Lecture | VOD + Live | Audio à liaison tardive | VOD uniquement |
| Lecture | VOD + Live | 302 redirection | VOD uniquement |