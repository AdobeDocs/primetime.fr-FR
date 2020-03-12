---
description: 'null'
seo-description: 'null'
seo-title: Fonctionnalités du périphérique requises pour lire le contenu protégé
title: Fonctionnalités du périphérique requises pour lire le contenu protégé
uuid: 1490711b-65d9-4716-8779-ae1da7d2c82c
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Fonctionnalités du périphérique requises pour lire le contenu protégé {#device-capabilities-required-to-play-protected-content}

Les fonctionnalités de périphérique requises indiquent les fonctionnalités matérielles requises pour accéder au contenu. Des informations sur les fonctionnalités matérielles sont disponibles pour les périphériques qui utilisent le kit de portage.

Les attributs suivants peuvent identifier les fonctionnalités du périphérique :

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
   <td colname="3" class="- topic/entry "> <p class="- topic/p ">Correspondance exacte </p> </td> 
   <td colname="4" class="- topic/entry "> <p class="- topic/p ">Si la valeur est true, le périphérique doit avoir une racine matérielle de confiance. </p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Cette règle d’utilisation est prise en charge par les clients DRM Adobe Primetime version 2.0.2 et ultérieure. Le comportement sur les anciens clients dépend de la version minimale du client prise en charge par le serveur de licences.
>
>Voir Version [](../../../../protecting-content/setting-up-the-sdk/setup-dev-env.md)minimale du client.

