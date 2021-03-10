---
description: Ces classes fournissent des informations qui vous aident à déterminer les performances du lecteur.
title: Classes QoS
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---


# Classes QoS {#qos-classes}

Ces classes fournissent des informations qui vous aident à déterminer les performances du lecteur.

<table frame="all" colsep="1" rowsep="1" id="table_2893EFF9755149159A4F94E781C76B6E"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"><b>Nom</b></th> 
   <th colname="2" class="entry"><b>Description</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"> <a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTDeviceInformation.html" format="html" scope="external"> PTDeviceInformation</a> </td> 
   <td colname="2">Fournit des informations sur la plate-forme et le système d’exploitation sur lesquels TVSDK s’exécute : 
    <ul id="ul_0DE69F3B38E84964AB98DCCD11E5E123"> 
     <li id="li_19B2D1889FCA4B0F8FCB0EE8F87353B2">Version du système d’exploitation de la plate-forme </li> 
     <li id="li_CA35F4A48FD34555AC7D7832D5997AD4">Numéro de version de la bibliothèque TVSDK </li> 
     <li id="li_30D38320C2A3440E92C0A477FFFBF9A0">Nom du modèle du périphérique </li> 
     <li id="li_2D15164B987E405685B96A900EBF041D">Nom du fabricant du périphérique </li> 
     <li id="li_B78485CB9580444DB9694404706BA191">UUID du périphérique </li> 
     <li id="li_841EA77499B44F0692192F9DE1A798E4">Largeur/hauteur de l’écran du périphérique </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTPlaybackInformation.html" format="html" scope="external"> PTPlaybackInformation</a> </td> 
   <td colname="2"> Fournit des informations sur les performances de la lecture. Cela inclut la fréquence d’images, le débit par profil, le temps total passé en mémoire tampon, le nombre de tentatives de mise en mémoire tampon, le temps nécessaire pour obtenir le premier octet à partir du premier fragment vidéo, le temps nécessaire au rendu de la première image, la longueur actuellement mise en mémoire tampon et le temps de mise en mémoire tampon. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><a href="https://help.adobe.com/en_US/primetime/api/psdk/appledoc/Classes/PTQoSProvider.html" format="html" scope="external"> PTQoSProvider</a> </td> 
   <td colname="2">
    <pre>
      Fournit des mesures de qualité de service essentielles pour la lecture et le périphérique.
    </pre>
    <pre>
      Classe de fournisseur d’informations QOS.
    </pre> </td> 
  </tr> 
 </tbody> 
</table>