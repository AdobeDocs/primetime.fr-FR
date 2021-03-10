---
title: Fonctionnalités de l'appareil requises pour lire le contenu protégé
description: Fonctionnalités de l'appareil requises pour lire le contenu protégé
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---


# Fonctionnalités de l&#39;appareil requises pour lire le contenu protégé {#device-capabilities-required-to-play-protected-content}

Spécifie les capacités matérielles requises pour accéder au contenu. Des informations sur les fonctionnalités matérielles sont disponibles pour les périphériques qui utilisent le kit de portage.

Les capacités du périphérique peuvent être identifiées par les attributs spécifiés dans le tableau suivant :

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
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">Si la valeur est true, le périphérique ne doit pas disposer d’un bus accessible à l’utilisateur. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1" class="- topic/entry "> <p class="- topic/p ">Racine matérielle de la confiance </p> </td> 
   <td colname="2" class="- topic/entry "> <p class="- topic/p ">"true" ou "false" </p> </td> 
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">Macro exacte </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">Si la valeur est true, le périphérique doit avoir une racine matérielle de confiance. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Cette règle d&#39;utilisation est prise en charge par les clients Adobe Access version 2.0.2 et ultérieure. Le comportement des clients plus anciens dépend de la version minimale du client prise en charge par le serveur de licences. Voir [Version minimale du client](../../../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md).

