---
description: Vous pouvez configurer globalement les noms de balises personnalisés dans TVSDK avec la classe MediaPlayerItemConfig ou en fonction du flux avec la classe MediaPlayerItemConfig .
title: Méthodes de classe de configuration pour les balises
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Méthodes de classe de configuration pour les balises{#config-class-methods-for-tags}

Vous pouvez configurer globalement les noms de balises personnalisés dans TVSDK avec la classe MediaPlayerItemConfig ou en fonction du flux avec la classe MediaPlayerItemConfig .

TVSDK applique automatiquement la configuration globale à tout flux multimédia qui ne spécifie aucune configuration spécifique au flux.

Les deux `PSDKConfig` et `MediaPlayerItemConfig` exposer ces méthodes pour gérer les balises personnalisées :

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="1"><b>Abonnement à des balises personnalisées spécifiques</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> fonction publique get subscribeTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2"> Récupère la liste actuelle des balises abonnées. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> fonction publique set subscribeTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2">Définit la liste des balises abonnées qui seront exposées à l’application. <p>Votre application est également automatiquement inscrite à toutes les balises transmises par le biais de <span class="codeph"> adTags</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1"><b>Personnaliser les balises d’annonce utilisées par le détecteur d’opportunités par défaut </b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> fonction publique get adTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2"> Récupère la liste actuelle des balises publicitaires. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> fonction publique set adTags():Vector.&lt;String&gt;</span> </td> 
   <td colname="col2"> Définit la liste des balises d’annonce qui seront utilisées par le générateur d’opportunités par défaut. </td> 
  </tr> 
 </tbody> 
</table>

Gardez à l’esprit les éléments suivants :

* Les méthodes setter ne permettent pas au paramètre tags de contenir des valeurs null.

  En cas de problème, TVSDK renvoie une `IllegalArgumentException`.
* Le nom de la balise personnalisée doit contenir le préfixe # .

  Par exemple : `#EXT-X-ASSET` est un nom de balise personnalisé correct, mais `EXT-X-ASSET` est incorrect.
* Vous ne pouvez pas modifier la configuration une fois le flux multimédia chargé.
