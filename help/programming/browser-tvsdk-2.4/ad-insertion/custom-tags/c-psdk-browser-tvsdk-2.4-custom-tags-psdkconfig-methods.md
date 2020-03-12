---
description: Vous pouvez configurer des noms de balises personnalisés dans un flux à l’aide de la classe MediaPlayerItemConfig.
seo-description: Vous pouvez configurer des noms de balises personnalisés dans un flux à l’aide de la classe MediaPlayerItemConfig.
seo-title: Méthodes de classe Config pour les balises
title: Méthodes de classe Config pour les balises
uuid: 222a0349-58d5-4bf3-9d03-e5920610faf5
translation-type: tm+mt
source-git-commit: b9e98ef2b4246fdfd79ebcd91db344c97367d661

---


# Méthodes de classe Config pour les balises{#config-class-methods-for-tags}

Vous pouvez configurer des noms de balises personnalisés dans un flux à l’aide de la classe MediaPlayerItemConfig.

To create a new `MediaPlayerItemConfig`:

```js
var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
```

Voici quelques informations sur l’utilisation des `MediaPlayerItemConfig` méthodes pour gérer les balises personnalisées :

<table id="table_0AC0973497144DDAB05726E3F031ACD1"> 
 <tbody> 
  <tr> 
   <td colname="col1"> <b>S’abonner à des balises personnalisées spécifiques</b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&amp;nbsp;subscribeTagsObtained&amp;nbsp;=&amp;nbsp;mediaPlayerItemConfig.subscribeTags;
    </code> </td> 
   <td colname="col2"> <p>Récupère le  actuel des balises abonnées. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&nbsp;subscribeTags&nbsp;=&nbsp;["#EXT-X-PROGRAM-DATE-TIME"];mediaPlayerItemConfig.subscribeTags&nbsp;=&nbsp;subscribeTags;
    </code> </td> 
   <td colname="col2"> <p>Définit le  des balises abonnées exposées à l’application. </p> <p>Votre application est également automatiquement abonnée à toutes les balises transmises par le biais de <span class="codeph"> balises </span>publicitaires. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <b>Personnaliser les balises publicitaires utilisées par le détecteur d'opportunités par défaut </b> </td> 
   <td colname="col2"> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&amp;nbsp;adTagsObtained&amp;nbsp;=&amp;nbsp;mediaPlayerItemConfig.adTags; 
    </code> </td> 
   <td colname="col2"> <p>Récupère le  actuel des balises publicitaires. </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> 
    <code class="syntax javascript">
      var&nbsp;adTags&nbsp;=&nbsp;["#EXT-X-CUE"];mediaPlayerItemConfig.adTags&nbsp;=&nbsp;adTags;
    </code> </td> 
   <td colname="col2"> <p>Définit le  des balises publicitaires à utiliser par le générateur d’opportunités par défaut. </p> </td> 
  </tr> 
 </tbody> 
</table>

Tenez compte des points suivants :

* Le nom de la balise personnalisée doit contenir le `#` préfixe.

   Par exemple, `#EXT-X-ASSET` est un nom de balise personnalisé correct, mais `EXT-X-ASSET` incorrect.

* Vous ne pouvez pas modifier la configuration une fois le flux média chargé.

