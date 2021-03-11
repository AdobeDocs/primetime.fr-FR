---
description: Ces classes fournissent des informations qui vous aident à déterminer les performances du lecteur.
title: Classes QoS
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# Classes QoS {#qos-classes}

Ces classes fournissent des informations qui vous aident à déterminer les performances du lecteur.

Package : [com.adobe.mediacore.qos](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/package-summary.html) Package : [com.adobe.mediacore.qos.metrics](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/package-summary.html)

<table frame="all" colsep="1" rowsep="1" id="table_2893EFF9755149159A4F94E781C76B6E"> 
 <thead> 
  <tr rowsep="1"> 
   <th colname="1" class="entry"> Nom </th> 
   <th colname="2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph">mesures.<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/BufferingMetrics.html" format="html" scope="external"> Mesures de mémoire tampon</a></span></td> 
   <td colname="2"> Fournit des informations sur le temps passé par le lecteur lors de la mise en mémoire tampon et la fréquence à laquelle un événement de mise en mémoire tampon s’est produit. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/DeviceInformation.html" format="html" scope="external"> Informations sur le périphérique</a> </span></td> 
   <td colname="2">Fournit des informations sur la plate-forme et le système d’exploitation sur lesquels l’expression
    exécute : 
    <ul id="ul_0DE69F3B38E84964AB98DCCD11E5E123"> 
     <li id="li_19B2D1889FCA4B0F8FCB0EE8F87353B2">Version du système d’exploitation de la plate-forme </li> 
     <li id="li_CA35F4A48FD34555AC7D7832D5997AD4">Numéro de version de la bibliothèque Expression </li> 
     <li id="li_30D38320C2A3440E92C0A477FFFBF9A0">Nom du modèle du périphérique </li> 
     <li id="li_2D15164B987E405685B96A900EBF041D">Nom du fabricant du périphérique </li> 
     <li id="li_B78485CB9580444DB9694404706BA191">UUID du périphérique </li> 
     <li id="li_841EA77499B44F0692192F9DE1A798E4">Largeur/hauteur de l’écran du périphérique </li> 
    </ul> </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/LoadInfo.html" format="html" scope="external"> LoadInfo</a></span> </td> 
   <td colname="2"> Contient diverses informations de qualité de service sur le chargement de diverses ressources (fichiers, manifeste ou liste de lecture, fragments/segments, pistes, etc.). </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/PlaybackInformation.html" format="html" scope="external"> PlaybackInformation</a></span> </td> 
   <td colname="2"> Fournit des informations sur les performances de la lecture. Cela inclut la fréquence d’images, le débit par profil, le temps total passé en mémoire tampon, le nombre de tentatives de mise en mémoire tampon, le temps nécessaire pour obtenir le premier octet à partir du premier fragment vidéo, le temps nécessaire au rendu de la première image, la longueur actuellement mise en mémoire tampon et le temps de mise en mémoire tampon. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph">mesures.<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/PlaybackLoadMetrics.html" format="html" scope="external"> PlaybackLoadMetrics</a></span> </td> 
   <td colname="2"> Fournit des informations sur le temps de chargement du média, sur le temps nécessaire au lecteur pour effectuer le rendu de la première image ou, en cas d’erreur, sur l’échec du lecteur. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph">mesures.<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/PlaybackLoadMetrics.html" format="html" scope="external"> PlaybackMetrics</a> </span></td> 
   <td colname="2"> Fournit des informations sur le comportement de la lecture. Cela inclut la fréquence d’images, le débit binaire, la longueur de la mémoire tampon, etc. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph">mesures.<a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/metrics/PlaybackSessionMetrics.html" format="html" scope="external"> PlaybackSessionMetrics</a></span> </td> 
   <td colname="2"> Fournit des informations sur le nombre de secondes que le lecteur a passées pendant la lecture et sur le temps que la vidéo a réellement passé à l’écran. </td> 
  </tr> 
  <tr rowsep="1"> 
   <td colname="1"><span class="codeph"><a href="https://help.adobe.com/en_US/primetime/api/psdk/javadoc_1.4/com/adobe/mediacore/qos/QOSProvider.html" format="html" scope="external"> QOSProvider</a></span></td> 
   <td colname="2">Fournit des mesures de qualité de service essentielles pour la lecture et le périphérique. Classe de fournisseur d’informations QOS.</td> 
  </tr> 
 </tbody> 
</table>
