---
description: Vous pouvez configurer les noms de balises personnalisées dans TVSDK globalement avec la classe MediaPlayerItemConfig ou en flux continu avec la classe MediaPlayerItemConfig.
title: Config des méthodes de classe pour les balises
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# Configurez les méthodes de classe pour les balises {#config-class-methods-for-tags}

Vous pouvez configurer les noms de balises personnalisées dans TVSDK globalement avec la classe MediaPlayerItemConfig ou en flux continu avec la classe MediaPlayerItemConfig.

TVSDK applique automatiquement la configuration globale à tout flux média qui ne spécifie pas de configuration spécifique au flux.

`PSDKConfig` et `MediaPlayerItemConfig` exposent ces méthodes pour gérer les balises personnalisées :

<table id="table_B37A6C75270D47BC99258F2884AD6905"> 
 <tbody> 
  <tr> 
   <td colname="1"><b>S’abonner à des balises personnalisées spécifiques</b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> fonction publique get subscriTags():Vector.&lt;string&gt;</span> </td> 
   <td colname="col2"> Récupère la liste actuelle des balises abonnées. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> public, fonction set subscriptionTags():Vector.&lt;string&gt;</span> </td> 
   <td colname="col2">Définit la liste des balises abonnées qui seront exposées à l’application. <p>Votre application est également automatiquement abonnée à toutes les balises transmises par le biais de <span class="codeph"> adTags</span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="1"><b>Personnaliser les balises publicitaires utilisées par le détecteur d'opportunités par défaut  </b> </td> 
   <td colname="3"> </td>
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> fonction publique get adTags():Vector.&lt;string&gt;</span> </td> 
   <td colname="col2"> Récupère la liste actuelle des balises publicitaires. </td> 
  </tr> 
  <tr> 
   <td colname="col1"><span class="codeph"> fonction publique set adTags():Vector.&lt;string&gt;</span> </td> 
   <td colname="col2"> Définit la liste des balises publicitaires qui seront utilisées par le générateur d’opportunités par défaut. </td> 
  </tr> 
 </tbody> 
</table>

Souvenez-vous des points suivants :

* Les méthodes setter n’autorisent pas le paramètre de balises à contenir des valeurs nulles.

   S’il est rencontré, TVSDK lance un `IllegalArgumentException`.
* Le nom de la balise personnalisée doit contenir le préfixe #.

   Par exemple, `#EXT-X-ASSET` est un nom de balise personnalisé correct, mais `EXT-X-ASSET` est incorrect.
* Vous ne pouvez pas modifier la configuration après le chargement du flux média.

