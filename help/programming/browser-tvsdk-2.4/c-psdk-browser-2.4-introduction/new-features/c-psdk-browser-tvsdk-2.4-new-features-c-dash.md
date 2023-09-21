---
description: Le TVSDK du navigateur prend en charge un certain nombre de fonctionnalités DASH que vous pouvez mettre en oeuvre pour ajouter des fonctionnalités à vos applications vidéo.
title: Fonctionnalités DASH prises en charge
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Fonctionnalités DASH prises en charge{#supported-dash-features}

Le TVSDK du navigateur prend en charge un certain nombre de fonctionnalités DASH que vous pouvez mettre en oeuvre pour ajouter des fonctionnalités à vos applications vidéo.

* [Fonctionnalités de lecture principale DASH](#dash-core-playback)
* [Fonctionnalités de lecture avancées DASH](#dash-advanced-playback)
* [Fonctionnalités de protection du contenu DASH](#dash-content-protection)
* [Fonctionnalités d’insertion des publicités principales DASH](#dash-core-ad-insertion)
* [Fonctionnalités d’insertion de publicités avancées DASH](#dash-advanced-insertion-features)
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

| Catégorie | Type de contenu | Fonctionnalité | HTML5 FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Intégrations | VOD + En direct | Intégration d’Adobe Analytics VHL | ![](assets/supported15.png) |
| Intégrations | VOD + En direct | Facturation | ![](assets/supported15.png) |
| Intégrations | VOD + En direct | Browserify | ![](assets/supported15.png) |

## Fonctionnalités DASH avancées d’insertion de publicités (CSAI) {#dash-advanced-insertion-features}

| Catégorie | Type de contenu | Fonctionnalité | HTML5 FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Ad Insertion | VOD | Publicité uniquement | Non pris en charge |
| Ad Insertion | VOD | Paramètres de ciblage | VOD uniquement |
| Ad Insertion | VOD | Paramètres personnalisés | VOD uniquement |
| Ad Insertion | VOD + En direct | Stratégie d’annonce personnalisée | Non pris en charge |
| Ad Insertion | VOD + En direct | Chargement différé des publicités | Non pris en charge |
| Ad Insertion | VOD | Publicités d’accompagnement, bannières publicitaires et annonces cliquables | Non pris en charge |
| Ad Insertion | VOD | VPAID 2.0 | Non pris en charge |

## Fonctionnalités d’insertion des publicités principales DASH (CSAI) {#dash-core-ad-insertion}

| Catégorie | Type de contenu | Fonctionnalité | HTML5 FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Ad Insertion | VOD + En direct | Pré-roll | VOD uniquement |
| Ad Insertion | VOD + En direct | Mid-roll | VOD uniquement |
| Ad Insertion | VOD + En direct | Post-roll | VOD uniquement |
| Ad Insertion | FER VOD | Résolution et comportement des publicités | Non pris en charge |
| Ad Insertion | VOD + En direct | Stratégie de publicité par défaut | VOD uniquement |
| Ad Insertion | VOD + En direct | VAST 2.0/3.0 | VOD uniquement |
| Ad Insertion | VOD + En direct | VMAP 1.0 | VOD uniquement |
| Ad Insertion | VOD + En direct | CRS v3.1 | VOD uniquement |

## Fonctionnalités de protection du contenu DASH {#dash-content-protection}

<table id="table_hrb_p2g_xx">  
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Catégorie </th> 
   <th colname="col2" class="entry"> Type de contenu </th> 
   <th colname="col3" class="entry"> Fonctionnalité </th> 
   <th colname="col6" class="entry"> HTML5 FF, IE, Chrome, Android Chrome</th>
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Protection du contenu </td> 
   <td colname="col2"> VOD + En direct </td> 
   <td colname="col3"> AES-128 </td> 
   <td colname="col6"> Non pris en charge </td>
  </tr> 
  <tr> 
   <td colname="col1"> Protection du contenu </td> 
   <td colname="col2"> VOD + En direct </td> 
   <td colname="col3"> Sample-AES </td> 
   <td colname="col6"> Non pris en charge </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Protection du contenu </td> 
   <td colname="col2"> VOD </td> 
   <td colname="col3"> DRM </td> 
   <td colname="col6"> 
    <ul id="ul_irb_p2g_xx"> 
     <li id="li_C4643F2978BC4C8ABDB3E6C72C75A468">Épouse allumée 
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

## Fonctionnalités de lecture avancées DASH {#dash-advanced-playback}

| Catégorie | Type de contenu | Fonctionnalité | HTML5, FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Lecture | VOD | Lecture au décalage | ![](assets/supported15.png) |
| Lecture | VOD | Lecture audio seule | ![](assets/supported15.png) |
| Lecture | VOD | Lecture de piste | ![](assets/supported15.png) |
| Lecture | VOD | Lecture de la mbox | ![](assets/supported15.png) |
| Lecture | VOD + En direct | Analyse d’ID3 | Non pris en charge |
| Lecture | VOD | Prise en charge sur plusieurs périodes | VOD uniquement |
| Lecture | VOD + En direct | Flux jetés | Non pris en charge |
| Lecture | VOD + En direct | Facturation | ![](assets/supported15.png) |
| Lecture | VOD + En direct | Browserify | ![](assets/supported15.png) |

## Fonctionnalités de lecture principale de DASH {#dash-core-playback}

| Catégorie | Type de contenu | Fonctionnalité | HTML5 FF, IE, Chrome, Android Chrome |
|---|---|---|---|
| Lecture | VOD + En direct | Lecture générale (Lecture, Pause, Recherche) | ![](assets/supported15.png) |
| Lecture | FER VOD | Lecture générale (Lecture, Pause, Recherche) | Non pris en charge |
| Lecture | VOD + En direct | Débit adaptatif | ![](assets/supported15.png) |
| Lecture | VOD + En direct | légendes 608/708 | ![](assets/supported15.png) |
| Lecture | VOD + En direct | WebVTT | VOD uniquement |
| Lecture | VOD + En direct | Basculement | VOD uniquement |
| Lecture | VOD + En direct | Notifications QoS et du lecteur | ![](assets/supported15.png) |
| Lecture | VOD + En direct | Prise en charge des en-têtes de cookie | ![](assets/supported15.png) |
| Lecture | VOD + En direct | Définition des paramètres de contrôle de la mémoire tampon | ![](assets/supported15.png) |
| Lecture | VOD + En direct | Définition des contrôles de débit adaptatif | ![](assets/supported15.png) |
| Lecture | VOD + En direct | Balises personnalisées (EventStream) | VOD uniquement (intégré) |
| Lecture | VOD + En direct | Liaison audio tardive | VOD uniquement |
| Lecture | VOD + En direct | 302 redirect | VOD uniquement |
