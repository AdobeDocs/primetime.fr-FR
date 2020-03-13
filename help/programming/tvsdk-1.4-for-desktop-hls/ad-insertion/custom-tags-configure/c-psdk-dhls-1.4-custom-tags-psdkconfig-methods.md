---
description: Vous pouvez configurer les noms de balises personnalisées dans TVSDK globalement avec la classe MediaPlayerItemConfig ou en flux continu avec la classe MediaPlayerItemConfig.
seo-description: Vous pouvez configurer les noms de balises personnalisées dans TVSDK globalement avec la classe MediaPlayerItemConfig ou en flux continu avec la classe MediaPlayerItemConfig.
seo-title: Méthodes de classe Config pour les balises
title: Méthodes de classe Config pour les balises
uuid: 3317fc8b-c13c-4e7d-8334-aa8cdf40fa05
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661

---


# Méthodes de classe Config pour les balises{#config-class-methods-for-tags}

Vous pouvez configurer les noms de balises personnalisées dans TVSDK globalement avec la classe MediaPlayerItemConfig ou en flux continu avec la classe MediaPlayerItemConfig.

TVSDK applique automatiquement la configuration globale à tout flux média qui ne spécifie aucune configuration spécifique au flux.

Les deux méthodes `PSDKConfig` et `MediaPlayerItemConfig` exposent ces méthodes pour gérer les balises personnalisées :

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="1"><b>S’abonner à des balises personnalisées spécifiques</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> fonction publique get subscriTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2"> Récupère le  actuel des balises abonnées. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public, fonction set subscriptionTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2">Définit le  des balises abonnées qui seront exposées à l’application. <p>Votre application est également automatiquement abonnée à toutes les balises transmises par le biais de <span class="codeph"> balises</span>publicitaires. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1"><b>Personnaliser les balises publicitaires utilisées par le détecteur d'opportunités par défaut </b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> fonction publique get adTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2"> Récupère le  actuel des balises publicitaires. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> fonction publique set adTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2"> Définit le  des balises publicitaires qui seront utilisées par le générateur d’opportunités par défaut. </td> 
  </tr> 
 </tbody> 
</table>

Tenez compte des points suivants :

* Les méthodes setter ne permettent pas au paramètre de balise de contenir des valeurs null.

   S’il est rencontré, TVSDK renvoie un message `IllegalArgumentException`.
* Le nom de la balise personnalisée doit contenir le préfixe #.

   Par exemple, `#EXT-X-ASSET` est un nom de balise personnalisé correct, mais `EXT-X-ASSET` incorrect.
* Vous ne pouvez pas modifier la configuration une fois le flux média chargé.

