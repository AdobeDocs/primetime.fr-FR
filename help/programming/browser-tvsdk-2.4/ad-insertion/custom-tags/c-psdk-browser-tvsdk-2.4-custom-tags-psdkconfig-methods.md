---
description: Vous pouvez configurer des noms de balises personnalisés dans un flux à l’aide de la classe MediaPlayerItemConfig.
title: Config des méthodes de classe pour les balises
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# Configurez les méthodes de classe pour les balises {#config-class-methods-for-tags}

Vous pouvez configurer des noms de balises personnalisés dans un flux à l’aide de la classe MediaPlayerItemConfig.

Pour créer `MediaPlayerItemConfig` :

```js
var mediaPlayerItemConfig = new AdobePSDK.MediPlayerItemConfig();
```

Voici quelques informations sur l&#39;utilisation des méthodes `MediaPlayerItemConfig` pour gérer les balises personnalisées :

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
   <td colname="col1"> <b>Personnaliser les balises publicitaires utilisées par le détecteur d'opportunités par défaut  </b> </td> 
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
   <td colname="col2"> <p>Définit la liste des balises publicitaires à utiliser par le générateur d’opportunités par défaut. </p> </td> 
  </tr> 
 </tbody> 
</table>

Souvenez-vous des points suivants :

* Le nom de la balise personnalisée doit contenir le préfixe `#`.

   Par exemple, `#EXT-X-ASSET` est un nom de balise personnalisé correct, mais `EXT-X-ASSET` est incorrect.

* Vous ne pouvez pas modifier la configuration après le chargement du flux média.

