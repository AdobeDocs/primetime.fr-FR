---
title: Notes de mise à jour de Browser TVSDK 2.4
description: Les notes de mise à jour de Browser TVSDK 2.4 décrivent les nouvelles fonctionnalités, les fonctionnalités prises en charge et non prises en charge, ainsi que les problèmes connus de Browser TVSDK 2.4.
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '6812'
ht-degree: 0%

---

# Notes de mise à jour de Browser TVSDK 2.4 {#browser-tvsdk-release-notes}

Les notes de mise à jour de Browser TVSDK 2.4 décrivent les nouvelles fonctionnalités, les fonctionnalités prises en charge et non prises en charge, ainsi que les problèmes connus de Browser TVSDK 2.4.

## Introduction {#introduction}

Browser TVSDK est une boîte à outils qui vous permet d’ajouter des fonctionnalités de lecture vidéo, une protection de contenu et de la publicité avancées à vos applications de lecteur vidéo basées sur un navigateur.

Le navigateur TVSDK 2.4 fournit des API JavaScript pour créer des applications vidéo basées sur un navigateur et inclut la prise en charge de la lecture dans les modes suivants :

* HTML5 uniquement
* HTML5 avec secours Flash automatique
* Flash toujours

Cette version comprend les informations suivantes :

・ [Documentation de l’API Browser TVSDK](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

・ [Guide de programmation du navigateur TVSDK](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_browser-tvsdk.pdf).

・ [Guide de migration TVSDK pour la version 1.4 DHLS vers Browser TVSDK 2.4](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html).

・ [Conversion de Browser TVSDK 2.4.6 à la version 2.4.7](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-246-to-247-for-javascript.html).

・ Une implémentation de référence, qui est incluse dans la version.

>[!NOTE]
>
>*Pour obtenir la liste complète des considérations relatives à la sécurité de cette version, voir Considérations relatives à la sécurité.

## Nouveautés et fonctionnalités prises en charge {#what-s-new-and-supported-features}

Cette version de Browser TVSDK fournit de nouvelles fonctionnalités que vous pouvez utiliser pour améliorer vos applications vidéo.

**Nouveautés de la mise à jour 2.4.12 (Build 204)**

L’ajout suivant est disponible dans le cadre de la mise à jour Browser TVSDK 2.4.12 (Build 204) :

* L’implémentation de l’API de volume d’AdobePSDK.MediaPlayer est modifiée afin d’autoriser la lecture automatique sur iOS lorsque la lecture est en mode muet.

・ Une nouvelle API, `auditudeSettings.ignoreVPAIDAds`, est ajouté pour permettre d’ignorer les publicités VPAID reçues du serveur Auditude. L’API ne fonctionne pas pour le Flash de secours.

**Version 2.4.11**

Les améliorations et ajouts suivants sont disponibles dans la version 2.4.11 de Browser TVSDK :

・ Le basculement de segment HLS Live est pris en charge pour les modes de secours MSE et Flash.

・ Prise en charge de `AuditudeSettings.creativeRepackagingDomain` L’API est désormais disponible pour MSE également. Auparavant, il n’était pris en charge qu’avec le mode de secours Flash.

・ Cette version contient des correctifs pour les problèmes critiques des clients. Voir *Problèmes résolus* une liste.

**Version 2.4.10**

Les améliorations et ajouts suivants sont disponibles dans la version 2.4.10 de Browser TVSDK :

・ TVSDK fournit enableLogging() pour activer ou désactiver la journalisation. Voir [Documentation de l’API](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)pour l’utilisation de .

・ TVSDK ne prend plus en charge les chapitres par défaut lorsque vous utilisez Adobe Analytics. Définissez et gérez des chapitres à l’aide de votre application.

・ Cette version contient des correctifs pour les problèmes critiques des clients. Voir *Problèmes résolus *une liste.

**Version 2.4.9**

Les améliorations et ajouts suivants sont disponibles dans la version 2.4.9 de Browser TVSDK :

・ Les diffusions HLS VOD et Live avec discontinuité dans le temps mais sans marqueurs de discontinuité sont prises en charge.

・ Les images ID3 v2.4.0 sont prises en charge avec la balise vidéo Safari pour les flux VOD HLS et Live.

・ La mise en oeuvre sécurisée du chargement des publicités garantit que les appels au serveur de publicités sont mis à niveau pour sécuriser le HTTP en fonction de la configuration de l’API. Pour plus d’informations, voir les classes AdobePSDK.AdvertisingMetadata et AdobePSDK.ForceHttpsAdConfiguration . Cette fonctionnalité n’est pas prise en charge en mode de secours par Flash.

・ Les informations d’identifiant de l’annonce et d’extension associées aux réponses VAST 3.0 sont désormais mises à la disposition de l’application par TVSDK et peuvent être utilisées pour mettre en oeuvre l’intégration de la souris pour les mesures publicitaires. Pour plus d’informations, voir API AdobePSDK.NetworkAdInfo . Ceci n’est pas pris en charge en mode de secours par Flash.

・ La classe AdobePSDK.ForceHttpsConfiguration n’est plus disponible. Il est remplacé par

Classe AdobePSDK.ForceHttpsAdConfiguration .

・ Une nouvelle API, AdobePSDK.optimizeFlashCalls, est désormais disponible pour optimiser les appels afin d’améliorer l’expérience de lecture HLS en mode de secours par Flash. Cette option est désactivée par défaut.

**Nouveautés de la mise à jour 2.4.8 (Build 6002)**

Cette mise à jour contient des correctifs pour les problèmes critiques des clients. Voir *Problèmes résolus*, pour la liste.

**Version 2.4.8**

Les améliorations et ajouts suivants sont disponibles dans la version 2.4.8 de Browser TVSDK :

・ Le SDK est désormais conforme à l’EME de Chrome et les bonnes pratiques changent à partir de Chrome v58. Pour plus d’informations, voir [https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf](https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf)**

・ La structure de l’interface utilisateur prend désormais en charge le DRM d’accès HLS sur le Flash, la publicité uniquement et le workflow Informations de ciblage.

・ L’API setDRMAuthenticateData est ajoutée à l’interface utilisateur. Pour lire des flux protégés par Adobe Access DRM, appelez cette API. L’attribut drmAuthenticateData peut également être spécifié dans le lecteur. Voir [AdobePSDK.videoBehavior](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/VideoBehavior.html)pour plus d’informations.

**Version 2.4.7**

Les fonctionnalités suivantes sont nouvelles dans la version 2.4.7 :

・ Ajout du configurateur de l’interface utilisateur dans l’interface utilisateur

Vous pouvez configurer le lecteur de l’une des manières suivantes :

・ Utilisation d’un objet JSON

・ Utilisation des API

Pour faciliter la génération de l’objet JSON, le navigateur TVSDK fournit un outil **Configurateur de l’interface utilisateur**.

Dans cet outil, vous pouvez sélectionner différents paramètres, cliquer sur **Tester la configuration **pour vérifier les paramètres, puis sur **Télécharger la configuration ** pour télécharger les paramètres. Après avoir téléchargé le fichier, vous pouvez transmettre le contenu de ce fichier sous la forme d’objet JSON à l’API ptp.videoPlayer.

・ Ajout de l’API MediaPlayerItemConfig à l’interface utilisateur

Plusieurs fonctionnalités, notamment advertisingMetadata, advertisingFactory, adSignalingMode, networkConfiguration, customRangeMetadata, useHardwareDecoder, subscribeTags, adTags, thumbnailScrubber, billingMetricsConfiguration, peuvent être configurées via MediaPlayerItemConfig. Pour plus d’informations, voir la documentation AdobePSDK.MediaPlayerItemConfig dans la section [API Browser TVSDK](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)* * [documentation](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

Dans la structure de l’interface utilisateur, la manière de transmettre des configurations réseau via la configuration du lecteur a été modifiée.

**Version 2.4.6**

`var player = ptp.videoPlayer(‘#videoHolder', {`

`player: {`

`networkConfiguration: <network configuration object>`

`}`

`};`

**Version 2.4.7**

`var player = ptp.videoPlayer(‘#videoHolder', {`

`player: {`

`mediaPlayerItemConfig: {`

`networkConfiguration: <network configuration object>`

`}`

`}`

`};`

* Prise en charge des processus DRM et Analytics dans l’interface utilisateur

Les configurations DRM et le suivi Analytics peuvent être activés par le biais de l’interface utilisateur.

* Ajout de `AdobePSDK.embedSWFinFullScreenDiv` API

Cette nouvelle API offre une certaine flexibilité à l’application de lecteur pour sélectionner la balise div dans laquelle elle peut incorporer le fichier FlashFallback.swf.

* Remplacé `getVersion`API de `AdobePSDK.MediaPlayer` classe avec `AdobePSDK.Version` classe pour les informations relatives à la version TVSDK. Pour plus d’informations, voir `AdobePSDK.Version` API [here](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.Version.html).

**Version 2.4.6**

Les fonctionnalités suivantes sont nouvelles dans la version 2.4.6 :

* **Prise en charge de la navigation**

Browserify vous permet d’utiliser les modules de style node.js dans le navigateur. Vous pouvez définir les dépendances et parcourir les lots dans un seul fichier JavaScript.

* **Facturation**

Grâce à la facturation, le navigateur TVSDK peut collecter des mesures d’utilisation du lecteur pour facturer les clients Primetime.

>[!NOTE]
>
>L’énumération obsolète MediaPlayer.Events et les constantes obsolètes dans Enum PSDKErrorCode ont été supprimées dans la version 2.4.6. Pour plus d’informations, voir [Conversion de Browser TVSDK 2.4.5 à la version 2.4.6](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-245-to-246-for-javascript.html).

**Version 2.4.5**

Les fonctionnalités suivantes sont nouvelles dans la version 2.4.5 :

* **Lectures et publicités complètes d’événements**

  Les diffusions HLS Full Event Replay (FER) prennent désormais en charge la résolution de publicité et les comportements publicitaires. Pour activer cette prise en charge, définissez le mode de signalisation de la publicité sur `MANIFEST_CUES` lors de la création de la variable `MediaPlayerItemConfig` .

* **Prise en charge de ScalePolicy par MediaplayerView**

  Les développeurs d’applications peuvent désormais spécifier une propriété scalePolicy différente pour la vue à l’aide de la propriété scalePolicy de MediaPlayerView .

* **Prise en charge du contenu anamorphique**

  La lecture du contenu anamorphique est désormais prise en charge lors de l’utilisation de la lecture MSE et par Flash.

* **Application sélective de`withCredentials`**

When `withCredentials` est défini sur true, la variable `Access-Control-Allow-Origin` ne peut pas être défini sur un caractère générique. Selon la réponse du serveur, le navigateur TVSDK définit de manière sélective la variable `withCredentials` attribut. Pour plus d’informations sur cette prise en charge, voir [Documentation de l’API TVSDK du navigateur](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

**Version 2.4.4**

Les nouvelles fonctionnalités suivantes ont été ajoutées à la version 2.4.4 :

* **Exemple d’application Chromecast**

Cette version fournit la prise en charge d’une application d’expéditeur et de récepteur qui illustre la lecture des flux VOD DASH et des flux Wi-Fi DASH avec insertion de publicités côté client.

* **Prise en charge avancée du basculement**

Cette version prend en charge les cas d’utilisation de basculement avancé (basculement de segment et de serveur) pour les flux VOD HLS.

**Version 2.4.3**

Les nouvelles fonctionnalités suivantes ont été ajoutées à la version 2.4.3 :

* **Balises personnalisées pour DASH VOD**

  Les balises personnalisées intégrées (événements) peuvent être abonnées à et reçues en tant qu’objet TimedMetadata.

* **Lecture des diffusions sans extensions**

  Les flux HLS et DASH sans extensions sont désormais pris en charge. Pour le fichier de manifeste, le paramètre resourceType doit être spécifié lors du chargement de la ressource. Pour les segments et les fichiers VTT, l’en-tête de réponse Content-Type est utilisé pour déterminer le type de contenu.

**Version 2.4.2**

Les nouvelles fonctionnalités suivantes ont été ajoutées à la version 2.4.2 :

* **Parité de l’API**

Pour obtenir la liste complète de la parité API, voir la section [Guide de migration TVSDK pour la version 1.4 DHLS vers Browser TVSDK 2.4](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html).

* **Prise en charge d’Sample-AES**

  Cette version ajoute la prise en charge de la lecture de contenu chiffré Sample-AES sur MSE et la version de secours de Flash. L’obligation d’héberger le contenu AES sur une origine sécurisée sur Google Chrome a été supprimée.

* **Prise en charge des conteneurs AAC**

  La lecture des fichiers avec l’extension .aac est désormais prise en charge. Il peut s’agir de diffusions audio uniquement ou de fichiers audio alternatifs.

  >[!NOTE]
  >
  >Les codecs AC3 et AC3 améliorés ne sont pas encore pris en charge.

* **Lecture de flux jetée**

Les flux HLS diffusés par le biais d’un réseau de diffusion de contenu (CDN) peuvent parfois utiliser des jetons d’authentification sur les demandes de manifeste et de segment à vérifier, et ces jetons peuvent être fournis en tant que paramètres d’URL ou en tant qu’en-têtes de cookie. La lecture de ces flux est désormais prise en charge.

**Version 2.4.1**

Les nouvelles fonctionnalités suivantes ont été ajoutées à la version 2.4.1 :

* **Structure de l’IU**

Cette structure, conçue pour accélérer le développement de l’interface utilisateur pour les applications de lecteur vidéo basées sur JavaScript, comprend des API permettant d’inclure des commandes de base telles que la lecture/pause et le volume, ainsi que d’ajouter ou de supprimer facilement des éléments tels que les états de la barre de défilement et les paramètres de sous-titres fermés. Vous pouvez spécifier le comportement associé aux contrôles, créer des contrôles personnalisés et appliquer un habillage à l’interface utilisateur du lecteur. Tout cela se fait par le biais de la structure, sans qu’il soit nécessaire de manipuler directement la structure DOM.

* **Améliorations de la lecture HLS pour les flux en direct**

Cette version prend en charge les discontinuités causées par l’insertion d’annonces. Elle utilise la balise EXT-PROGRAM-DATE-TIME suivie de la balise EXT-MEDIA-SEQUENCE pour synchroniser les profils de débit adaptatif en vue d’une lecture fluide.

* **Prise en charge de VPAID 2.0**

La version 2.0 de la définition de l’interface de service publicitaire du lecteur vidéo (VPAID) offre une expérience multimédia enrichie aux utilisateurs et permet aux éditeurs de mieux cibler les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo. Cette version prend en charge les annonces VPAID JavaScript linéaires pour le contenu vidéo à la demande (VOD).

* **Balises HLS personnalisées**

Les diffusions multimédia peuvent comporter des métadonnées supplémentaires sous la forme de balises dans le fichier playlist/manifest. TVSDK du navigateur vous permet de spécifier et de vous abonner à des balises supplémentaires et d’être averti lorsque ces balises apparaissent dans le manifeste.

* **Marqueurs publicitaires affichés dans la chronologie du lecteur**

Cette version prend en charge l’affichage des marqueurs publicitaires dans la chronologie du lecteur pour le contenu VOD et en direct. Vous pouvez voir ce comportement dans le lecteur de référence.

**Pris en charge dans 2.4**

Les fonctionnalités suivantes étaient disponibles dans la version 2.4 :

* **Lecture audio MP3**

  Cette version prend en charge la lecture audio MP3 sur les navigateurs utilisant les extensions Media Source (MSE) et la balise vidéo Safari.

* **Lecture vidéo MP4**

  Les fonctionnalités suivantes sont prises en charge :

   * Lecture en continu unique
   * Publicités MP4 preroll et Post-roll avec comportements publicitaires et suivi
   * Publicités HLS preroll et Post-roll avec comportements publicitaires et suivi
   * Publicités DASH preroll et Post-roll avec comportements publicitaires et suivi

## Plateformes prises en charge {#supported-platforms}

Le SDK du navigateur présente des exigences spécifiques pour les niveaux de plateformes et de logiciels sur lesquels il doit s’exécuter. Les plateformes et les niveaux logiciels suivants sont pris en charge :

### Configurations de bureau {#desktop-configurations}

* Microsoft Windows 7 :

   * Internet Explorer 11+
   * Chrome 33+
   * Firefox 38+

* Microsoft Windows 8.1

   * Internet Explorer 11+
   * Chrome 33+
   * Firefox 38+

* Microsoft Windows 10

   * Edge+

* APPLE OS X

   * Safari 9+
   * Chrome 33+
   * Firefox 38+

### Configurations web mobiles {#mobile-web-configurations}

* Android 4.4

   * Navigateur natif
   * Chrome 33+

* Android 5.0

   * Navigateur natif
   * Chrome 33+

* Android 6.0

   * ・ Chrome 33+

* APPLE IOS 9

   * Safari 9+
   * Chrome 33+

* Apple iOS 10

   * Safari 9+
   * Chrome 33+

**Google Chromecast (deuxième génération ; pour la lecture DASH uniquement)**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Technologie</strong> </p> </td> 
   <td><p><strong>Balise vidéo du navigateur TVSDK</strong><sup>1</sup></p> </td> 
   <td><p><strong>Browser TVSDK MSE</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>Technologie par défaut</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>iOS</p> </td> 
   <td><p>MP4 et HLS</p> </td> 
   <td><p>-</p> </td> 
   <td><p>-</p> </td> 
   <td><p>Balise vidéo</p> </td> 
  </tr> 
  <tr> 
   <td><p>Android</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS et DASH</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
  <tr> 
   <td><p>Apple Safari 8</p> </td> 
   <td><p>MP4 et HLS</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MP4 et HLS</p> </td> 
   <td><p>Balise vidéo</p> </td> 
  </tr> 
  <tr> 
   <td><p>Google Chrome</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS et DASH</p> </td> 
   <td><p>MP4 et HLS</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
  <tr> 
   <td><p>Mozilla Firefox</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS et DASH</p> </td> 
   <td><p>MP4 et HLS</p> </td> 
   <td><p>MSE<sup>2</sup></p> </td> 
  </tr> 
  <tr> 
   <td><p>Internet Explorer 11</p> <p>(Windows 7)</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>-</p> </td> 
   <td><p>MP4 et HLS</p> </td> 
   <td><p>Flash</p> </td> 
  </tr> 
  <tr> 
   <td><p>Internet Explorer 11</p> <p>(Windows 8.1)</p> </td> 
   <td><p>MP4</p> </td> 
   <td><p>HLS, DASH</p> </td> 
   <td><p>MP4 et HLS</p> </td> 
   <td><p>MSE</p> </td> 
  </tr> 
 </tbody> 
</table>

## Matrice de fonctionnalités {#feature-matrix}

Voici la liste des fonctionnalités prises en charge et non prises en charge pour cette version :

* *Fonctionnalités audio MP3 — Lecture principale*
* *Fonctionnalités vidéo MP4 — Lecture principale*
* *Fonctionnalités vidéo MP4 — Ad Insertion principal*

>[!NOTE]
>
>*Dans les tableaux de la matrice des fonctionnalités ci-dessous, un &quot;Y&quot; signifie que la fonctionnalité est prise en charge dans la version actuelle.*

### Fonctionnalités audio MP3 {#mp-audio-features}

**Tableau 1 : Lecture principale{#table-core-playback}**

| Catégorie | Type de contenu | Fonctionnalité | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Lecture | MP3 VOD | Lecture générale (Lecture, Pause, Recherche) | Non pris en charge | Y | Y |

1 La balise Browser TVSDK Video ne prend pas en charge la diffusion en continu et DRM. La prise en charge du codec et du conteneur n’est pas la même dans tous les navigateurs.

2 Firefox est défini par défaut sur Flash Player pour la version 41 ou antérieure.

### Fonctionnalités audio MP4 {#mp-audio-features-1}

**Tableau 2 : Lecture principale**

| Catégorie | Type de contenu | Fonctionnalité | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Lecture | MP4 VOD | Lecture générale (Lecture, Pause, Recherche) | Non pris en charge | Y | Y |

**Tableau 3 : Ad Insertion principal**

| Catégorie | Type de contenu | Fonctionnalité | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | MP4 VOD | preroll (MP4) | Non pris en charge | Y | Y |
| Ad Insertion | MP4 VOD | Post-roll (MP4) | Non pris en charge | Y | Y |

Pour plus d’informations sur la prise en charge des fonctionnalités HLS ou DASH, voir ci-dessous.

## Matrice des fonctionnalités HLS {#hls-feature-matrix}

Voici la matrice des fonctionnalités des fonctionnalités HLS dans Browser TVSDK.

* *Lecture principale HLS*
* *Fonctionnalités de lecture avancées HLS*
* *Fonctionnalités de protection de contenu HLS*
* *Fonctionnalités d’insertion des publicités principales HLS*
* *Fonctionnalités d’insertion de publicités avancées HLS*
* *Intégrations HLS*

>[!NOTE]
>
>*Dans les tableaux de la matrice des fonctionnalités ci-dessous, un &quot;Y&quot; signifie que la fonctionnalité est prise en charge dans la version actuelle.*

### Fonctionnalités HLS {#hls-features}

Les fonctionnalités suivantes sont prises en charge :

**Tableau 4 : Lecture principale HLS**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Catégorie</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5 : Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Lecture générale (lecture, pause, recherche)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Lecture générale (lecture, pause et recherche)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Débit adaptatif</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>légendes 608/708</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>WebVTT</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>VOD uniquement</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Basculement du manifeste</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Basculement avancé</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Notifications QoS et du lecteur</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Prise en charge limitée de QoS</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Prise en charge des en-têtes de cookie</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Définition des paramètres de contrôle de la mémoire tampon</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Définir la variable adaptative</p> <p>contrôles de débit binaire</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Balises personnalisées</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td>Liaison audio tardive</td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>302 redirect</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 5. Fonctionnalités de lecture avancée HLS**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Catégorie</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5 : Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Lecture au décalage</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Lecture audio seule</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Lecture de la carte</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Lecture de la mbox</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Analyse d’ID3</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Prise en charge des marqueurs de discontinuité</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Flux jetés</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Facturation</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 6. Fonctionnalités de protection du contenu HLS**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Catégorie</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5 : Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Protection du contenu</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>AES-128</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Protection du contenu</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Sample-AES</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Protection du contenu</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>Accès aux Adobes</p> </td> 
   <td><p>Non pris en charge</p> </td> 
   <td><p>FairPlay</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 7 : Fonctionnalités principales d’insertion de publicités HLS**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Catégorie</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5 : Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>preroll (MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Mid-roll (HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Post-roll (MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Résolution et comportements des publicités</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Stratégie de publicité par défaut</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>VAST 2.0/3.0</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Creative Repackaging (MP4 vers HLS)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 8 : fonctions avancées d’insertion de publicités HLS**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Catégorie</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5 : Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Publicité uniquement</p> </td> 
   <td><p>Non pris en charge</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Paramètres de ciblage</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Paramètres personnalisés</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Stratégie d’annonce personnalisée</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Chargement différé des publicités</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Non pris en charge</p> </td> 
   <td><p>Limitation de la plateforme</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Publicités d’accompagnement, bannières publicitaires, publicités cliquables</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>VPAID 2.0</p> </td> 
   <td><p>SWF</p> </td> 
   <td><p>JavaScript</p> </td> 
   <td><p>JavaScript</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 9 : Intégrations HLS{#table-hls-integrations}**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Catégorie</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5 : Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Intégrations</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Intégration d’Adobe Analytics VHL</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## Matrice des fonctionnalités DASH {#dash-feature-matrix}

Voici la matrice des fonctionnalités des fonctions DASH dans le navigateur TVSDK.

・ *Fonctionnalités de lecture principale DASH*

・ *Fonctionnalités de lecture avancées DASH*

・ *Fonctionnalités de protection du contenu DASH*

・ *Fonctionnalités d’insertion des publicités principales DASH*

・ *Fonctionnalités d’insertion de publicités avancées DASH*

・ *Intégrations DASH*

>[!NOTE]
>
>Dans les tableaux de la matrice des fonctionnalités ci-dessous, un Y signifie que la fonctionnalité est prise en charge dans la version actuelle.

### Fonctionnalités DASH {#dash-features}

Les fonctionnalités suivantes sont prises en charge :

**Tableau 10 : fonctions de lecture principale de DASH**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Catégorie</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>HTML5 FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Lecture générale (lecture, pause, recherche)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Lecture générale (lecture, pause et recherche)</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Débit adaptatif</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>légendes 608/708</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>WebVTT</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Basculement</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Notifications QoS et du lecteur</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Prise en charge des en-têtes de cookie</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Définition des paramètres de contrôle de la mémoire tampon</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Définition des contrôles de débit adaptatif</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Balises personnalisées (EventStream)</p> </td> 
   <td><p>VOD uniquement (intégré)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Audio liée en retard</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>302 redirect</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 11 : Fonctionnalités de lecture avancées de DASH**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Catégorie</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><strong>HTML5 FF, IE, Chrome, Android Chrome</strong></td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Lecture au décalage</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Lecture audio seule</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Lecture de piste</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Lecture de la mbox</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Analyse d’ID3</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Prise en charge sur plusieurs périodes</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Flux jetés</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Facturation</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 12 : Fonctionnalités de protection du contenu DASH**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Catégorie</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>HTML5 FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Protection du contenu</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>AES-128</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Protection du contenu</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Sample-AES</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Protection du contenu</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>・ Widevine sous Chrome, Firefox 47 et versions ultérieures, et Chromecast</p> <p>・ PlayReady sur Internet Explorer sous Windows 8.1 et Edge</p> <p>・ Primetime DRM pour Windows Firefox (vidéo uniquement)</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 13 : Fonctionnalités principales d’insertion de publicités dans DASH**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Catégorie</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>HTML5 FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>preroll (MP4/DASH)</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Mid-roll (DASH)</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Post-roll (MP4/DASH)</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Résolution et comportement des publicités</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Stratégie de publicité par défaut</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>VAST 2.0/3.0</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Creative Repackaging (MP4 vers DASH)</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 14 : Fonctionnalités avancées d’insertion de publicités DASH**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Catégorie</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>HTML5</strong> FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Publicité uniquement</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Paramètres de ciblage</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Paramètres personnalisés</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Stratégie d’annonce personnalisée</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Chargement différé des publicités</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Publicités d’accompagnement, bannières publicitaires, publicités cliquables</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ad Insertion</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>VPAID 2.0</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 15 : Intégrations DASH**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Catégorie</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Intégrations</p> </td> 
   <td><p>VOD + En direct</p> </td> 
   <td><p>Intégration d’Adobe Analytics VHL</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## Problèmes résolus {#issues-fixed}

**Problèmes résolus dans la mise à jour 2.4.12 (Build 204)**

Les problèmes suivants ont été corrigés dans la mise à jour 2.4.12 de Browser TVSDK (Build 204) :

・ **21647**- TVSDK doit permettre la lecture vidéo automatique sur les appareils iOS lorsque l’audio est coupé.

・ **21465**- Clé d’erreur L’accès au système refusé est reçu lors de la lecture d’un flux DASH protégé par DRM après la lecture d’un flux DASH en direct.

・ **21442**- Activez la lecture automatique du contenu sur le web iOS, après la lecture de la publicité preroll avec un geste de l’utilisateur.

・ **21240**- API fournie pour filtrer les publicités VPAID analysées à partir d’Auditude/VMAP.

**Problèmes résolus dans la version 2.4.11**

Les problèmes suivants ont été corrigés dans la version 2.4.11 de Browser TVSDK :

**Fonctionnalités de lecture principale :**

・ **19192**: TVSDK implémente désormais TextFormat:bottomInset et TextFormat:safeArea. En raison de ces améliorations, les sous-titres fermés peuvent être repositionnés si la barre de contrôle s’affiche à l’écran.

・ **21009**: les sous-titres codés persistent à l’écran en cas de recherche par-delà la discontinuité jusqu’à ce que de nouvelles sous-titres apparaissent.

・ **21141**: la recherche en amont est rejetée en raison d’une condition de concurrence lors de l’ajout du segment.

・ **21142**: rend disponibles les plages de lecture pouvant être consultées lorsque le lecteur est à l’état INITIALISÉ. En raison de ces modifications, la session de démarrage en position est désormais prise en charge.

・ **21363**: 608/708 sous-titres fermés ne sont plus synchronisés après l’insertion de publicités pour les flux DASH.

**Fonctionnalités d’insertion d’annonces :**

・ **21179**: les problèmes liés au mid-roll (longues pauses, images noires) avec le contenu VOD sont désormais résolus en définissant correctement la propriété ad.primaryAsset.adParameters .

・ **21257**: le fichier MP4 avec le débit le plus élevé est sélectionné pour le transcodage si MP4 n’est pas un type MIME valide et que la fonction de reconditionnement créatif est activée.

・ **21361**: TVSDK transmet désormais le système publicitaire et l’identifiant créatif de la réponse VAST en tant que paramètres de requête dans la demande de package créatif afin de prendre en charge des règles de normalisation supplémentaires.

**Problèmes résolus dans la version 2.4.10**

Les problèmes suivants ont été corrigés dans la version 2.4.10 de Browser TVSDK :

**Fonctionnalités de lecture principale :**

・ **21060**: erreur de codec non valide générée avec les flux HLS qui contiennent une discontinuité et les boîtes BMFF ISO s’exécutent à la fin de la diffusion.

・ **21045**: la lecture automatique ne fonctionne pas sur iOS une fois la première lecture vidéo de la liste de lecture terminée.

・ **20975**: le débit d’image est renvoyé en tant que NaN par le fournisseur QoS sur le navigateur Chrome.

・ **20823**: erreur de codec non prise en charge générée lors de la rencontre de segments sans données.

・ **20769**: le SDK commence désormais par le débit en cours à la recherche au lieu de basculer immédiatement en fonction de la stratégie ABR.

・ **20031**: lorsque le mode portrait est activé sur IE11 (Windows 8.1), l’écran vidéo devient petit. Fonctionnalité de protection du contenu :

・ **19316**: ignorez les segments qui ne parviennent pas à décrypter en cas de flux HLS AES-128.

**Problèmes résolus dans la version 2.4.9**

Les problèmes suivants ont été corrigés dans la version 2.4.9 de Browser TVSDK :

**Fonctionnalités de lecture principale :**

・ **13407**: les flux DASH peuvent se bloquer si Firefox cesse d’envoyer l’événement &quot;ontimeupdate&quot; pendant la lecture.

・ **16380**: lors de la lecture de contenu audio-vidéo composite de segments dont les heures de début ne correspondent pas via MSE, l’erreur de synchronisation audio entre les représentations s’accumule sur les commutateurs ABR, ce qui entraîne en fin de compte une erreur (problème Chromium #663686).

・ **17985**: lors de la lecture d’un flux ISO-BMFF particulier sur le navigateur Firefox, la lecture se bloque (problème Firefox #1342913). Ce problème a été corrigé depuis Firefox v53.

・ **19141**: Non intercepté (en promesse) ReferenceError : la largeur n’est pas définie.

・ **18997, 1929**: problème de scintillement vidéo à la limite du segment. Cela se produisait car le SDK ne calculait pas correctement le décalage temporel de la dernière composition de l’échantillon.

・ **19780**: la lecture ne démarre pas pour le contenu HLS et la publicité HLS dans Firefox v53 (problème Firefox #354653).

・ **20046**: Date/heure du programme est reçue en tant que clé au lieu de la valeur lorsqu’elle est reçue en tant qu’objet de métadonnées minuté.

・ **20047**: useDefaultResizeHandler renvoie une erreur avec le Flash de secours.

・ **20179**: Flash de la reprise ne fonctionne pas avec le Flash Player v25.0.0.171.

・ **20293**: Firefox arrête la mise en mémoire tampon des données de certains flux HLS menant à un blocage.

・ **20626**: le lecteur renvoie une erreur de décodage multimédia sur Chrome en raison d’une gestion incorrecte des exemples vidéo sans durée.

・ **20078**: blocage de lecture sur l’erreur de navigateur &quot;QuotaExceeded&quot;.

・ **18639**: dans le flux HLS Live 608 CC, le texte semble parfois mal orthographié.

・ **20028**: le paramètre de taille ClosedCaptions ne modifie pas la taille de police.

・ **20613**: les zones de sous-titres codés se chevauchent, ce qui les rend illisibles.

**Fonctionnalités de l’Ad Insertion principal :**

・ **20043**: appels d’impression de publicité et de suivi des publicités manquants avec plusieurs publicités et redirections tierces.

・ **2044**: lors de l’utilisation d’un reconditionnement créatif, toutes les publicités de la coupure publicitaire doivent être reconditionnées avec succès. Dans le cas contraire, la coupure publicitaire est complètement ignorée.

・ **20097**: la lecture de la publicité est ignorée et le contenu principal reprend immédiatement au lieu d’attendre le délai d’attente de 20 secondes si le manifeste de publicité n’est pas disponible.

**Problèmes résolus dans la mise à jour de la version 2.4.8 (build 6002)**

Les problèmes suivants ont été corrigés dans la mise à jour de Browser TVSDK version 2.4.8 (Build 6002) :

・ **14126 :** La lecture peut bloquer Firefox (problème #1316024) en raison d’un vide interne dans la mémoire tampon source MSE. Tentative de recherche pour reprendre la lecture

・ **19608 :** Correctif pour honorer la valeur de décalage temporel de la réponse VMAP Auditude.

・ **19635 :** Correction du blocage vidéo dans Internet Explorer 11 sous Windows 10.

・ **19761 :** Correctifs de problèmes ABR avec HLS.

・ **19780 :** Correction de la lecture de la publicité avec du contenu HLS rompu dans Mozilla Firefox v53.

・ **1987 et 1974 :** Les problèmes corrigent l’incohérence de la sélection du débit après une opération de recherche. Désormais, la sélection du débit lors de la recherche correspond à la valeur inférieure du débit actuel et du débit au démarrage.

・ **1981 :** La lecture est bloquée et la mise en mémoire tampon s’affiche pendant un temps infini une fois la recherche effectuée entre 3 et 4 fois.

・ **19884 :** Confirmez la conformité aux exigences de Chrome 59 bêta vérifiée Media Path (VMP). bTVSDK a pu lire le contenu DRM Widevine avec Chrome 59 bêta.

・ **19916 :** La lecture DRM sur UI-Framework a été interrompue. Désormais, il appelle acquireLicense même s’il n’existe aucune stratégie dans les métadonnées.

**Problèmes résolus dans la version 2.4.8**

Les problèmes suivants ont été corrigés dans la version 2.4.8 de Browser TVSDK :

・ **10075**: lorsque vous effectuez une recherche en amont de la chronologie, l’événement de fin de lecture n’a pas été reçu dans Firefox et Chrome et l’événement de recherche n’a pas été reçu dans Firefox.

・ **15775**: Lire l’événement complete non reçu sur Windows 8.1 Internet Explorer.

・ **17306**: pour les flux SSAI, la lecture est prise en charge. Le suivi de la publicité groupée n’est pas pris en charge.

・ **19142**: parfois le retour en arrière entraîne le maintien ininterrompu de l’état de mise en mémoire tampon du lecteur vidéo.

・ **19218**: les marqueurs d’annonce ne sont pas disponibles via la structure de l’interface utilisateur.

・ **19219**: la lecture des publicités ne fonctionne pas uniquement via la structure de l’interface utilisateur.

・ **1922**: la clé AES-128 est demandée une fois pour une liste de lecture et les demandes suivantes sont diffusées à partir du cache. Auparavant, il était demandé pour chaque segment.

・ **19597**: &quot;Uncaught TypeError: Cannot read property &#39;log&#39; of undefined&quot; (erreur de type non interceptée : impossible de lire la propriété &quot;log&quot; d’indéfinie) a été visualisé avec les versions de canari Chrome.

・ **1960**: adRequestDomain n’était pas disponible en mode Flash de secours.

・ **19608**: les publicités VMAP n’étaient pas insérées pour les flux HLS Live. Le SDK prend désormais en compte les marqueurs de repère et ne dépend pas des valeurs de décalage temporel dans les réponses VMAP.

・ **1963**: la lecture des publicités entraîne uniquement une erreur de script à la fin de la publicité.

・ **19732**: les demandes de liste de lecture CRS échouaient avec une erreur 404. Les demandes 1401 et 1403 du Browser TVSDK sont désormais mises à jour pour prendre en charge ce problème.

・ **19762**: acquisitionLicense utilisée pour être appelée avant setAuthenticationToken en en raison de laquelle une licence valide a été renvoyée, quelle que soit la validité du jeton. Ce problème a été corrigé maintenant et acquireLicense n’est appelé qu’après la réponse setAuthenticationToken .

**Problèmes résolus dans la version 2.4.7**

Les problèmes suivants ont été corrigés dans la version 2.4.7 :

・ **8397**: les flux HLS Live générés par l’Adobe Media Server peuvent ne pas être lus si les segments ne commencent pas par un cadre de clé.

・ **13606**: plusieurs problèmes liés à la recherche ont été corrigés pour le flux HLS sur le navigateur Chrome.

・ **14807**: sur le navigateur Chrome, si la recherche ou la mise en pause est déclenchée immédiatement après la fonction play(), la lecture peut s’arrêter avec l’erreur DOMException : la requête play() a été interrompue par un appel...(Problème Chromium# 593273).

・ **19085**: les paramètres MediaPlayer tels que volume, abrControlParameters et ccStyle ne sont pas définis sur Valeurs par défaut lors de la réinitialisation du lecteur.

**Problèmes résolus dans la version 2.4.6**

Le problème suivant a été corrigé dans la version 2.4.6 :

・ **18093**: les métadonnées de la balise en regard de la balise abonnée sont renvoyées lorsque vous utilisez la version 24 du Flash Player en mode de secours par Flash.

**Problèmes résolus dans la version 2.4.4**

Les problèmes suivants ont été corrigés dans la version 2.4.4 :

・ **8711**: avec MSE, 608/708 légendes sont conservées par défaut.

・ **13934**: les paramètres ABR pour les publicités ne s’appliquent pas lors de la lecture avec des flux HLS Live.

・ **14079**: la longévité des diffusions HLS Live avec une faible fenêtre de réalité virtuelle peut échouer, car la lecture peut être en retard en raison de problèmes de latence du réseau. Cliquez sur le point d’activation pour reprendre la lecture.

・ **15037**: les exemples fournis avec la structure de l’interface utilisateur du lecteur ne fonctionnent pas sur Microsoft Internet Explorer 10 sous Windows 7.

・ **15913**: pour les flux VOD HLS, dans Chrome, le flux ne se lance pas si la réponse du manifeste est 304 et n’est pas modifiée. Ce problème est résolu depuis Chrome v55 (problème Chromium 633696).

・ **16103**: sur Android Chrome, dans des conditions de bande passante faible, la lecture peut bloquer avec la propriété Uncaught TypeError: Cannot read property ’programDateTime’ of undefined error.

・ **16265**: pour les flux VOD HLS et Live, la recherche entre discontinuités ne fonctionne pas.

・ **16709**: la reprise du flux HLS Live avec PDT et le marqueur de discontinuité peuvent entraîner un blocage du lecteur dans la mise en mémoire tampon.

## Problèmes connus et limites {#known-issues-and-limitations}

Les limites et les problèmes connus du SDK du navigateur sont mentionnés ci-dessous.

**Tableau 16 : Fonctionnalités de lecture principales**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Type de contenu</strong></td> 
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML5 dans Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 dans Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (lecture DASH uniquement)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Lecture générale (Lecture, Pause, Recherche)</td> 
   <td><p>・ Les formats multimédias autres que HLS ne sont pas pris en charge.</p> <p>8799 : Le Flash de secours ne prend pas en charge le contenu mixte. Il est donc nécessaire de s’assurer que le contenu, l’annonce et les autres URL ne génèrent pas de contenu mixte (contenu sécurisé et non sécurisé ensemble).</p> <p>・ 19271 : la lecture multi-view via l’interface utilisateur n’est pas prise en charge en mode de secours par Flash.</p> <p>・ Le Flash de secours ne fonctionne pas sur Microsoft Internet Explorer 8 et 9 sous Windows 7, car ces versions ne sont pas prises en charge par le SDK.</p> <p>・ 20262 : le Flash de secours ajoute des paramètres personnalisés à la liste d’informations de ciblage. L’ordre de priorité des paramètres personnalisés est également différent en cas de Flash et de MSE.</p> <p>・ 20653 : La reprise du Flash Browser TVSDK ne fonctionne pas sur Win10 avec la mise à jour Creators.</p> <p>・ Flash de secours fonctionne avec Flash Player version 23 et ultérieure.</p> <p>・ 20087 - Chrome 59 bêta avec</p> <p>Flash 25.0.0.171</p> <p>Version bêta (par défaut), la lecture HLS ne fonctionne pas en mode Flash de secours. Ça marche bien sur Canary.</p> </td> 
   <td><p>・ 12563 : Les flux de mémoire avec codec audio mp4a.40.02 ne sont pas lus sur Firefox en raison d’une chaîne de codec audio non prise en charge dans MPD. Le codec audio mp4a.40.2 est pris en charge.</p> <p>15029 : Lors du passage d’une vidéo à l’autre dans multiView dans l’interface utilisateur-Framework, le bouton de lecture/pause n’est pas mis à jour en conséquence.</p> <p>・ 16034 : sous Windows 8.1 IE, l’appel de reset() entraîne une erreur de type MIME inconnu. Rechargez le média pour reprendre la lecture.</p> <p>・ 18235 : certains problèmes de recherche sont observés avec les flux de vod DASH avec des publicités.</p> <p>・ 18727 : L’API d’erreur n’est pas prise en charge pour MSE</p> <p>18750 : les événements de changement d’état peuvent être dans l’ordre dans certains cas pour le SDK et la structure de l’interface utilisateur. Dans le framework de l’interface utilisateur, les événements IDLE et Initialisation de l’étatChange peuvent être manquants pour les écouteurs d’événement ajoutés après le chargement de la ressource.</p> <p>・ 18889 : Si MediaPlayer est à l’état ERROR, l’objet view n’est pas renvoyé.</p> <p>・ 19039 : si AdobePSDK. MediaPlayer. La fonction searchToLocal() est utilisée avec une valeur supérieure à EOF, puis la lecture commence à partir du début dans le cas de MSE.</p> <p>・ 19049 : aucun état d’erreur n’est signalé pour le Flash Player sur Chrome, IE, Firefox lorsque la vidéo est bloquée pendant la lecture.</p> <p>・ 17205 : La lecture vidéo se bloque sur la lecture d’un flux non muet pendant quelques heures tandis que la lecture audio continue (numéro Chromium 664033).</p> <p>・ 12308 : les flux DASH avec composition_time_offset spécifié peuvent avoir timeStampOffset appliqué sur le navigateur Chrome, ce qui entraîne une heure de décodage négative et donc MEDIA_ERR_SRC_NOT_ Erreur PRISE en charge (problème Chromium #398141).</p> <p>・ 14126 : la lecture peut bloquer Firefox (numéro 1316024) en raison d’un écart interne dans la mémoire tampon source MSE. Essayez de rechercher pour reprendre la lecture.</p> <p>・ 19115 : MS Edge et IE 11 (Win 8.1 et 10) ne définit pas Origin sur null lors de la redirection CORS et échoue, car l’en-tête n’est pas nul, ce qui entraîne une erreur de lecture.</p> <p>・ 19861 : problème lié au comportement d’ajout sur la mémoire tampon source pour les médias déjà lus. Chrome rejette le fragment ajouté, y compris moov, provoquant ainsi une erreur de décodage. (Problème Chromium #735335)</p> <p>19921 : la lecture bloque certains contenus HLS même si leur mise en mémoire tampon a réussi (problème Chromium #713540)</p> <p>・ 2044 : la recherche vers la fin de la plage mise en mémoire tampon sur IE et Edge peut entraîner le blocage de la lecture.</p> <p>・ 20511 : Parfois, le rejet de la recherche peut être observé pour les flux HLS avec ou sans publicité.</p> <p>・ 20743 : sous Windows 10 Chrome, le flux HLS Live est lu pendant quelques secondes avant la lecture preroll MP4.</p> <p>・ 21043 : La dimension vidéo peut ne pas être correcte au chargement initial en raison d’un manque de métadonnées.</p> <p>・ 21115 : Android Le geste de l’utilisateur est nécessaire pour démarrer la lecture si la publicité preroll est disponible pour les vidéos dans une liste de lecture.</p> <p>・ HLS Live ne prend pas en charge le roulement de l’horodatage.</p> <p>・ Le son AAC-SSR n’est pas pris en charge.</p> <p>Les codecs audio AC3 et l’AC3 amélioré ne sont pas pris en charge.</p> <p>・ Pour les diffusions dont l’horodatage est incohérent mais sans marqueurs de discontinuité</p> <p>・ La lecture peut avoir des problèmes et une recherche incorrecte en raison des sauts.</p> <p>・ La durée du contenu et la durée de lecture peuvent ne pas correspondre.</p> <p>・ Les discontinuités entre les représentations et les rendus doivent correspondre à d’autres facteurs peut entraîner des problèmes de synchronisation et de blocage.</p> <p>・ Les sous-titres et WebVTT peuvent ne pas apparaître près de la fin de flux.</p> <p>・ Les modifications du codec audio ne sont pas prises en charge dans les sauts d’horodatage.</p> <p>・ L’insertion de publicités n’est pas prise en charge.</p> <p>・ Le mode de transfert rapide peut entraîner une boucle de lecture sur Win 8.1 IE 11 (problème MS #12446268).</p> <p>DASH :</p> <p>・ Pour les flux en direct : le profil en direct avec le type dynamique est pris en charge.</p> <p>・ Pour les flux VoD : le profil en direct avec le type statique est pris en charge.</p> <p>Pour les flux VoD : le profil à la demande n’est pas certifié pour les flux de production publicitaires.</p> </td> 
   <td><p>・ Les diffusions DASH Live et DASH Video on Demand ne sont pas prises en charge.</p> <p>・ La lecture vidéo PIP (Image dans l’Image) n’est pas prise en charge sur iOS en mode plein écran.</p> <p>Sur l’extension Safari (Video Tag) moins manifeste sans en-tête de type de contenu correct, ne fonctionnent pas.</p> </td> 
   <td><p>・ applicationID dans l’application d’expéditeur doit être identique à celui généré lors de l’enregistrement de l’URL du récepteur en tant qu’application de récepteur personnalisée.</p> <p>・ Le lecteur de référence est certifié pour les processus DASH. La structure de l’interface utilisateur n’est pas certifiée.</p> <p>Pour obtenir la liste des codecs multimédias pris en charge, reportez-vous à la section <a href="https://developers.google.com/cast/docs/media"><em>here</em></a>.</p> </td> 
  </tr> 
  <tr> 
   <td>FER VOD</td> 
   <td>Lecture générale (Lecture, Pause, Recherche)</td> 
   <td> </td> 
   <td>18098 : Certains problèmes de recherche sont observés avec le flux de flux HLS LBA FER.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Débit adaptatif</td> 
   <td><p>・ 20079 : Réécriture de la mémoire tampon à la recherche dans une plage mise en mémoire tampon.</p> <p>20080 : le comportement de l’ABR de Flash est cohérent avec MSE.</p> </td> 
   <td><p>・ La variante Version de secours audio seule dans un flux ABR est ignorée en raison des limitations liées à la mémoire tampon.</p> <p>・ 12289 : Les paramètres de contrôle ABR ne s'appliquent pas à l'audio en cas de flux HLS/DASH non muxés.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>608/708 Captions</td> 
   <td> </td> 
   <td><p>・ 7810 : Sur Android 4.4.4, Chrome ne semble pas prendre en charge les familles de polices CSS de base utilisées par le lecteur. Par conséquent, la fonction de changement de style de police ne fonctionne pas.</p> <p>・ Les canaux CC ne peuvent pas être modifiés dans le cas de 608 sous-titres.</p> <p>・ Les fonctions de style avancées ne sont pas prises en charge pour les sous-titres 608.</p> <p>Les sous-titres incorporés (608/708), signalés via la balise d’accessibilité sont pris en charge.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>WebVTT</td> 
   <td> </td> 
   <td><p>・ 5206 : les balises de région dans le fichier WebVTT sont ignorées par le lecteur lors de l’affichage des sous-titres.</p> <p>・ DASH : les fichiers VTT fragmentés/segmentés ne sont pas pris en charge.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Basculement du manifeste</td> 
   <td>21056 : Avec Flash Fallback, le basculement ne se produit pas pour le flux en direct si le flux principal renvoie une erreur 404 pendant la lecture.</td> 
   <td>Le basculement du manifeste s’applique uniquement au contenu et non aux publicités.</td> 
   <td>Le basculement de liste de lecture manquant fonctionne uniquement sur Safari pour le code d’erreur HTTP 404.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Basculement avancé</td> 
   <td> </td> 
   <td><p>・ Le basculement de segment ne prend pas en charge le saut de segments indisponibles et la poursuite de la lecture.</p> <p>2053 : les segments manquants dans une liste de lecture doivent être traités comme une discontinuité et la lecture doit reprendre à partir du prochain segment disponible.</p> <p>21267 : le changement de diffusion en raison d’un basculement peut entraîner le téléchargement d’anciens segments.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Notifications QoS et du lecteur</td> 
   <td>21129 : La fréquence d'image n'est pas disponible en cas de secours par Flash.</td> 
   <td><p>• 11170:</p> <p>Timed_Event n’est pas disponible pour Browser TVSDK avec MSE, contrairement à Browser TVSDK avec Flash Fallback.</p> <p>21129 : Le taux d'image n'est pas calculé pour les flux en direct.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Prise en charge des en-têtes de cookie</td> 
   <td> </td> 
   <td> </td> 
   <td><p>L’indicateur withCredentials et les en-têtes de cookie ne sont pas pris en charge sur Safari.</p> <p>21051 : Pour autoriser les cookies dans Safari, activez le paramètre "Cookies et données de site web" dans Préférences &gt; Confidentialité.</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Balises personnalisées</td> 
   <td>14763 : Les balises personnalisées autres que commençant par # ne doivent pas être prises en charge. En ce moment, l’objet TimedMetadata est créé et rapporté pour ces balises lors d’un Flash de secours.</td> 
   <td>Les flux avec des balises personnalisées intégrées ne sont pas certifiés.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Audio de liaison différée</td> 
   <td> </td> 
   <td><p>・ L’insertion de publicités n’est pas prise en charge avec les flux LBA HLS Live.</p> <p>・ 17273 : les flux LBA HLS VOD passent au rendu par défaut en cas de basculement et ne peuvent pas être rétablis sur la dernière sélection.</p> <p>・ 20251 : la diffusion HLS Live LBA peut bloquer la recherche.</p> <p>・ 20497 : Le lecteur reste en état de mise en mémoire tampon si les diffusions HLS LBA non muxées ont des images audio ou vidéo manquantes à la fin de la diffusion.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Redirection 302</td> 
   <td> </td> 
   <td><p>15787: 302</p> <p>l’optimisation de la redirection n’est pas prise en charge sur les navigateurs Windows Edge et IE, car ils ne prennent pas en charge la propriété responseURL dans l’objet XMLHttpRequest .</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 17 : Fonctionnalités de lecture avancées**

<table> 
 <tbody> 
  <tr> 
   <td>Type de contenu</td> 
   <td>Fonctionnalité</td> 
   <td>Flash</td> 
   <td><strong>HTML5 dans Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 dans Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (lecture DASH uniquement)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Lecture au décalage</td> 
   <td><p>Le démarrage de la lecture à une valeur de décalage spécifique n’est pas pris en charge dans le contenu MP4.</p> </td> 
   <td>20492 : les publicités mid-roll précédant le décalage sont lues avant que le contenu ne reprend de la valeur de décalage.</td> 
   <td>La lecture avec décalage n’est pas prise en charge dans iOS.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Lecture de la carte</td> 
   <td>La lecture en continu ne fonctionne pas pour les diffusions qui n’ont aucun rendu iFrame.</td> 
   <td><p>・ Les adaptations de la lecture de la marque ne sont pas prises en charge sur Firefox et Internet Explorer et le mode de ruse inverse n’est donc pas disponible sur ces navigateurs.</p> <p>・ La lecture de texte n’est pas disponible lors de la lecture de contenu avec des publicités.</p> <p>・ 10435 : pendant la lecture DASH, la vidéo se bloque lors de la lecture de l’astuce avant sur Internet Explorer (Windows 8.1)</p> <p>par intermittence. Cela se produit puisque nous utilisons la propriété playbackRate des éléments vidéo sans l’adaptation de lecture de l’astuce.</p> <p>14182 : Parfois, lors du retour en arrière sur le navigateur Chrome, l’événement de recherche peut ne pas être reçu et par conséquent, le mode de ruse ne fonctionne pas.</p> <p>・ 14942 : les taux de lecture peuvent être définis sur Chrome pour Android même en cas de flux de lecture autres que les tours, mais le paramètre ne sera pas appliqué et la lecture continuera à un rythme normal.</p> <p>・ 17308 : La recherche ne fonctionne pas en mode Trickplay.</p> <p>・ 17309 : sur le navigateur Chrome, le mode de l’envers ne peut pas être maintenu pendant plus de 2 secondes.</p> <p>19272 : il se peut que la lecture de la marque ne récupère pas de la mise en mémoire tampon sur le navigateur Windows 10 Edge dans le cas des flux DASH.</p> </td> 
   <td>Le mode Rembobiner n’est pas pris en charge.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Analyse d’ID3</td> 
   <td>20346 : L’octet de codage de texte des images ID3 doit également être renvoyé par le SDK.</td> 
   <td><p>Les balises ID3 disponibles dans les flux de transfert de données audio (ADTS) sont ignorées par le SDK.</p> <p>・ 12378 : les métadonnées minutées ID3 sont analysées à différents moments sur le Flash et le navigateur avec prise en charge de MSE. Par conséquent, le comportement d’affichage sur la chronologie du lecteur de référence est également différent.</p> <p>・ 19247 : l’analyse ID3 n’est pas prise en charge dans l’interface utilisateur.</p> </td> 
   <td><p>・ 20323 : la balise PRIV ID3 utilisée pour signaler l’horodatage du premier exemple de segment n’est pas analysé par Safari (numéro Safari #32422733)</p> <p>・ 20350 : sur certains appareils (y compris MAC OS X 10.1, iPad10), Safari ne fournit pas d’événement de changement de repère en mode de ruse et par conséquent, les images ID3 ne sont pas reçues. (Problème Safari #32450526)</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Prise en charge des marqueurs de discontinuité</td> 
   <td> </td> 
   <td><p>・ L’insertion de publicités côté client n’est pas prise en charge avec les flux HLS contenant une discontinuité.</p> <p>・ Le changement de codec audio n’est pas autorisé dans les discontinuités du flux HLS.</p> <p>・ Le commutateur de piste audio n’est pas pris en charge pour le flux HLS avec des marqueurs de discontinuité</p> </td> 
   <td>Le numéro de séquence de discontinuité est obligatoire pour les flux HLS avec discontinuité afin de permettre la lecture sur Safari.</td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 18 : Fonctionnalités de protection du contenu**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Type de contenu</strong></td> 
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML5 dans Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 dans Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (lecture DASH uniquement)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>AES-128</td> 
   <td> </td> 
   <td>La plage d’octets n’est pas prise en charge avec le contenu chiffré AES-128.</td> 
   <td>12324 : La lecture des diffusions cryptées HLS AES-128 échoue sur Safari si la balise IV n’est pas spécifiée.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>DRM</td> 
   <td> </td> 
   <td><p>・ 12660 : le lecteur HTML5 renvoie une erreur interne au serveur pour les contenus de hachage chiffrés PlayReady expirés.</p> <p>・ 16720 : le contenu chiffré DASH DRM ne fonctionnera pas si l’attribut start dans la balise period est manquant.</p> <p>・ 18589 : la lecture n’est pas prise en charge pour les flux multipériodes Dash VoD protégés par DRM avec Xlink.</p> <p>・ 18653 : la lecture du contenu multi-période de Widevine avec plusieurs clés s’arrête à la première période et ne peut pas passer à la période suivante.</p> <p>・ 18656 : Diffusion multi-périodes prête à la lecture, cryptée avec différentes clés, sans lecture.</p> <p>Playready 2.0 pour le tiret n’est pas certifiée.</p> <p> </p> <p> </p> </td> 
   <td>12602 : les métadonnées DRM HLS Fairplay sont régulièrement actualisées par le lecteur HTML5 sur Safari.</td> 
   <td><p>Le contenu DRM d’appareil à grande vitesse DASH conditionné via Bento4 peut être lu. Le contenu conditionné via Offline Packager et Shaka packager ne s’exécute pas. DASH PlayReady DRM n’est pas pris en charge.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 19 : Fonctionnalités principales de l’Ad Insertion**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Type de contenu</strong></td> 
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML5 dans Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 dans Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (lecture DASH uniquement)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Pré/Mid/Post</td> 
   <td> </td> 
   <td><p>・ Les publicités preroll avec du contenu HLS en direct sont lues en mode double lecteur.</p> <p>・ Les publicités DASH avec contenu HLS et les publicités HLS avec contenu DASH ne sont pas prises en charge.</p> <p>・ 19002 : Dans HTML5 Player avec MSE adBreak. insertType ne renvoie pas la valeur correcte pour décrire le type d’insertion correct, c’est-à-dire le client inséré et ou le serveur inséré.</p> <p>7794 : sur les appareils mobiles (iOS, Android avec Chrome 33 ou version inférieure ou Navigateur natif) où la barre de contrôle par défaut est visible en mode Plein écran, la barre de recherche et les boutons de transfert rapide sont disponibles lors de la lecture des publicités.</p> <p>・ 11048 : le passage de la publicité au contenu HLS Live n’est pas fluide dans le cas des extensions de source de média.</p> <p>・ 16083 : sur Android 4.4 Chrome v52, il arrive que la publicité HLS avec du contenu HLS entraîne une erreur de décodage de pipeline après la lecture bloquée.</p> <p>・ 16097 : Les erreurs rencontrées lors de la coupure publicitaire ne sont pas gérées, ce qui peut entraîner l’arrêt de la lecture de la diffusion principale.</p> <p>・ 18095 : les publicités MP4 ne sont pas prises en charge avec le contenu HLS en direct.</p> <p>19120 : Plusieurs recherches sur des annonces HLS avec du contenu HLS peuvent entraîner l’arrêt de la lecture de la diffusion.</p> <p>・ 19131 : la superposition de la mémoire tampon peut apparaître lors du passage de la coupure publicitaire preroll au contenu.</p> <p>・ 20296 : dans le cas de diffusions HLS Live, la recherche en amont dans la fenêtre de l’enregistreur de contenu, suivie de la recherche sur les parcours intermédiaires résolus, peut entraîner un blocage de lecture.</p> <p>・ 20298 : Diffusions HLS Live avec des rouleaux moyens bloquent dès que la première publicité mid-roll sort de la fenêtre de l’enregistreur numérique.</p> <p>・ 20317 : les flux HLS Live peuvent bloquer lors du passage à la publicité suivante ou de la publicité vers le contenu si la coupure publicitaire contient plusieurs publicités.</p> 
    <ul> 
     <li>Les publicités dans la fenêtre de l’enregistreur numérique des diffusions HLS Live ne sont pas résolues.</li> 
    </ul> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>Le SDK n’honore pas l’attribut de séquence dans la réponse VMAP pour VAST adSource.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>20779 : Le SDK ne respecte pas l’attribut de séquence dans la réponse VMAP pour VAST adSource.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>VMAP 1.0</td> 
   <td> </td> 
   <td>12014 : L’attribut de répétition VMAP n’est pas pris en charge.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Creative Repackaging</td> 
   <td> </td> 
   <td>21464 : La réponse de la publicité est complètement ignorée si le reconditionnement créatif échoue pour l’une des publicités de la coupure publicitaire.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 20 : Fonctionnalités Ad Insertion avancées (CSAI)**

<table> 
 <tbody> 
  <tr> 
   <td><strong>Type de contenu</strong></td> 
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Flash</strong></td> 
   <td><strong>HTML5 dans Firefox, IE, Chrome, Android Chrome</strong></td> 
   <td><strong>HTML5 dans Safari, iOS Safari</strong></td> 
   <td><strong>Chromecast (lecture DASH uniquement)</strong></td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Publicité uniquement</td> 
   <td> </td> 
   <td>20056 : La propriété de la technologie du lecteur n’est pas pertinente, car elle est basée sur le contenu principal, qui est vide dans le cas de la lecture de publicité seule.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + En direct</td> 
   <td>Stratégie de publicité personnalisée</td> 
   <td> </td> 
   <td><p>・ Les comportements publicitaires ne sont pas pris en charge avec les publicités MP4 et le contenu MP4.</p> <p>・ 13973 : Comportements de publicité personnalisés - La stratégie de SKIP ne génère pas d’événement complete lorsqu’elle est utilisée avec MSE.</p> <p>・ 14939 : Les stratégies de comportement de publicité personnalisées ignorent et ignorent la coupure publicitaire ne fonctionnent pas pour le contenu DASH.</p> <p>・ 17131 : La première image de la publicité est visible, puis le contenu reprend en cas de stratégie de coupure publicitaire par SKIP.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Publicités d’accompagnement/bannières publicitaires/publicités cliquables</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>Les bannières publicitaires ne sont pas visibles lors de l’utilisation du lecteur de référence.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>VPAID 2.0</td> 
   <td> </td> 
   <td><p>・ Les comportements publicitaires ne sont pas pris en charge pour les publicités VPAID.</p> <p>・ 15032 : les publicités VPAID en combinaison avec les publicités MP4 ou HLS en coupure publicitaire ne sont pas prises en charge.</p> <p>・ 19001 : sur Android et iOS, lorsque la publicité VPAID est lue avec le contenu MP4 comme contenu principal, deux pistes audio sont audibles, l’une du contenu principal et l’autre de la publicité.</p> <p>・ 20762 : les publicités VPAID ne sont pas prises en charge avec le mode "Image dans l’Image" (PIP).</p> <p>・ 21172 : L’événement Lire terminée n’est pas reçu pour le contenu VOD HLS avec publicités VPAID.</p> <p>・ 21173 : onAdBreakCompleteEvent n’est pas reçu pour le contenu VOD HLS et les publicités VPAID post-roll.</p> </td> 
   <td>Le lecteur bascule entre le mode normal et le mode plein écran lors du basculement entre la publicité VPAID et le contenu principal.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 21 : Intégrations**

| **Type de contenu** | **Fonctionnalité** | **Flash** | **HTML5 dans Firefox, IE, Chrome, Android Chrome** | **HTML5 dans Safari, iOS Safari** | **Chromecast (lecture DASH uniquement)** |
|---|---|---|---|---|---|
| VOD + En direct | Intégration d’Adobe Analytics VHL |  | 19004 : Le suivi des analyses vidéo n’est pas disponible via l’outil de configuration de l’interface utilisateur. |  |  |

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://experienceleague.adobe.com/docs/primetime.html) page.
