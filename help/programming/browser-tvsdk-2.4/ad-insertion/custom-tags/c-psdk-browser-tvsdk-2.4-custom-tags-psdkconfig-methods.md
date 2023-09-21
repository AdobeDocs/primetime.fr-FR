---
description: Vous pouvez configurer des noms de balise personnalisés dans un flux avec la classe MediaPlayerItemConfig .
title: Méthodes de classe de configuration pour les balises
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Méthodes de classe de configuration pour les balises{#config-class-methods-for-tags}

Vous pouvez configurer des noms de balise personnalisés dans un flux avec la classe MediaPlayerItemConfig .

Pour créer une `MediaPlayerItemConfig`:

```js
var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
```

Voici quelques informations sur la manière dont la variable `MediaPlayerItemConfig` sont utilisées pour gérer les balises personnalisées :

<table id="table_0AC0973497144DDAB05726E3F031ACD1"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>Abonnement à des balises personnalisées spécifiques</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&amp;nbsp;subscribeTagsObtained&amp;nbsp;=&amp;nbsp;mediaPlayerItemConfig.subscribeTags;
    </code> </td> 
   <td colname="col2"> <p>Récupère la liste actuelle des balises abonnées. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&nbsp;subscribeTags&nbsp;=&nbsp;["#EXT-X-PROGRAM-DATE-TIME"];mediaPlayerItemConfig.subscribeTags&nbsp;=&nbsp;subscribeTags;
    </code> </td> 
   <td colname="col2"> <p>Définit la liste des balises abonnées exposées à l’application. </p> <p>Votre application est également automatiquement abonnée à toutes les balises transmises par le biais de <span class="codeph"> adTags </span>. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>Personnaliser les balises d’annonce utilisées par le détecteur d’opportunités par défaut </b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&amp;nbsp;adTagsObtained&amp;nbsp;=&amp;nbsp;mediaPlayerItemConfig.adTags; 
    </code> </td> 
   <td colname="col2"> <p>Récupère la liste actuelle des balises publicitaires. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&nbsp;adTags&nbsp;=&nbsp;["#EXT-X-CUE"];mediaPlayerItemConfig.adTags&nbsp;=&nbsp;adTags;
    </code> </td> 
   <td colname="col2"> <p>Définit la liste des balises d’annonce à utiliser par le générateur d’opportunités par défaut. </p> </td> 
  </tr> 
 </tbody> 
</table>

Gardez à l’esprit les éléments suivants :

* Le nom de la balise personnalisée doit contenir la variable `#` préfixe.

  Par exemple : `#EXT-X-ASSET` est un nom de balise personnalisé correct, mais `EXT-X-ASSET` est incorrect.

* Vous ne pouvez pas modifier la configuration une fois le flux multimédia chargé.
