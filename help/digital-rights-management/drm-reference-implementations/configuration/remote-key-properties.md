---
description: 'null'
seo-description: 'null'
seo-title: Propriétés de la diffusion des clés distantes (iOS)
title: Propriétés de la diffusion des clés distantes (iOS)
uuid: 17e1b756-d106-47a7-99ae-641190693870
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---


# Propriétés de la diffusion des clés distantes (iOS){#remote-key-delivery-properties-ios}

Pour prendre en charge la génération de licences pour la diffusion de clés distantes à un client iOS dans Adobe Primetime DRM, vous devez spécifier le certificat du serveur de clés dans le fichier `flashaccess-refimpl.properties`.

Les propriétés suivantes ont été ajoutées dans Primetime DRM :

<table frame="all" colsep="1" rowsep="1" class="+ topic/table adobe-d/table " id="table_xz2_lwy_n4"> 
 <thead class="- topic/thead "> 
  <tr rowsep="1" class="- topic/row "> 
   <th colname="1" class="- topic/entry entry"> <p class="- topic/p ">Propriété </p> </th> 
   <th colname="2" class="- topic/entry entry"> <p class="- topic/p ">Description </p> </th> 
  </tr> 
 </thead>
 <tbody class="- topic/tbody "> 
  <tr rowsep="1" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> HandlerConfiguration.KeyServerCertificate</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Certificat serveur de licences du serveur de clés émis par Adobe. </p> <p>Ce certificat génère des licences pour les périphériques iOS lorsque les métadonnées indiquent qu’un serveur clé est requis. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry "> <p>Alias du certificat serveur de licences émis par Adobe d'un serveur de clés qui est stocké sur HSM. </p> <p>Lorsque vous activez HSM, vous pouvez appliquer cette propriété au lieu de la propriété <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span>. </p> </td> 
  </tr> 
 </tbody> 
</table>

