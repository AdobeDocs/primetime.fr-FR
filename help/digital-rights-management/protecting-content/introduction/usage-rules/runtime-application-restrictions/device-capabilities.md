---
title: Fonctionnalités de l’appareil requises pour lire du contenu protégé
description: Fonctionnalités de l’appareil requises pour lire du contenu protégé
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Fonctionnalités de l’appareil requises pour lire du contenu protégé {#device-capabilities-required-to-play-protected-content}

Les fonctionnalités de périphérique requises spécifient les fonctionnalités matérielles requises pour accéder au contenu. Des informations sur les fonctionnalités matérielles sont disponibles pour les appareils qui utilisent le kit de portage.

Les attributs suivants peuvent identifier les fonctionnalités de l’appareil :

<table id="table_v3n_fks_n4"> 
 <tbody> 
  <tr> 
   <td><b>Attribut</b> </td> 
   <td><b>Valeurs prises en charge</b> </td> 
   <td><b>Critères de correspondance</b> </td> 
   <td><b>Description</b> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Bus accessible aux non-utilisateurs </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true" ou "false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">Correspondance exacte </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">Si la valeur est true, l’appareil ne doit pas comporter de bus accessible à l’utilisateur. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Racine matérielle de la confiance </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true" ou "false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">Correspondance exacte </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">Si la valeur est true, le périphérique doit avoir une racine matérielle de confiance. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Cette règle d’utilisation est prise en charge par les clients DRM Adobe Primetime version 2.0.2 et ultérieure. Le comportement sur les clients plus anciens dépend de la version client minimale prise en charge par le serveur de licences.
>
>Voir [Version minimale du client](../../../../protecting-content/setting-up-the-sdk/setup-dev-env.md).
