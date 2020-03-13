---
description: Sur les périphériques prenant en charge l’accélération GPU (matérielle), vous pouvez utiliser un objet flash.media.StageVideo pour traiter la vidéo directement sur le matériel du périphérique.
seo-description: Sur les périphériques prenant en charge l’accélération GPU (matérielle), vous pouvez utiliser un objet flash.media.StageVideo pour traiter la vidéo directement sur le matériel du périphérique.
seo-title: Configuration minimale requise pour StageVideo
title: Configuration minimale requise pour StageVideo
uuid: 8916dbac-33e0-4efd-8105-9ddbc85f0a3f
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# Configuration minimale requise pour StageVideo{#stagevideo-minimum-requirements}

Sur les périphériques prenant en charge l’accélération GPU (matérielle), vous pouvez utiliser un objet flash.media.StageVideo pour traiter la vidéo directement sur le matériel du périphérique.

<!--<a id="section_64DDAA8DB215493E8A7CA6636819D350"></a>-->

Une combinaison de différents facteurs détermine quand et comment vous pouvez utiliser `StageVideo`. Le tableau suivant présente un instantané de certaines des exigences et restrictions associées à l’utilisation de StageVideo. Ces exigences et restrictions peuvent être modifiées.

<table id="table_882F4462A5AE47E28A60A39D112164A7"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Plateforme </th> 
   <th colname="col2" class="entry"> Windows et Mac OS </th> 
  </tr>
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> Flash Player </td> 
   <td colname="col2"> 
    <ul id="ul_s42_lm2_jp"> 
     <li id="li_308FA9EC206B437A9EE04C29F9480B73">Au moins Flash 10.1 ou version ultérieure </li> 
     <li id="li_5898EDB0D12A43389076BCC7F4A27A0A">Pour la fonctionnalité de secours aux logiciels, Flash 15 et versions ultérieures </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1">Navigateurs et paramètres <span class="codeph"> wmode</span> </td> 
   <td colname="col2"> <p><b>Dans Flash 15</b>, définissez <span class="codeph"> wmode=opaque</span> pour que vous puissiez utiliser des incrustations HTML. </p> <p>Les navigateurs suivants ne prennent actuellement pas en charge l’accélération matérielle : 
     <ul id="ul_frv_ykf_jp"> 
      <li id="li_3D407A61FEE042A9B85A6EFACA6D7719">Mozilla Firefox sous Microsoft Windows </li> 
      <li id="li_39B85AC352564DA8B86EA826638F1F4B">Google Chrome avant 26 et toute version de Chrome sous Windows XP et Vista </li> 
      <li id="li_0042BA6070C849E6B7C4B4BF4333F712">Microsoft Internet Explorer (toutes les versions) </li> 
     </ul>D’autres combinaisons navigateur/système d’exploitation peuvent empêcher l’accès à l’accélération matérielle. Dans ces scénarios, <span class="codeph"> StageVideo</span> revient au logiciel avec un impact négatif sur les performances. </p> <p><b>Dans Flash 14 et les versions antérieures</b>, si le navigateur ne prend pas en charge l’accélération matérielle, le lecteur Flash peut effectuer le rendu directement sur le GPU, mais définir <span class="codeph"> wmode=direct</span> pour activer ce rendu. <p>Conseil :  Les pilotes GPU plus anciens que 2009 devront peut-être être mis à jour car ils ne prennent pas en charge l'accélération matérielle. </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> Objet NetStream </td> 
   <td colname="col2">Le  <span class="codeph"> StageVideoEvent.RENDER_STATE</span> n’est pas distribué, sauf si vous associez un objet <span class="codeph"> NetStream</span> à l’objet <span class="codeph"> StageVideo</span> . </td> 
  </tr> 
 </tbody> 
</table>

