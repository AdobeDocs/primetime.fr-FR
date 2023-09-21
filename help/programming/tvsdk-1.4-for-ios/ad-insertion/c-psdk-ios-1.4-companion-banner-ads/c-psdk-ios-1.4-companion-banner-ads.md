---
description: TVSDK prend en charge les bannières publicitaires connexes, qui accompagnent une publicité linéaire et restent souvent sur la page après la fin de la publicité linéaire. Votre application est responsable de l’affichage des bannières compagnons fournies avec une publicité linéaire.
title: Bannières publicitaires d’accompagnement
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# Bannières publicitaires d’accompagnement {#companion-banner-ads}

TVSDK prend en charge les bannières publicitaires connexes, qui accompagnent une publicité linéaire et restent souvent sur la page après la fin de la publicité linéaire. Votre application est responsable de l’affichage des bannières compagnons fournies avec une publicité linéaire.

Lors de l’affichage des publicités compagnons, procédez comme suit :

* Essayez de présenter autant de bannières publicitaires d’accompagnement que vous le souhaitez dans la disposition de votre lecteur.
* Présenter une bannière compagnon uniquement si vous disposez d’un emplacement correspondant exactement à sa hauteur et largeur spécifiées.

  >[!TIP]
  >
  >Ne redimensionnez pas la bannière.

* Présenter la ou les bannières d’accompagnement dès que possible après le début de la publicité.
* Ne superposez pas le conteneur publicitaire/vidéo principal avec les bannières compagnons.
* Continuez à afficher les bannières compagnons une fois la publicité terminée.

  La norme consiste à afficher chaque bannière compagnon jusqu’à ce que vous ayez un remplacement pour cette bannière.

## Companion banner data {#companion-banner-data}

Le contenu d’une ressource PTAdAsset décrit une bannière compagnon.

<!--<a id="section_D730B4FD6FD749E9860B6A07FC110552"></a>-->

La variable `PTMediaPlayerAdStartedNotification` la notification renvoie une `PTAd` qui contient une instance `companionAssets` property (tableau de `PtAdAsset`).
Chaque `PtAdAsset` fournit des informations sur l’affichage de la ressource.

<table id="table_760C885E2DCA4BE983CC57FDA7BD5B14"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> Informations disponibles </th> 
   <th colname="col2" class="entry"> Description </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> width </td> 
   <td colname="col2"> Largeur de la bannière compagnon en pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> height </td> 
   <td colname="col2"> Hauteur de la bannière compagnon en pixels. </td> 
  </tr> 
  <tr> 
   <td colname="col1"> type de ressource </td> 
   <td colname="col2">Type de ressource pour cette bannière compagnon : 
    <ul id="ul_A067787FE49E4B6095BE0AC1D447DBB3"> 
     <li id="li_02B7224C67004095B3F6E50FD21E507E">html : les données se trouvent dans le code du HTML. </li> 
     <li id="li_5F37E14472424F808C6094F42009E676">iframe : les données sont une URL iframe (src). </li> 
     <li id="li_76B945007CE842158B5125422765E0B2">static : les données sont une staticURL qui est une URL directe vers une image. </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> data </td> 
   <td colname="col2"> Les données du type spécifié par <span class="codeph"> resourceType</span> pour cette bannière compagnon. </td> 
  </tr> 
 </tbody> 
</table>

## Afficher les bannières publicitaires {#display-banner-ads}

Pour afficher les bannières publicitaires, vous devez créer des instances de bannière et permettre à TVSDK d’écouter les événements liés aux publicités.

TVSDK fournit une liste des bannières publicitaires associées à une publicité linéaire par le biais de la variable `PTMediaPlayerAdPlayStartedNotification` événement de notification .

Les manifestes peuvent spécifier des bannières publicitaires d’accompagnement en :

* Fragment de HTML
* URL d’une page iFrame
* URL d’une image statique ou d’un fichier de SWF de Flash Adobe

Pour chaque publicité compagnon, TVSDK indique les types disponibles pour votre application.

1. Créez un `PTAdBannerView`  pour chaque emplacement publicitaire compagnon de votre page.

       Assurez-vous que les informations suivantes ont été fournies :
   
   * Pour empêcher la récupération des publicités compagnons de tailles différentes, une instance de bannière qui spécifie la largeur et la hauteur.
   * Taille standard des bannières.

1. Ajoutez un observateur pour la fonction `PTMediaPlayerAdStartedNotification` qui effectue les opérations suivantes :
   1. Efface les publicités existantes dans l’instance de bannière.
   1. Récupère la liste des publicités compagnons à partir de `Ad.getCompanionAssets` `PTAd.companionAssets`.
   1. Si la liste des publicités d’accompagnement n’est pas vide, passez la souris sur la liste pour les instances de bannière.

      Chaque instance de bannière ( a `PTAdAsset`) contient des informations, telles que la largeur, la hauteur, le type de ressource (html, iframe ou statique), ainsi que les données requises pour afficher la bannière compagnon.
   1. Si une publicité vidéo ne comporte aucune publicité compagnon enregistrée, la liste des ressources compagnons ne contient aucune donnée pour cette publicité vidéo.

      Pour afficher une publicité d’affichage autonome, ajoutez la logique à votre script afin d’exécuter une balise d’affichage publicitaire standard DFP (DoubleClick for Publishers) dans l’instance de bannière appropriée.
   1. Envoie les informations sur la bannière à une fonction de votre page qui affiche les bannières à un emplacement approprié.

      Il s’agit généralement d’une `div`, et votre fonction utilise la fonction `div ID` pour afficher la bannière. Par exemple :

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
