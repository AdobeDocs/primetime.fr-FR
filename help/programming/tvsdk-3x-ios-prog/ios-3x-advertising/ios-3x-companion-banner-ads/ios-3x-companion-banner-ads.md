---
description: TVSDK prend en charge les bannières publicitaires complémentaires, qui sont des publicités qui accompagnent une publicité linéaire et qui restent souvent sur la page après la fin de la publicité linéaire. Votre application est responsable de l'affichage des bannières d'accompagnement fournies avec une publicité linéaire.
title: Bannières publicitaires d’accompagnement
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---


# Bannières publicitaires d’accompagnement {#companion-banner-ads}

TVSDK prend en charge les bannières publicitaires complémentaires, qui sont des publicités qui accompagnent une publicité linéaire et qui restent souvent sur la page après la fin de la publicité linéaire. Votre application est responsable de l&#39;affichage des bannières d&#39;accompagnement fournies avec une publicité linéaire.

Lors de l’affichage des publicités complémentaires, suivez ces recommandations :

* Tentez de présenter autant de bannières publicitaires d’accompagnement d’une publicité vidéo que vous le souhaitez dans la mise en page de votre lecteur.
* Présentez une bannière d’accompagnement uniquement si vous disposez d’un emplacement correspondant exactement à sa hauteur et largeur spécifiées.

   >[!TIP]
   >
   >Ne redimensionnez pas la bannière.

* Présentez la ou les bannières d’accompagnement dès que possible après le début de la publicité.
* N’incrustez pas le conteneur publicitaire/vidéo principal avec les bannières d’accompagnement.
* Continuez à afficher les bannières d’accompagnement une fois la publicité terminée.

   La norme consiste à afficher chaque bannière d’accompagnement jusqu’à ce que vous ayez un remplaçant pour cette bannière.

## Données de bannière d’accompagnement {#companion-banner-data}

Le contenu d’un fichier PTAdAsset décrit une bannière connexe.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

La notification `PTMediaPlayerAdStartedNotification` renvoie une instance `PTAd` contenant une propriété `companionAssets` (tableau de `PtAdAsset`).
Chaque `PtAdAsset` fournit des informations sur l&#39;affichage de la ressource.

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"><b>Informations disponibles</b></th> 
   <th colname="col2" class="entry"><b>Description</b></th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> width </td> 
   <td colname="col2"> Largeur de la bannière d’accompagnement en pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> hauteur </td> 
   <td colname="col2"> Hauteur de la bannière d’accompagnement en pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> type de ressource </td> 
   <td colname="col2">Type de ressource pour cette bannière complémentaire : 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html : Les données sont en code HTML. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe : Les données sont une URL iframe (src). </li> 
     <li id="li_76B945007CE842158B5125422765E0B2">static: Les données sont un staticURL qui est une URL directe vers une image. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> data </td> 
   <td colname="col2"> Données du type spécifié par <span class="codeph">resourceType</span> pour cette bannière d'accompagnement. </td> 
  </tr> 
 </tbody> 
</table>

## Afficher les bannières publicitaires {#display-banner-ads}

Pour afficher des bannières publicitaires, vous devez créer des instances de bannière et autoriser TVSDK à écouter les événements liés aux publicités.

TVSDK fournit une liste de bannières publicitaires associées associées à une publicité linéaire via le événement de notification `PTMediaPlayerAdPlayStartedNotification`.

Les manifestes peuvent spécifier des bannières publicitaires complémentaires en :

* Un extrait de code HTML
* URL d’une page iFrame
* URL d’une image statique ou d’un fichier SWF de Flash d’Adobe

Pour chaque publicité connexe, TVSDK indique les types disponibles pour votre application.

1. Créez une instance `PTAdBannerView` pour chaque emplacement publicitaire secondaire sur votre page.

       Assurez-vous que les informations suivantes ont été fournies :
   
   * Pour empêcher la récupération des publicités complémentaires de différentes tailles, une instance de bannière qui spécifie la largeur et la hauteur.
   * Taille standard des bannières.

1. Ajoutez un observateur pour le `PTMediaPlayerAdStartedNotification` qui effectue les tâches suivantes :
   1. Efface les publicités existantes dans l’instance de bannière.
   1. Obtient la liste des publicités complémentaires de `Ad.getCompanionAssets` `PTAd.companionAssets`.
   1. Si la liste des publicités complémentaires n’est pas vide, effectuez une itération sur la liste pour les instances de bannière.

      Chaque instance de bannière ( `PTAdAsset`) contient des informations telles que la largeur, la hauteur, le type de ressource (html, iframe ou static) et les données requises pour afficher la bannière correspondante.
   1. Si une publicité vidéo ne comporte aucune publicité connexe, la liste des ressources d’accompagnement ne contient aucune donnée pour cette publicité vidéo.

      Pour afficher une publicité d’affichage autonome, ajoutez la logique à votre script afin d’exécuter une balise d’affichage publicitaire standard DFP (DoubleClick for Publishers) dans l’instance de bannière appropriée.
   1. Envoie les informations de la bannière à une fonction de votre page qui affiche les bannières à l’emplacement approprié.

      Il s&#39;agit généralement d&#39;un `div` et votre fonction utilise le `div ID` pour afficher la bannière. Par exemple :

      ```
      - (void) onMediaPlayerAdPlayStarted:(NSNotification *) notification { 
          _currentAd  = [notification.userInfo  objectForKey:PTMediaPlayerAdKey];  
          if (_currentAd != nil) { 
              [self removeAllBanners]; // remove any existing PTAdBannerView views 
      
              // banners 
              if (_currentAd.companionAssets && _currentAd.companionAssets.count > 0) { 
                  PTAdAsset *bannerAsset = [_currentAd.companionAssets objectAtIndex:0]; 
      
                  PTAdBannerView *bannerView = [[PTAdBannerView alloc] initWithAsset:bannerAsset];  
                  bannerView.player = self.player; 
                  bannerView.delegate = self; 
      
                  bannerView.frame = CGRectMake(0.0, 0.0, bannerAsset.width, bannerAsset.height);  
                  [_adBannerView.bannerView addSubview:bannerView]; 
              } 
          } 
      }
      ```
