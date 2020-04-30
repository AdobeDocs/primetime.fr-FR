---
seo-title: Fonctionnalités de l'appareil requises pour lire le contenu protégé
title: Fonctionnalités de l'appareil requises pour lire le contenu protégé
uuid: 16ed73d9-e02f-4c86-bf15-2d3e7122bf5a
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

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

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Cette règle d’utilisation est prise en charge par les clients Adobe Access versions 2.0.2 et ultérieures. Le comportement des clients plus anciens dépend de la version minimale du client prise en charge par le serveur de licences. Voir Version [](../../../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md)minimale du client.

