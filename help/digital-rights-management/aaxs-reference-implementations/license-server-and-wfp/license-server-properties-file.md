---
title: Fichier de propriétés du serveur de licences
description: Fichier de propriétés du serveur de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Fichier de propriétés du serveur de licences {#license-server-properties-file}

Utilisez la variable [!DNL flashaccess-refimpl.properties] pour configurer le composant Serveur de licences de l’implémentation de référence. Veillez à configurer au minimum les propriétés liées aux informations d’identification de transport et aux informations d’identification du serveur de licences. Les emplacements des fichiers d’informations d’identification doivent être spécifiés par rapport au répertoire spécifié par la variable `config.resourcesDirectory` . Ce fichier contient également plusieurs propriétés liées au contenu de package : ces propriétés ne sont utilisées que pour la conversion des métadonnées Flash Media Rights Management Server 1.x. Si vous modifiez l’une des valeurs de ce fichier de propriétés, vous devez redémarrer le serveur de licences pour que les modifications soient prises en compte.

Pour prendre en charge la génération de licences pour la diffusion de clé à distance aux clients iOS dans Adobe Access, le certificat du serveur de clé doit être spécifié dans [!DNL flashaccess-refimpl.properties].

Les propriétés suivantes ont été ajoutées dans Adobe Access :

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
   <td colname="2" class="- topic/entry "> Certificat du serveur de licences du serveur de clés, émis par Adobe. Ce certificat est utilisé pour générer des licences pour les appareils iOS, lorsque les métadonnées indiquent qu’un serveur de clés est requis. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry ">Alias du certificat de serveur de licences émis par Adobe par le serveur de clés stocké sur HSM. Lorsque HSM est activé, utilisez cette propriété au lieu de <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span>. </td> 
  </tr> 
 </tbody> 
</table>
