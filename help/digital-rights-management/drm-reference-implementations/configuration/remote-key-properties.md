---
title: Propriétés de diffusion à clé distante (iOS)
description: Propriétés de diffusion à clé distante (iOS)
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---

# Propriétés de diffusion à clé distante (iOS){#remote-key-delivery-properties-ios}

Pour prendre en charge la génération de licences pour la diffusion de clé à distance à un client iOS dans Adobe Primetime DRM , vous devez spécifier le certificat de serveur de clé dans la variable `flashaccess-refimpl.properties` fichier .

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
   <td colname="2" class="- topic/entry "> <p>Certificat du serveur de licences de clé émis par Adobe. </p> <p>Ce certificat génère des licences pour les appareils iOS lorsque les métadonnées indiquent qu’un serveur de clés est requis. </p> </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry "> <p>L’alias du certificat de serveur de licences émis par un Adobe par un serveur de clés, stocké sur HSM. </p> <p>Lorsque vous activez HSM, vous pouvez appliquer cette propriété au lieu de la propriété <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span> . </p> </td> 
  </tr> 
 </tbody> 
</table>
