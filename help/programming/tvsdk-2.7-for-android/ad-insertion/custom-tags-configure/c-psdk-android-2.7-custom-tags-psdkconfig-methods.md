---
description: Vous pouvez configurer globalement les noms de balises personnalisées dans TVSDK avec la classe MediaPlayerItemConfig.
seo-description: Vous pouvez configurer globalement les noms de balises personnalisées dans TVSDK avec la classe MediaPlayerItemConfig.
seo-title: Config des méthodes de classe pour les balises
title: Config des méthodes de classe pour les balises
uuid: 64284876-1f31-47e0-a99b-3bfe17e10707
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Config des méthodes de classe pour les balises {#config-class-methods-for-tags}

Vous pouvez configurer globalement les noms de balises personnalisées dans TVSDK avec la classe MediaPlayerItemConfig.

TVSDK applique automatiquement la configuration globale à tout flux média qui ne spécifie aucune configuration spécifique au flux.

`MediaPlayerItemConfig` expose les méthodes suivantes pour gérer les balises personnalisées :

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>S’abonner à des balises personnalisées spécifiques</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> chaîne finale publique[] getSubscribedTags </span> </td> 
   <td colname="col2"> <p>Récupère la liste actuelle des balises abonnées. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setSubscribedTags(String[] tags); </span> </td> 
   <td colname="col2"> <p>Définit la liste des balises abonnées qui seront exposées à l’application. </p> <p>Votre application est également automatiquement abonnée à toutes les balises transmises via <span class="codeph"> setAdTags </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>Personnaliser les balises publicitaires utilisées par le détecteur d'opportunités par défaut</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final String[] getAdTags; </span> </td> 
   <td colname="col2"> <p>Récupère la liste actuelle des balises publicitaires. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <span class="codeph"> public final void setAdTags(String[] tags); </span> </td> 
   <td colname="col2"> <p>Définit la liste des balises publicitaires qui seront utilisées par le générateur d’opportunités par défaut. </p> </td> 
  </tr> 
 </tbody> 
</table>

Souvenez-vous des points suivants :

* Les méthodes setter n’autorisent pas le paramètre de balises à contenir des valeurs nulles.

   S’il est détecté, TVSDK lance un `IllegalArgumentException`jeton.
* Le nom de la balise personnalisée doit contenir le `#` préfixe.

   Par exemple, `#EXT-X-ASSET` est un nom de balise personnalisé correct, mais `EXT-X-ASSET` incorrect.

* Vous ne pouvez pas modifier la configuration après le chargement du flux média.
