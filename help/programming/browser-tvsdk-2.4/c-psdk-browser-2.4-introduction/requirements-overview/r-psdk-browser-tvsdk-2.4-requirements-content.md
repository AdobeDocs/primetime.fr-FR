---
description: Vérifiez les restrictions et les exigences pour les flux et les listes de lecture (manifestes).
seo-description: Vérifiez les restrictions et les exigences pour les flux et les listes de lecture (manifestes).
seo-title: Exigences en matière de contenu et de manifeste
title: Exigences en matière de contenu et de manifeste
uuid: 22ee7d02-b06d-4162-a8a4-a2391658fdb3
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# Exigences en matière de contenu et de manifeste{#content-and-manifest-requirements}

Vérifiez les restrictions et les exigences pour les flux et les listes de lecture (manifestes).

<table id="table_D7C38CD3B4D24C3D9A3B55D8CEFE7366"> 
 <tbody> 
  <tr> 
   <td colname="col1"> Durée du segment de contenu </td> 
   <td colname="col2"> La durée d’un segment ne doit pas dépasser la durée de cible spécifiée dans le fichier manifeste. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Exigences de contenu </td> 
   <td colname="col2"> Chaque segment TS doit être début avec un cadre clé. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Contenu HLS </td> 
   <td colname="col2"> <p>Souvenez-vous des points suivants : 
     <ul id="ul_B226605345EA46F69DA1380E16826117"> 
      <li id="li_6564DC0E879544BB8513DD2D1CFBA8DE">Le son AAC-SSR n'est pas pris en charge. </li> 
      <li id="li_B73CAEBE4347406EA4DB25551B444BDA">Les codecs audio AC3 et AC3 amélioré ne sont pas pris en charge. </li> 
      <li id="li_5986DD33C0FE485D99D4C00E2E6012CA">Les flux HLS présentent une discontinuité, mais aucun marqueur de discontinuité n’est pris en charge. </li> 
      <li id="li_FED8686372DF4A39BAABC531BA4EB137">HLS Live ne prend pas en charge le roulement de l’horodatage. </li> 
      <li id="li_565CFBEAD9874BA48F6E25B0893BF131">Les publicités dans la fenêtre DVR des flux HLS Live ne sont pas résolues. </li> 
      <li id="li_7D22EA32C94240D79EDDA96D9E72FE8F">La plage d’octets n’est pas prise en charge avec le contenu chiffré AES-128. </li> 
     </ul></p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Contenu DASH </td> 
   <td colname="col2"> <p>Souvenez-vous des points suivants : 
     <ul id="ul_9D33C2418F9F49DEAE0E642301726F89"> 
      <li id="li_74C69A21A7BD4831B92F0D57900E1CB1">Pour les flux en direct : le profil en direct avec le type dynamique est pris en charge. </li> 
      <li id="li_0C8743DB152047819D23C9F180998AD7">Pour les flux VOD : le profil dynamique avec type statique est pris en charge. </li> 
      <li id="li_FBC6828663FB413798A4BDAF0B9831AA">Pour les flux VOD - Le profil à la demande n’est pas certifié pour les workflows publicitaires. </li> 
      <li id="li_4393B9B1F6144BDEAE484C879750ED23">La lecture de flux DASH comportant plusieurs périodes n’est pas prise en charge. </li> 
      <li id="li_6A2CEC4E974C4D44A45F5503A1A9D8D0">Les légendes intégrées (608/708), signalées par la balise Accessibility, sont prises en charge. </li> 
      <li id="li_EDE93DF4F3A64A53BA80877F701A8F0D">Les fichiers VTT fragmentés/segmentés ne sont pas pris en charge. </li> 
      <li id="li_8897F73611194030A490A4FF1178364C">Les flux comportant des balises personnalisées en bande ne sont pas certifiés. </li> 
     </ul></p> </td> 
  </tr> 
 </tbody> 
</table>

