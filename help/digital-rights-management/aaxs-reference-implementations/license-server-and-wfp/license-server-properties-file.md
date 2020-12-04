---
seo-title: Fichier de propriétés du serveur de licences
title: Fichier de propriétés du serveur de licences
uuid: bede307a-2060-451f-baf5-d058702c0a7e
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Fichier de propriétés du serveur de licences {#license-server-properties-file}

Utilisez le fichier [!DNL flashaccess-refimpl.properties] pour configurer le composant License Server de l&#39;implémentation de référence. Au minimum, veillez à configurer les propriétés liées aux informations d&#39;identification de transport et aux informations d&#39;identification du serveur de licences. Les emplacements des fichiers d’informations d’identification doivent être spécifiés par rapport au répertoire spécifié par la propriété `config.resourcesDirectory`. Ce fichier contient également plusieurs propriétés liées au contenu d’assemblage : ces propriétés ne sont utilisées que pour la conversion des métadonnées Flash Media Rights Management Server 1.x. Si vous modifiez l’une des valeurs de ce fichier de propriétés, vous devez redémarrer le serveur de licences pour que les modifications prennent effet.

Pour prendre en charge la génération de licences pour la diffusion de clés distantes pour les clients iOS dans Adobe Access, le certificat du serveur de clés doit être spécifié dans [!DNL flashaccess-refimpl.properties].

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
   <td colname="2" class="- topic/entry "> Certificat du serveur de licences du serveur de clés, émis par Adobe. Ce certificat est utilisé pour générer des licences pour les périphériques iOS, lorsque les métadonnées indiquent qu’un serveur clé est requis. </td> 
  </tr> 
  <tr rowsep="0" class="- topic/row "> 
   <td colname="1" class="- topic/entry "><span class="codeph"> RefImpl.HSM.HandlerConfiguration.\ KeyServerCertificate.Alias</span> </td> 
   <td colname="2" class="- topic/entry ">Alias du certificat de serveur de licences émis par Adobe par Key Server stocké sur HSM. Lorsque HSM est activé, utilisez cette propriété au lieu de <span class="codeph"> HandlerConfiguration.KeyServerCertificate</span>. </td> 
  </tr> 
 </tbody> 
</table>

