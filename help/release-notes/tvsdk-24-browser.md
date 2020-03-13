---
title: Notes de mise à jour du navigateur TVSDK 2.4
seo-title: Notes de mise à jour du navigateur TVSDK 2.4
description: Les notes de mise à jour du navigateur TVSDK 2.4 décrivent les nouvelles fonctionnalités, les fonctionnalités prises en charge et les problèmes connus du navigateur TVSDK 2.4.
seo-description: Les notes de mise à jour du navigateur TVSDK 2.4 décrivent les nouvelles fonctionnalités, les fonctionnalités prises en charge et les problèmes connus du navigateur TVSDK 2.4.
uuid: 3a1eb1a5-0e72-4658-beeb-bca8816570e7
contentOwner: dekalra
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: d71886cb-f34b-47b2-9df7-168686478106
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Notes de mise à jour du navigateur TVSDK 2.4 {#browser-tvsdk-release-notes}

Les notes de mise à jour du navigateur TVSDK 2.4 décrivent les nouvelles fonctionnalités, les fonctionnalités prises en charge et les problèmes connus du navigateur TVSDK 2.4.

## Introduction {#introduction}

Le SDK du navigateur est un kit d’outils qui vous permet d’ajouter des fonctionnalités avancées de lecture vidéo, de protection du contenu et de publicité à vos applications de lecteur vidéo basées sur un navigateur.

Le navigateur TVSDK 2.4 fournit des API JavaScript pour créer des applications vidéo basées sur un navigateur et prend en charge la lecture dans les modes suivants :

* HTML5 uniquement
* HTML5 avec abandon automatique du flash
* Flash toujours

Cette version comprend les informations suivantes :

・ Documentation [sur l&#39;API](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)du navigateur TVSDK.

・ Guide [de programmation du](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_browser-tvsdk.pdf)navigateur TVSDK.

・ [TVSDK for 1.4 DHLS to Browser TVSDK 2.4 Migration Guide](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html).

・ [Conversion de Browser TVSDK 2.4.6 à la version 2.4.7](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-246-to-247-for-javascript.html).

・ Une mise en oeuvre de référence, qui est incluse dans la compilation.

>[!NOTE]
>
>*Pour un complet des considérations de sécurité pour cette version, voir Considérations relatives à la sécurité.

## Nouveautés et fonctionnalités prises en charge {#what-s-new-and-supported-features}

Cette version de Browser TVSDK fournit de nouvelles fonctionnalités que vous pouvez utiliser pour améliorer vos applications vidéo.

**Nouveautés de la mise à jour 2.4.12 (version 204)**

L’ajout suivant est disponible dans le cadre de la mise à jour de Browser TVSDK 2.4.12 (version 204) :

* L’implémentation de l’API de volume d’AdobePSDK.MediaPlayer est modifiée afin d’autoriser la lecture automatique sur iOS lorsque la lecture est interrompue.

・ Une nouvelle API `auditudeSettings.ignoreVPAIDAds`, est ajoutée pour permettre d’ignorer les publicités VPAID reçues du serveur Auditude. L’API ne fonctionne pas pour les abandons Flash.

**Version 2.4.11**

Les améliorations et ajouts suivants sont disponibles dans la version 2.4.11 de Browser TVSDK :

・ Le basculement du segment HLS Live est pris en charge pour les modes de secours MSE et Flash.

・ La prise en charge de `AuditudeSettings.creativeRepackagingDomain` l&#39;API est maintenant disponible pour MSE également. Auparavant, il était uniquement pris en charge avec le mode de secours Flash.

・ La version contient des correctifs pour les problèmes critiques des clients. Voir *Problèmes résolus* dans un .

**Version 2.4.10**

Les améliorations et ajouts suivants sont disponibles dans la version 2.4.10 de Browser TVSDK :

・ TVSDK fournit enableLogging() pour activer ou désactiver la journalisation. Reportez-vous à la [documentation de l’](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)API pour plus d’informations.

・ TVSDK ne prend plus en charge les chapitres par défaut lors de l’utilisation d’Adobe Analytics. Définissez et gérez des chapitres à l’aide de votre application.

・ La version contient des correctifs pour les problèmes critiques des clients. Voir *Problèmes résolus *un  de.

**Version 2.4.9**

Les améliorations et ajouts suivants sont disponibles dans la version 2.4.9 de Browser TVSDK :

・ Les flux HLS VOD et Live avec discontinuité dans le temps mais sans discontinuité sont pris en charge.

・ Les images ID3 v2.4.0 sont prises en charge avec la balise vidéo Safari pour les flux VOD HLS et Live.

・ La mise en oeuvre du chargement sécurisé des publicités garantit que les appels du serveur d’annonces sont mis à niveau vers le protocole HTTP sécurisé en fonction de la configuration de l’API. Pour plus d’informations, voir AdobePSDK.AdvertisingMetadata et AdobePSDK.ForceHttpsAdConfiguration classes. Cette fonctionnalité n’est pas prise en charge en mode de secours Flash.

・ Les informations sur les identifiants publicitaires et les informations sur l’extension associées aux réponses VAST 3.0 sont maintenant mises à la disposition de l’application par TVSDK et peuvent être utilisées pour mettre en oeuvre l’intégration Moat pour les mesures publicitaires. Pour plus d’informations, voir AdobePSDK.NetworkAdInfo API. Ceci n’est pas pris en charge en mode de secours Flash.

・ La classe AdobePSDK.ForceHttpsConfiguration n’est plus disponible. Il est remplacé par

Classe AdobePSDK.ForceHttpsAdConfiguration.

・ Une nouvelle API, AdobePSDK.optimizeFlashCalls, est désormais disponible pour optimiser les appels afin d’améliorer l’expérience de lecture HLS en mode de secours Flash. Il est désactivé par défaut.

**Nouveautés de la mise à jour 2.4.8 (version 6002)**

Cette mise à jour contient des correctifs pour les problèmes critiques des clients. Voir Problèmes ** résolus pour le  du.

**Version 2.4.8**

Les améliorations et ajouts suivants sont disponibles dans la version 2.4.8 de Browser TVSDK :

・ Le SDK est maintenant conforme au modèle Chrome EME et les meilleures pratiques sont disponibles à partir de Chrome v58. Pour plus d’informations, voir [https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf](https://storage.googleapis.com/wvdocs/Chrome_EME_Changes_and_Best_Practices.pdf)**

・ Le Cadre d&#39;interface utilisateur prend désormais en charge la gestion des droits numériques HLS Access sur Flash, les annonces publicitaires uniquement et le flux de travaux Ciblage des informations.

・ L&#39;API setDRMAuthenticateData est ajoutée à la structure de l&#39;interface utilisateur. Pour lire des flux protégés par Adobe Access DRM, appelez cette API. Vous pouvez également spécifier l’attribut drmAuthenticateData dans le lecteur. Voir [AdobePSDK.videoBehavior ](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/VideoBehavior.html)pour plus d’informations.

**Version 2.4.7**

Les fonctionnalités suivantes sont nouvelles dans la version 2.4.7 :

・ Ajout du configurateur d&#39;interface dans le cadre de l&#39;interface utilisateur

Vous pouvez configurer le lecteur de l’une des manières suivantes :

・ Utilisation d’un objet JSON

・ Utilisation des API

Pour faciliter la génération de l’objet JSON, le navigateur TVSDK fournit un **outil **UI Configurator **.

Dans cet outil, vous pouvez sélectionner divers paramètres, cliquer sur **Test de la configuration **pour vérifier les paramètres, puis sur **Télécharger la configuration **pour télécharger les paramètres. Après avoir téléchargé le fichier, vous pouvez transmettre le contenu de ce fichier sous forme d’objet JSON à l’API ptp.videoPlayer.

・ Ajout de l’API MediaPlayerItemConfig à la structure de l’interface utilisateur

Diverses fonctionnalités, dont les pubsMetadata, adsFactory, adSignalingMode, networkConfiguration, customRangeMetadata, useHardwareDecoder, subscriptionTags, adTags, thumbnailScrubber, billingMetricsConfiguration, peuvent être configurées via MediaPlayerItemConfig. Pour plus d’informations, reportez-vous à la documentation AdobePSDK.MediaPlayerItemConfig dans l’API [du](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)navigateur TVSDK* * [documentation](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html).

Dans la structure de l&#39;interface utilisateur, la manière de transmettre les configurations réseau via la configuration du lecteur a été modifiée.

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

* Prise en charge des  DRM et Analytics dans l’interface utilisateur

Les configurations DRM et le suivi Analytics peuvent être activés via l’interface utilisateur.

* Ajout d’une `AdobePSDK.embedSWFinFullScreenDiv` API

Cette nouvelle API offre une certaine flexibilité à l’application du lecteur pour la sélection de la balise div dans laquelle elle peut incorporer le fichier FlashFallback.swf.

* Remplacement de l’ `getVersion`API de la `AdobePSDK.MediaPlayer` classe par la `AdobePSDK.Version` classe pour les informations relatives à la version de TVSDK. Pour plus d&#39;informations, reportez-vous à `AdobePSDK.Version` l&#39;API [ici](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/AdobePSDK.Version.html).

**Version 2.4.6**

Les fonctionnalités suivantes sont nouvelles dans la version 2.4.6 :

* **Prise en charge de la navigation**

Browserify vous permet d’utiliser les modules de style node.js dans le navigateur. Vous pouvez définir les dépendances et parcourir les regroupements dans un seul fichier JavaScript.

* **Facturation**

Grâce à la facturation, le navigateur TVSDK peut collecter des mesures d’utilisation du lecteur afin de facturer les clients Primetime.

>[!NOTE]
>
>Les valeurs enum MediaPlayer.et les constantes déconseillées dans Enum PSDKErrorCode ont été supprimées dans la version 2.4.6. Pour plus d’informations, voir [Conversion du navigateur TVSDK 2.4.5 en version 2.4.6](https://helpx.adobe.com/primetime/conversion-guides/browser-tvsdk-245-to-246-for-javascript.html).

**Version 2.4.5**

Les fonctionnalités suivantes sont nouvelles dans la version 2.4.5 :

* **Révisions et publicités de  complètes**

   Les flux de réexécution des  HLS Full (FER) prennent désormais en charge la résolution des publicités et les comportements publicitaires. Pour activer cette prise en charge, définissez le mode de signalisation publicitaire sur `MANIFEST_CUES` lors de la création de l’ `MediaPlayerItemConfig` objet.

* **Prise en charge des stratégies d’échelle MediaPlayerView**

   Les développeurs d’applications peuvent désormais spécifier une stratégie scalePolicy différente pour le à l’aide de la propriété scalePolicy de Media PlayerView.

* **Prise en charge du contenu anamorphique**

   La lecture de contenu anamorphique est désormais prise en charge lors de l’utilisation de la lecture MSE et Flash.

* **Application sélective de`withCredentials`**

Lorsque `withCredentials` est défini sur true, l’ `Access-Control-Allow-Origin` en-tête ne peut pas être défini sur un caractère générique. Selon la réponse du serveur, le navigateur TVSDK définira sélectivement l’ `withCredentials` attribut. Pour plus d’informations sur cette prise en charge, consultez la documentation [API](https://help.adobe.com/en_US/primetime/api/psdk/browser_tvsdk/index.html)du navigateur TVSDK.

**Version 2.4.4**

Les nouvelles fonctionnalités suivantes ont été ajoutées à la version 2.4.4 :

* **Exemple d’application Chromecast**

Cette version prend en charge une application d’expéditeur et de destinataire qui montre la lecture des flux VOD DASH et des flux Widevine DASH avec insertion de publicités côté client.

* **Prise en charge avancée du basculement**

Cette version prend en charge les cas d’utilisation de basculement avancés (basculement de segment et de serveur) pour les flux VOD HLS.

**Version 2.4.3**

Les nouvelles fonctionnalités suivantes ont été ajoutées à la version 2.4.3 :

* **Balises personnalisées pour DASH VOD**

   Les balises personnalisées intégrées () peuvent être abonnées et reçues en tant qu’objet TimedMetadata.

* **Lecture des flux sans extensions**

   Les flux HLS et DASH sans extensions sont désormais pris en charge. Pour le fichier manifeste, le type resourceType doit être spécifié lors du chargement de la ressource. Pour les segments et les fichiers VTT, l’en-tête de réponse Content-Type est utilisé pour déterminer le type de contenu.

**Version 2.4.2**

Les nouvelles fonctionnalités suivantes ont été ajoutées à la version 2.4.2 :

* **Parité API**

Pour obtenir un complet de la parité API, reportez-vous au Guide [de migration](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-dhls-browser-tvsdk-24.html)TVSDK for 1.4 DHLS to Browser TVSDK 2.4.

* **Prise en charge d’Sample-AES**

   Cette version ajoute la prise en charge de la lecture de contenu chiffré Sample-AES sur les versions de secours MSE et Flash. L’obligation d’héberger le contenu AES sur des  sécurisés  sur Google Chrome a été supprimée.

* **Prise en charge des  de AAC**

   La lecture des fichiers avec l’extension .aac est maintenant prise en charge. Il peut s’agir de flux audio uniquement ou de fichiers audio alternatifs.

   >[!NOTE]
   >
   >Les codecs AC3 et AC3 améliorés ne sont pas encore pris en charge.

* **Lecture de flux jetée**

Les flux HLS diffusés par l’intermédiaire d’un réseau CDN (Content Network) peuvent parfois utiliser des jetons d’authentification sur les demandes de manifeste et de segment à vérifier. Ces jetons peuvent être fournis sous forme de paramètres d’URL ou d’en-têtes de cookie. La lecture de ces flux est désormais prise en charge.

**Version 2.4.1**

Les nouvelles fonctionnalités suivantes ont été ajoutées à la version 2.4.1 :

* **Structure d’interface**

Cette structure, conçue pour accélérer le développement de l’interface utilisateur pour les applications de lecteur vidéo basées sur JavaScript, consiste en des API permettant d’inclure des commandes de base telles que play/pause et volume et d’ajouter ou de supprimer facilement des éléments tels que les états de barre de défilement et les paramètres de sous-titrage. Vous pouvez spécifier le comportement associé aux contrôles, créer des contrôles personnalisés et habiller l’interface utilisateur du lecteur. Tout cela se passe par le cadre, sans avoir à manipuler directement la structure DOM.

* **Améliorations de la lecture HLS pour les flux en direct**

Cette version prend en charge les discontinuités provoquées par l’insertion d’une publicité. Il utilise la balise EXT--DATE-TIME, suivie de la balise EXT-MEDIA-SEQUENCE, pour synchroniser sur le de débit adaptatif  pour une lecture en douceur.

* **Prise en charge de VPAID 2.0**

La version 2.0 de l’interface VPAID (Video Player Ad Serving Interface), offre aux utilisateurs une expérience multimédia enrichie et permet aux éditeurs de mieux les publicités, suivre les impressions publicitaires et monétiser le contenu vidéo. Cette version prend en charge les annonces VPAID JavaScript linéaires pour le contenu vidéo à la demande (VOD).

* **Balises HLS personnalisées**

Les flux de médias peuvent comporter des métadonnées supplémentaires sous la forme de balises dans le fichier playlist/manifest. Le navigateur TVSDK vous permet de spécifier des balises supplémentaires et de vous y abonner et d’être averti lorsque ces balises apparaissent dans le manifeste.

* **Marques publicitaires affichées dans la chronologie du lecteur**

Cette version prend en charge l’affichage des marqueurs publicitaires sur la chronologie du lecteur pour le contenu VOD et Live. Vous pouvez voir ce comportement dans le lecteur de référence.

**Pris en charge dans la version 2.4**

Les fonctionnalités suivantes étaient disponibles dans la version 2.4 :

* **Lecture audio MP3**

   Cette version prend en charge la lecture audio MP3 sur les navigateurs avec Media Source Extensions (MSE) et avec la balise vidéo Safari.

* **Lecture vidéo MP4**

   Les fonctionnalités suivantes sont prises en charge :

   * Lecture en flux continu unique
   * Publicités MP4 preroll et Post-roll avec comportements publicitaires et suivi
   * Publicités HLS preroll et Post-roll avec comportements publicitaires et suivi
   * Publicités DASH preroll et Post-roll avec comportements publicitaires et suivi

## Plates-formes prises en charge {#supported-platforms}

Le SDK du navigateur contient des exigences spécifiques pour les niveaux de plates-formes et de logiciels sur lesquels il doit être exécuté. Les plates-formes et niveaux de logiciels suivants sont pris en charge :

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

* Apple OS X

   * Safari 9+
   * Chrome 33+
   * Firefox 38+

### Configurations Web mobiles {#mobile-web-configurations}

* Android 4.4

   * Navigateur natif
   * Chrome 33+

* Android 5.0

   * Navigateur natif
   * Chrome 33+

* Android 6.0

   * ・ Chrome 33+

* Apple iOS 9

   * Safari 9+
   * Chrome 33+

* Apple iOS 10

   * Safari 9+
   * Chrome 33+

**Google Chromecast (deuxième génération; pour la lecture DASH uniquement)**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Technologie</strong> </p> </td> 
   <td><p><strong>Balise</strong><sup>vidéo du navigateur TVSDK 1</sup></p> </td> 
   <td><p><strong>Navigateur TVSDK MSE</strong></p> </td> 
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

## Matrice des fonctionnalités {#feature-matrix}

Voici un  des fonctionnalités prises en charge et non prises en charge pour cette version :

* *Fonctionnalités audio MP3 — Lecture principale*
* *Fonctionnalités vidéo MP4 — Lecture principale*
* *Fonctionnalités vidéo MP4 — Insertion d&#39;annonce principale*

>[!NOTE]
>
>*Dans les tableaux de la matrice des fonctionnalités ci-dessous, &quot;Y&quot; signifie que la fonctionnalité est prise en charge dans la version actuelle.*

### Fonctionnalités audio MP3 {#mp-audio-features}

**Tableau 1 : Lecture principale{#table-core-playback}**

| Category | Type de contenu | Fonctionnalité | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Lecture | MP3 VOD | Lecture générale (Lecture, Pause, Recherche) | Non pris en charge | Y | Y |

1 La balise vidéo du navigateur TVSDK ne prend pas en charge la diffusion en flux continu et la gestion dynamique des balises. La prise en charge du codec et des  n’est pas la même dans tous les navigateurs.

2 Firefox utilise par défaut Flash Player pour la version 41 ou antérieure.

### Fonctionnalités audio MP4 {#mp-audio-features-1}

**Tableau 2 : Lecture principale**

| Category | Type de contenu | Fonctionnalité | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Lecture | MP4 VOD | Lecture générale (Lecture, Pause, Recherche) | Non pris en charge | Y | Y |

**Tableau 3 : Insertion d&#39;annonce principale**

| Category | Type de contenu | Fonctionnalité | Flash | HTML5 : FF, IE, Chrome, Android Chrome | HTML5 : Safari, iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Insertion d&#39;une publicité | MP4 VOD | Pré-roll (MP4) | Non pris en charge | Y | Y |
| Insertion d&#39;une publicité | MP4 VOD | Post-roll (MP4) | Non pris en charge | Y | Y |

Pour plus d’informations sur la prise en charge des fonctionnalités HLS ou DASH, voir ci-dessous.

## Matrice des fonctionnalités HLS {#hls-feature-matrix}

Voici la matrice des fonctionnalités des fonctionnalités HLS dans le SDK du navigateur.

* *Lecture principale HLS*
* *Fonctions de lecture avancées HLS*
* *Fonctionnalités de protection du contenu HLS*
* *Fonctionnalités d&#39;insertion des annonces HLS Core et des annonces publicitaires*
* *Fonctionnalités d&#39;insertion de publicités HLS Advanced*
* *Intégrations HLS*

>[!NOTE]
>
>*Dans les tableaux de la matrice des fonctionnalités ci-dessous, &quot;Y&quot; signifie que la fonctionnalité est prise en charge dans la version actuelle.*

### Fonctionnalités HLS {#hls-features}

Les fonctionnalités suivantes sont prises en charge :

**Tableau 4 : Lecture principale HLS**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Category</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5 : Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
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
   <td><p>VOD + Live</p> </td> 
   <td><p>Débit adaptatif</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Légendes 608/708</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>WebVTT</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>VOD uniquement</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Basculement du manifeste</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Basculement avancé</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Notifications QoS et du lecteur</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Prise en charge limitée de la qualité de service</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Prise en charge des en-têtes de cookie</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Définition des paramètres de contrôle du tampon</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Définir adaptatif</p> <p>contrôles de débit binaire</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Balises personnalisées</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td>Audio à liaison tardive</td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>302 redirection</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 5 : Fonctions de lecture avancées HLS**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Category</strong></p> </td> 
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
   <td><p>Lecture audio uniquement</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Lecture de Trick</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Lecture lisse</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Analyse ID3</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Prise en charge des marqueurs de discontinuité</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Flux jetables</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Facturation</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 6 : Fonctionnalités de protection du contenu HLS**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Category</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5 : Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Protection du contenu</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>AES-128</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Protection du contenu</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Sample-AES</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Protection du contenu</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>Adobe Access</p> </td> 
   <td><p>Non pris en charge</p> </td> 
   <td><p>FairPlay</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 7 : Fonctionnalités d&#39;insertion des annonces HLS Core et des annonces publicitaires**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Category</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5 : Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Pré-roll (MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Mid-roll (HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Post-roll (MP4/HLS)</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Résolution et comportements des publicités</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Stratégie publicitaire par défaut</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VAST 2.0/3.0</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Creative Repackaging (MP4 vers HLS)</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 8 : Fonctionnalités d&#39;insertion de publicités HLS Advanced**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Category</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5 : Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Publicité uniquement</p> </td> 
   <td><p>Non pris en charge</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Paramètres de ciblage</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Paramètres personnalisés</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Stratégie publicitaire personnalisée</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Chargement différé de publicités</p> </td> 
   <td><p>Y</p> </td> 
   <td><p>Non pris en charge</p> </td> 
   <td><p>Limitation des plateformes</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Publicités d’accompagnement, bannières publicitaires, publicités cliquables</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
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
   <td><p><strong>Category</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>Flash</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
   <td><p><strong>HTML5 : Safari, iOS Safari</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Intégrations</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Intégration d’Adobe Analytics VHL</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## Matrice des fonctionnalités DASH {#dash-feature-matrix}

Voici la matrice des fonctionnalités des fonctionnalités DASH dans le navigateur TVSDK.

・ *DASH Core playfeatures*

・ *DASH Fonctions de lecture avancées*

・ *DASH Protection du contenu*

・ Fonctions *DASH Core et d&#39;insertion*

・ *DASH Fonctions avancées d&#39;insertion de publicités*

・ Intégrations *DASH*

>[!NOTE]
>
>Dans les tableaux de la matrice des fonctionnalités ci-dessous, un Y signifie que la fonctionnalité est prise en charge dans la version actuelle.

### Fonctions DASH {#dash-features}

Les fonctionnalités suivantes sont prises en charge :

**Tableau 10 : Fonctions de lecture DASH Core**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Category</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>HTML5 FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
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
   <td><p>VOD + Live</p> </td> 
   <td><p>Débit adaptatif</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Légendes 608/708</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>WebVTT</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Basculement</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Notifications QoS et du lecteur</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Prise en charge des en-têtes de cookie</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Définition des paramètres de contrôle du tampon</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Définition des contrôles de débit binaire adaptatif</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Balises personnalisées (EventStream)</p> </td> 
   <td><p>VOD uniquement (intégré)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Audio lié tardivement</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>302 redirection</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 11 : Fonctions de lecture DASH Advanced**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Category</strong></p> </td> 
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
   <td><p>Lecture audio uniquement</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Trump play</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Lecture lisse</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Analyse ID3</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Prise en charge de plusieurs périodes</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Flux jetables</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Lecture</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Facturation</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 12 : Fonctions de protection du contenu DASH**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Category</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>HTML5 FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Protection du contenu</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>AES-128</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Protection du contenu</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Sample-AES</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Protection du contenu</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>DRM</p> </td> 
   <td><p>・ Widevine sur Chrome, Firefox 47 et versions ultérieures et Chromecast</p> <p>・ PlayReady sur Internet Explorer sous Windows 8.1 et Edge</p> <p>・ Primetime DRM pour Windows Firefox (vidéo uniquement)</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 13 : Fonctions d’insertion des annonces DASH Core**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Category</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>HTML5 FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Pré-roll (MP4/DASH)</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Mid-roll (DASH)</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Post-roll (MP4/DASH)</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>FER VOD</p> </td> 
   <td><p>Résolution et comportements des publicités</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Stratégie publicitaire par défaut</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VAST 2.0/3.0</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>VMAP 1.0</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Creative Repackaging (MP4 vers DASH)</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 14 : Fonctions avancées d’insertion de publicités DASH**

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Category</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>HTML5</strong> FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Publicité uniquement</p> </td> 
   <td><p>Y</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Paramètres de ciblage</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Paramètres personnalisés</p> </td> 
   <td><p>VOD uniquement</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Stratégie publicitaire personnalisée</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Chargement différé de publicités</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
   <td><p>VOD</p> </td> 
   <td><p>Publicités d’accompagnement, bannières publicitaires, publicités cliquables</p> </td> 
   <td><p>Non pris en charge</p> </td> 
  </tr> 
  <tr> 
   <td><p>Insertion d'une publicité</p> </td> 
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
   <td><p><strong>Category</strong></p> </td> 
   <td><p><strong>Type de contenu</strong></p> </td> 
   <td><p><strong>Fonctionnalité</strong></p> </td> 
   <td><p><strong>HTML5 : FF, IE, Chrome, Android Chrome</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Intégrations</p> </td> 
   <td><p>VOD + Live</p> </td> 
   <td><p>Intégration d’Adobe Analytics VHL</p> </td> 
   <td><p><strong> </strong></p> <p>Y</p> </td> 
  </tr> 
 </tbody> 
</table>

## Problèmes résolus {#issues-fixed}

**Problèmes résolus dans la mise à jour 2.4.12 (version 204)**

Les problèmes suivants ont été corrigés dans la mise à jour 2.4.12 de Browser TVSDK version 2.4.12 (version 204) :

・ **21647**- Le kit TVSDK doit permettre la lecture automatique de la vidéo sur les appareils iOS lorsque le son est coupé.

・ **21465**- Erreur Clé système L&#39;accès refusé est reçu lors de la lecture d&#39;un flux DASH protégé par DRM après la lecture d&#39;un flux DASH Live.

・ **21442**- Activez la lecture automatique du contenu sur le Web iOS, après la lecture de la publicité preroll avec un geste de l’utilisateur.

・ **21240**- Fourni une API pour filtrer les publicités VPAID analysées à partir d&#39;Auditude/VMAP.

**Problèmes résolus dans la version 2.4.11**

Les problèmes suivants ont été résolus dans la version 2.4.11 de Browser TVSDK :

**Fonctions de lecture de base :**

・ **19192**: TVSDK implémente désormais TextFormat:bottomInset et TextFormat:safeArea. Grâce à ces améliorations, les sous-titres peuvent être repositionnés si la barre de contrôle est affichée à l’écran.

・ **21009**: Les sous-titres codés persistent à l’écran en cas de recherche par discontinuité jusqu’à ce que de nouvelles sous-titres apparaissent.

・ **21141**: La recherche de retour est rejetée en raison d’une condition de concurrence lors de l’ajout du segment.

・ **21142**: Mise à disposition de plages de lecture pouvant être recherchées lorsque le lecteur est à l’état INITIALISÉ. En raison de ces modifications, la session de  en position est désormais prise en charge.

・ **21363**: Les sous-titres 608/708 sont désynchronisés après l’insertion de publicités pour les flux DASH.

**Fonctionnalités d&#39;insertion d&#39;annonce :**

・ **21179**: Les problèmes liés au milieu du roulement (pauses longues, images noires) avec le contenu VOD sont maintenant résolus en définissant correctement la propriété ad.primaireAsset.adParameters.

・ **21257**: Le fichier MP4 avec le débit binaire le plus élevé est sélectionné pour le transcodage si MP4 n’est pas un type MIME valide et que la fonction de reconditionnement créatif est activée.

・ **21361**: TVSDK transmet désormais le système d’annonce et l’ID de création de la réponse VAST sous forme de paramètres  dans la demande d’assemblage créatif afin de prendre en charge des règles de normalisation supplémentaires.

**Problèmes résolus dans la version 2.4.10**

Les problèmes suivants ont été résolus dans la version 2.4.10 de Browser TVSDK :

**Fonctions de lecture de base :**

・ **21060**: Erreur de codec non valide générée avec les flux HLS qui contiennent une discontinuité et les zones BMFF ISO s’exécutent jusqu’à la fin du flux.

・ **21045**: La lecture automatique ne fonctionne pas sur iOS une fois la première lecture vidéo d’une liste de lecture terminée.

・ **20975**: La fréquence d’images est renvoyée sous la forme NaN par le fournisseur QoS du navigateur Chrome.

・ **20823**: Erreur de codec non prise en charge générée lors de la rencontre de segments sans données.

・ **20769**: Le SDK est désormais avec le débit binaire actuel sur la recherche au lieu de basculer immédiatement en fonction de la stratégie ABR.

・ **20031**: En mode portrait sur IE11 (Windows 8.1), l’écran vidéo devient petit. Fonction de protection du contenu :

・ **19316**: Ignorez les segments qui ne parviennent pas à décrypter dans le cas de flux AES-128 HLS.

**Problèmes résolus dans la version 2.4.9**

Les problèmes suivants ont été résolus dans la version 2.4.9 de Browser TVSDK :

**Fonctions de lecture de base :**

・ **13407**: Les flux DASH peuvent bloquer si Firefox cesse d’envoyer des  &quot;ontimeupdate&quot; au cours de la lecture.

・ **16380**: Lors de la lecture de contenu vidéo multimédia de segments dont les temps de ne correspondent pas via MSE, l’erreur de synchronisation audio entre les représentations s’accumule sur les commutateurs ABR, ce qui entraîne en fin de compte une erreur (problème de chrome n° 663686).

・ **17985**: Lors de la lecture d’un flux ISO-BMFF particulier sur le navigateur Firefox, la lecture est bloquée (numéro Firefox 1342913). Ce problème est corrigé depuis Firefox v53.

・ **19141**: Non capturé (promis) RéférenceErreur : width n’est pas défini.

・ **18997, 19299**: Problème de scintillement vidéo aux limites du segment. Cela se produisait puisque le SDK ne calculait pas correctement le décalage temporel de la dernière composition de l’échantillon.

・ **19780**: La lecture n’est pas  pour le contenu HLS et l’annonce HLS dans Firefox v53 (numéro Firefox 354653).

・ **20046**: Date  Heure de réception du en tant que clé au lieu de valeur lorsqu’elle est reçue en tant qu’objet de métadonnées minutées.

・ **20047**: useDefaultResizeHandler renvoie une erreur avec la méthode de secours Flash.

・ **20179**: Flash Fallback ne fonctionne pas avec Flash Player v25.0.0.171.

・ **20293**: Firefox arrête la mise en mémoire tampon des données pour certains flux HLS conduisant à un blocage.

・ **20626**: Le lecteur renvoie une erreur de décodage multimédia sur Chrome en raison d’une gestion incorrecte des échantillons vidéo de durée nulle.

・ **20078**: La lecture se bloque sur l’erreur de navigateur &quot;QuotaOverceeded&quot;.

・ **18639**: Dans le flux en direct HLS 608 CC, le texte apparaît parfois mal orthographié.

・ **20028**: Le paramètre de taille ClosedCaptions ne modifie pas la taille de la police.

・ **20613**: Les zones de sous-titrage codé se chevauchent, ce qui les rend illisibles.

**Fonctionnalités CSAI (Core Ad Insertion) :**

・ **20043**: Appels de suivi d’impression et de publicité manquants avec plusieurs publicités et redirections tierces.

・ **20044**: Lors de l’utilisation du reconditionnement de la création, toutes les publicités de la coupure publicitaire doivent être reconditionnées correctement, sinon la coupure publicitaire est complètement ignorée.

・ **20097**: La lecture de la publicité est ignorée et le contenu principal reprend immédiatement au lieu d’attendre un dépassement de délai de 20 secondes si le manifeste de la publicité n’est pas disponible.

**Problèmes résolus dans la mise à jour de la version 2.4.8 (version 6002)**

Les problèmes suivants ont été résolus dans la mise à jour 2.4.8 de Browser TVSDK version 2.4.8 (version 6002) :

・ **14126:** La lecture peut bloquer Firefox (numéro 1316024) en raison d’un espace interne dans la mémoire tampon source MSE. Tentez de rechercher pour reprendre la lecture.

・ **19608 :** Correctif pour honorer la valeur de décalage temporel de la réponse VMAP d’Auditude.

・ **19635 :** Correction d’un blocage vidéo dans Internet Explorer 11 sous Windows 10.

・ **19761 :** Correctifs pour les problèmes ABR avec HLS.

・ **19780 :** Correction de la lecture de la publicité avec du contenu HLS rompu dans Mozilla Firefox v53.

・ **1987 et 1974 :** Ces problèmes corrigent l’incohérence de la sélection du débit après une opération de recherche. Maintenant, la sélection du débit à la recherche est la valeur la plus faible du débit actuel et le débit au -dessus.

・ **19881 :** La lecture est bloquée et l’incrustation de mise en mémoire tampon s’affiche pendant une durée illimitée après que la recherche a été effectuée 3 à 4 fois.

・ **19884 :** Confirmez la conformité aux exigences relatives au chemin de média vérifié (VMP) de Chrome 59 bêta. bTVSDK a pu lire le contenu DRM Widevine avec Chrome 59 bêta.

・ **19916 :** La lecture DRM sur UI-Framework a été interrompue. Désormais, il invoque la propriété acquisitionLicense même s’il n’existe aucune stratégie dans les métadonnées.

**Problèmes résolus dans la version 2.4.8**

Les problèmes suivants ont été résolus dans la version 2.4.8 de Browser TVSDK :

・ **10075**: Lorsque vous recherchez avant la chronologie, la lecture du complet n’a pas été reçue sur Firefox et Chrome et la recherche de n’a pas été  sur Firefox.

・ **15775**: Lire le complet non reçu sous Windows 8.1 Internet Explorer.

・ **17306**: Pour les flux SSAI, la lecture est prise en charge. Le suivi des publicités assemblées n’est pas pris en charge.

・ **19142**: Parfois, le retour en arrière entraîne le maintien du lecteur vidéo dans l’état de mise en mémoire tampon pour toujours.

・ **19218**: Les marqueurs publicitaires ne sont pas disponibles via la structure de l’interface utilisateur.

・ **19219**: La lecture des publicités ne fonctionne pas uniquement dans le cadre de l’interface utilisateur.

・ **19222**: La clé AES-128 est demandée une seule fois pour une liste de lecture et les requêtes suivantes sont servies à partir du cache. Auparavant, il était demandé pour chaque segment.

・ **19597**: &quot;Uncatch TypeError : Impossible de lire la propriété &#39;log&#39; d’undefined&quot; a été vue avec les versions canaires de Chrome.

・ **19605**: adRequestDomain n’était pas disponible en mode de secours Flash.

・ **19608**: Les publicités VMAP n’étaient pas insérées pour les flux en direct HLS. Le SDK prend désormais en compte les marqueurs de repère et ne dépend pas des valeurs de décalage temporel dans les réponses VMAP.

・ **19637**: La lecture des publicités entraîne uniquement une erreur de script à la fin de la publicité.

・ **19732**: Les requêtes de liste de lecture CRS échouaient avec une erreur 404. Les requêtes 1401 et 1403 du navigateur TVSDK sont maintenant mises à jour pour s’en occuper.

・ **19762**: acquérirLicense était appelé avant setAuthenticationToken car une licence valide était renvoyée indépendamment de la validité du jeton. Ce problème est maintenant résolu et l’acquisitionLicense n’est appelée qu’après la réponse setAuthenticationToken.

**Problèmes résolus dans la version 2.4.7**

Les problèmes suivants ont été corrigés dans la version 2.4.7 :

・ **8397**: Les flux en direct HLS générés via Adobe Media Server peuvent ne pas être lus si les segments ne  pas avec un cadre de clé.

・ **13606**: Plusieurs problèmes liés à la recherche ont été résolus pour le flux HLS sur le navigateur Chrome.

・ **14807**: Dans le navigateur Chrome, si la recherche ou la mise en pause est déclenchée immédiatement après play(), la lecture peut s’arrêter avec l’erreur DOMException : La requête play() a été interrompue par un appel...(numéro de chrome 593273).

・ **19085**: Les paramètres MediaPlayer tels que volume, abrControlParameters et ccStyle ne sont pas définis sur Valeurs par défaut lors de la réinitialisation du lecteur.

**Problèmes résolus dans la version 2.4.6**

Le problème suivant a été corrigé dans la version 2.4.6 :

・ **18093**: Les métadonnées de la balise en regard de la balise abonnée sont renvoyées lorsque vous utilisez la version 24 de Flash Player en mode de secours Flash.

**Problèmes résolus dans la version 2.4.4**

Les problèmes suivants ont été corrigés dans la version 2.4.4 :

・ **8711**: Avec MSE, les légendes 608/708 restent justifiées par défaut.

・ **13934**: Les paramètres ABR pour les publicités ne sont pas applicables lors de la lecture de flux en direct HLS.

・ **14079**: La longévité des flux HLS Live avec une fenêtre DVR faible peut échouer, car la lecture peut être en retard en raison de problèmes de latence du réseau. Cliquez sur le point de lecture pour reprendre la lecture.

・ **15037**: Les exemples fournis avec la structure de l’interface utilisateur du lecteur ne fonctionnent pas avec Microsoft Internet Explorer 10 sous Windows 7.

・ **15913**: Pour les flux VOD HLS, sur Chrome, le flux ne se lit pas si la réponse du manifeste est 304 n’est pas modifiée. Ce problème est corrigé depuis Chrome v55 (numéro de chrome 633696).

・ **16103**: Sous Android Chrome, dans des conditions de faible bande passante, la lecture peut échouer avec l’erreur TypeError non interceptée : Impossible de lire la propriété &quot;programDateTime&quot; d&#39;une erreur non définie.

・ **16265**: Pour les flux VOD HLS et Live, la recherche entre les discontinuités ne fonctionne pas.

・ **16709**: La reprise du flux en direct HLS avec PDT et le marqueur de discontinuité peut entraîner le blocage du lecteur dans la mise en mémoire tampon.

## Problèmes connus et limites {#known-issues-and-limitations}

Les limitations et les problèmes connus dans le SDK du navigateur sont mentionnés ci-dessous.

**Tableau 16 : Fonctions de lecture principales**

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
   <td>VOD + Live</td> 
   <td>Lecture générale (Lecture, Pause, Recherche)</td> 
   <td><p>・ Les formats de médias autres que HLS ne sont pas pris en charge.</p> <p>8799 : La fonction de secours Flash ne prend pas en charge le contenu mixte et doit donc s’assurer que le contenu, les publicités et les autres URL ne génèrent pas de contenu mixte (contenu sécurisé et non sécurisé ensemble).</p> <p>・ 19271 : La lecture de plusieurs vues via la structure d’interface utilisateur n’est pas prise en charge en mode de secours Flash.</p> <p>・ La fonction de secours Flash ne fonctionne pas sur Microsoft Internet Explorer 8 et 9 sous Windows 7, car ces versions ne sont pas prises en charge par le SDK.</p> <p>・ 20262 : La fonction de secours Flash ajoute des paramètres personnalisés aux  d’informations de ciblage. L’ordre de priorité des paramètres personnalisés est également différent dans le cas de Flash et de MSE.</p> <p>・ 20653:Le lecteur TVSDK Flash de secours ne fonctionne pas sur Win10 avec Creators Update.</p> <p>・ Flash Fallback fonctionne avec Flash Player version 23 et ultérieure.</p> <p>・ 20087 - Version bêta de Chrome 59 avec</p> <p>Flash 25.0.0.171</p> <p>Bêta (par défaut), la lecture HLS ne fonctionne pas en mode de secours Flash. Ça marche bien sur Canary.</p> </td> 
   <td><p>・ 12563: Les flux de données avec le codec audio mp4a.40.02 ne sont pas lus dans Firefox en raison d’une chaîne de codec audio non prise en charge dans la MPD. Le codec audio mp4a.40.2 est pris en charge.</p> <p>15029 : Lors du passage d’une vidéo à une autre dans multiView dans UI-Framework, le bouton Lecture/Pause n’est pas mis à jour en conséquence.</p> <p>・ 16034:Sous Windows 8.1 IE, l'appel de reset() conduit à une erreur de type MIME inconnu. Veuillez recharger le média pour reprendre la lecture.</p> <p>・ 18235: Certains problèmes de recherche sont observés avec les flux de votes DASH avec des publicités.</p> <p>・ 18727: L’API d’erreur n’est pas prise en charge pour MSE</p> <p>18750 : Dans certains cas, le des modifications d’état peut être hors service pour le SDK et la structure de l’interface utilisateur, et dans la structure de l’interface utilisateur, les IDLE et Initialization StatusChange peuvent être absents pour les  des écouteurs d’état ajoutés après le chargement de la ressource.</p> <p>・ 18889 : Si MediaPlayer est à l’état ERROR, l’objet  du n’est pas renvoyé.</p> <p>・ 19039 : Si AdobePSDK. MediaPlayer. La fonction searchToLocal() est utilisée avec une valeur supérieure à EOF, puis le de lecture commence dans le cas de MSE.</p> <p>・ 19049 : Aucun état d’erreur n’est signalé pour Flash Player sur Chrome, IE, Firefox lorsque la vidéo est bloquée pendant la lecture.</p> <p>・ 17205: La lecture vidéo s’interrompt pendant quelques heures sur la lecture d’un flux non muxé pendant que la lecture audio se poursuit (numéro Chromium 664033).</p> <p>・ 12308: Dans les flux DASH avec composition_time_offset spécifié, timeStampOffset peut lui être appliqué sur le navigateur Chrome, ce qui entraîne une durée de décodage négative. Par conséquent, MEDIA_ERR_ SRC_NOT_ Erreur PRISE EN CHARGE (Problème de chrome #398141).</p> <p>・ 14126: La lecture peut bloquer Firefox (numéro de publication 1316024) en raison d’un espace interne dans la mémoire tampon source MSE. Essayez de rechercher pour reprendre la lecture.</p> <p>・ 1915 : MS Edge et IE 11 (Win 8.1 et 10) ne définissent pas  sur null lors de la redirection CORS et échoue pourtant, car l’en-tête n’est pas nul et entraîne une erreur de lecture.</p> <p>・ 19861:Problème avec le comportement d'ajout sur la mémoire tampon source pour les médias déjà lus. Chrome rejette le fragment annexé, y compris moov, provoquant une erreur de décodage ultérieure. (numéro Chromium 735335)</p> <p>19921 : La lecture se bloque pour certains contenus HLS, même si leur mise en mémoire tampon a réussi (numéro Chromium 713540)</p> <p>・ 2044:La recherche de la fin de la plage mise en mémoire tampon sur IE et Edge peut entraîner le blocage de la lecture.</p> <p>・ 20511 : Parfois, le rejet de recherche peut être observé pour les flux HLS avec ou sans publicité.</p> <p>・ 20743 : Sous Windows 10 Chrome, le flux en direct HLS est lu pendant quelques secondes avant la lecture MP4 preroll.</p> <p>・ 21043 : La dimension de la vidéo peut ne pas être correcte lors du chargement initial en raison d’un manque de métadonnées.</p> <p>・ 21115: Un geste de l’utilisateur Android est nécessaire pour  la lecture si une publicité preroll est disponible pour les vidéos d’une liste de lecture.</p> <p>・ HLS Live ne prend pas en charge le roulement de l'horodatage.</p> <p>・ Le son AAC-SSR n'est pas pris en charge.</p> <p>Les codecs audio AC3 et AC3 amélioré ne sont pas pris en charge.</p> <p>・ Pour les cours d’eau avec discontinuité d’horodatage mais sans marqueurs de discontinuité</p> <p>・ La lecture peut avoir des problèmes et une recherche incorrecte en raison des sauts.</p> <p>・ La durée du contenu et la durée de lecture peuvent ne pas correspondre.</p> <p>・ Les discontinuités entre les représentations et les rendus doivent correspondre à d'autres éléments sages peuvent entraîner des problèmes de synchronisation et de blocage.</p> <p>・ Les légendes et WebVTT peuvent ne pas apparaître près de la fin du flux.</p> <p>・ Les modifications du codec audio ne sont pas prises en charge dans les sauts d’horodatage.</p> <p>・ L’insertion d’une publicité n’est pas prise en charge.</p> <p>・ Le mode Avance rapide peut conduire à une boucle de lecture sous Win 8.1 IE 11 (numéro MS #12446268).</p> <p>DASH :</p> <p>・ Pour les flux en direct - les  dynamiques de type dynamique sont prises en charge.</p> <p>・ Pour les flux VoD - les  en direct avec type statique sont prises en charge.</p> <p>Pour les flux VoD : le  à la demande n’est pas certifié pour les  publicitaires.</p> </td> 
   <td><p>・ Les flux DASH Live et DASH Video on Demand ne sont pas pris en charge.</p> <p>・ La lecture vidéo PIP (Image en image) n’est pas prise en charge sur iOS en mode plein écran.</p> <p>Dans l’extension Safari (balise vidéo) moins manifeste sans en-tête de type de contenu correct, ne fonctionnent pas.</p> </td> 
   <td><p>・ applicationID dans l’application d’expéditeur doit être identique à celle générée lors de l’enregistrement de l’URL du destinataire en tant qu’application de destinataire personnalisée.</p> <p>・ Le lecteur de référence est certifié pour les  DASH. La structure de l’interface utilisateur n’est pas certifiée.</p> <p>Pour  des codecs de média pris en charge, reportez-vous <a href="https://developers.google.com/cast/docs/media"><em>à cette</em></a>rubrique.</p> </td> 
  </tr> 
  <tr> 
   <td>FER VOD</td> 
   <td>Lecture générale (Lecture, Pause, Recherche)</td> 
   <td> </td> 
   <td>18098 : Certains problèmes de recherche sont observés avec le flux d’accès libre HLS LBA FER.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Débit adaptatif</td> 
   <td><p>・ 20079 : Réécriture de la mémoire tampon lors de la recherche dans une plage mise en mémoire tampon.</p> <p>2008 : Le comportement de Flash ABR est cohérent avec MSE.</p> </td> 
   <td><p>・ La variante de secours audio uniquement dans un flux ABR est ignorée en raison des limitations liées à la mise en mémoire tampon.</p> <p>・ 12289: Les paramètres de contrôle ABR ne s’appliquent pas aux fichiers audio en cas de flux HLS/DASH non muxés.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Légendes 608/708</td> 
   <td> </td> 
   <td><p>・ 7810: Sur Android 4.4.4, Chrome ne semble pas prendre en charge les familles de polices CSS de base utilisées par le lecteur et ne fonctionne donc pas.</p> <p>・ Le CC ne peut être modifié dans le cas de 608 sous-titres.</p> <p>・ Les fonctions de mise en forme avancée ne sont pas prises en charge pour 608 légendes.</p> <p>Les légendes intégrées (608/708), signalées par l’intermédiaire de la balise Accessibilité, sont prises en charge.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>WebVTT</td> 
   <td> </td> 
   <td><p>・ 5206 : Les balises de région du fichier WebVTT sont ignorées par le lecteur lors de l’affichage des légendes.</p> <p>・ DASH : Les fichiers VTT fragmentés/segmentés ne sont pas pris en charge.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Basculement du manifeste</td> 
   <td>21056 : Avec Flash Fallback, le basculement n’a pas lieu pour le flux en direct si le flux principal renvoie une erreur 404 pendant la lecture.</td> 
   <td>Le basculement du manifeste ne s’applique qu’au contenu et non aux publicités.</td> 
   <td>Le basculement de liste de lecture manquant fonctionne sur Safari uniquement pour le code d’erreur HTTP 404.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Basculement avancé</td> 
   <td> </td> 
   <td><p>・ Le basculement de segment ne prend pas en charge la saut de segments indisponibles et la lecture continue.</p> <p>20533 : Les segments manquants dans une liste de lecture doivent être traités comme une discontinuité et la lecture doit reprendre à partir du segment disponible suivant.</p> <p>21267 : Le basculement de flux en raison d’un basculement peut entraîner le téléchargement de segments plus anciens.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Notifications QoS et Player</td> 
   <td>21129 : La fréquence d’images n’est pas disponible en cas de reprise Flash.</td> 
   <td><p>• 11170:</p> <p>Timed_n’est pas disponible pour le SDK Browser TVSDK avec MSE, contrairement au SDK Browser TVSDK avec Flash Fallback.</p> <p>21129 : Le débit d’images n’est pas calculé pour les flux en direct.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Prise en charge des en-têtes de cookie</td> 
   <td> </td> 
   <td> </td> 
   <td><p>L’indicateur withCredentials et les en-têtes de cookie ne sont pas pris en charge dans Safari.</p> <p>21051 : Pour autoriser les cookies dans Safari, activez le paramètre "Cookies et données du site Web" dans Préférences &gt; Confidentialité.</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Balises personnalisées</td> 
   <td>14763 : Les balises personnalisées autres que le fait de commencer par # ne doivent pas être prises en charge. Actuellement, l’objet TimedMetadata est créé et rapporté pour de telles balises lors d’un abandon Flash.</td> 
   <td>Les flux comportant des balises personnalisées intégrées ne sont pas certifiés.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Audio de liaison tardive</td> 
   <td> </td> 
   <td><p>・ L’insertion d’une publicité n’est pas prise en charge avec les flux LBA en direct HLS.</p> <p>・ 17273: Les flux LBA HLS VOD passent au rendu par défaut en cas de basculement et ne peuvent pas être rétablis sur la dernière sélection.</p> <p>・ 20251 : Le flux LBA en direct HLS peut bloquer la recherche.</p> <p>・ 20497 : Le lecteur reste en état de mise en mémoire tampon si les flux non muxés HLS LBA ne comportent pas d’images audio ou vidéo à proximité de la fin du flux.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>302 Redirection</td> 
   <td> </td> 
   <td><p>15787: 302</p> <p>l’optimisation de la redirection n’est pas prise en charge sur les navigateurs Windows Edge et IE, car elle ne prend pas en charge la propriété responseURL dans l’objet XMLHttpRequest.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 17 : Fonctions de lecture avancées**

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
   <td><p>Le démarrage de la lecture à une valeur de décalage particulière n’est pas pris en charge pour le contenu MP4.</p> </td> 
   <td>20492 : Les publicités de milieu de gamme précédant le décalage sont lues avant que le contenu ne reprend de la valeur de décalage.</td> 
   <td>La lecture avec décalage n’est pas prise en charge sous iOS.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>Lecture de Trick</td> 
   <td>La fonction de lecture en continu ne fonctionne pas pour les flux sans rendu d’iFrame.</td> 
   <td><p>・ Les adaptations de la méthode Trick Play ne sont pas prises en charge sur Firefox et Internet Explorer et le mode de la méthode inverse n’est donc pas disponible sur ces navigateurs.</p> <p>・ La lecture de texte en vidéo n’est pas disponible lorsque vous lisez du contenu avec des publicités.</p> <p>・ 10435: Pendant la lecture DASH, la vidéo se bloque lors de la lecture de l’astuce avancée sur Internet Explorer (Win 8.1)</p> <p>par intermittence. Cela se produit puisque nous utilisons la propriété playbackRate des éléments vidéo sans l’adaptation de lecture de l’astuce.</p> <p>14182 : Parfois, lors d’un retour en arrière sur le navigateur Chrome, il est possible que les  de recherche ne soient pas reçues et que le mode de ruse ne fonctionne donc pas.</p> <p>・ 14942: Les taux de lecture peuvent être définis sur Chrome pour Android, même en cas de flux de lecture non liés aux astuces, mais le paramètre n’est pas appliqué et la lecture se poursuit à un rythme normal.</p> <p>・ 17308: Seek ne fonctionne pas en mode Trickplay.</p> <p>・ 17309: Dans le navigateur Chrome, le mode de ruée inverse ne peut pas durer plus de 2 secondes.</p> <p>19272 : Dans le cas de flux DASH, la lecture de la vidéo peut ne pas être récupérée après la mise en mémoire tampon sur le navigateur Windows 10 Edge.</p> </td> 
   <td>Le mode Rembobinage n’est pas pris en charge.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Analyse ID3</td> 
   <td>20346 : L’octet de codage de texte des images ID3 doit également être renvoyé par le SDK.</td> 
   <td><p>Les balises ID3 disponibles dans les flux de transport de données audio (ADTS) sont ignorées par le SDK.</p> <p>・ 12378: Les métadonnées minutées ID3 sont analysées à différents moments dans Flash et le navigateur avec la prise en charge de MSE. Par conséquent, le comportement d’affichage sur la chronologie du lecteur de référence est également différent.</p> <p>・ 19247 : L’analyse ID3 n’est pas prise en charge sur la structure de l’interface utilisateur.</p> </td> 
   <td><p>・ 20323 : La balise PRIV ID3 utilisée pour signaler l’horodatage du premier échantillon de segment ac n’est pas analysée par Safari (numéro Safari #32422733)</p> <p>・ 20350 : Sur certains périphériques (y compris MAC OS X 10.1, iPad 10), Safari ne fournit pas de de changement de repère  en mode "secret" et donc les images ID3 ne sont pas reçues. (numéro Safari 32450526)</p> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Prise en charge des marqueurs de discontinuité</td> 
   <td> </td> 
   <td><p>・ L'insertion de publicités côté client n'est pas prise en charge avec les flux HLS contenant des discontinuités.</p> <p>・ Le changement du codec audio n’est pas autorisé dans les discontinuités du flux HLS.</p> <p>・ Le commutateur de piste audio n’est pas pris en charge pour le flux HLS avec des marqueurs de discontinuité</p> </td> 
   <td>Le numéro de séquence de discontinuité est une condition requise pour les flux HLS avec discontinuité afin de pouvoir lire sur Safari.</td> 
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
   <td>VOD + Live</td> 
   <td>AES-128</td> 
   <td> </td> 
   <td>La plage d’octets n’est pas prise en charge avec le contenu chiffré AES-128.</td> 
   <td>12324 : La lecture des flux chiffrés HLS AES-128 échoue sur Safari si la balise IV n’est pas spécifiée.</td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD</td> 
   <td>DRM</td> 
   <td> </td> 
   <td><p>・ 12660: Le lecteur HTML5 renvoie une erreur interne du serveur pour le contenu du tiret chiffré PlayReady expiré.</p> <p>・ 16720: Le contenu chiffré DASH DRM ne fonctionnera pas si l’attribut de  dans la balise period est manquant.</p> <p>・ 18589 : La lecture n’est pas prise en charge pour les flux VoD multipériode Dash protégés DRM avec Xlink.</p> <p>・ 18653 : La lecture du contenu multipériode Widevine avec plusieurs clés s’arrête au premier point et ne peut pas passer à la période suivante.</p> <p>・ 18656 : Le flux multi-période prêt à l’emploi, chiffré avec différentes clés, ne peut pas être lu.</p> <p>Playready 2.0 pour le tiret n’est pas certifié.</p> <p> </p> <p> </p> </td> 
   <td>12602: Les métadonnées DRM HLS Fairplay sont régulièrement actualisées par le lecteur HTML5 sur Safari.</td> 
   <td><p>DASH Le contenu DRM Widevine emballé par Bento4 peut être lu. Le contenu compressé via Offline Packager et Shaka Packager ne s’exécute pas. DASH PlayReady DRM n’est pas pris en charge.</p> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 19 : Fonctions d’insertion d’annonces principales (CSAI)**

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
   <td>VOD + Live</td> 
   <td>Pré/Mid/Publication</td> 
   <td> </td> 
   <td><p>・ Les publicités preroll avec contenu HLS en direct sont lues en mode Double lecteur.</p> <p>・ Les publicités DASH avec contenu HLS et HLS avec contenu DASH ne sont pas prises en charge.</p> <p>・ 19002 : Dans le lecteur HTML5 avec MSE adBreak. insertType ne renvoie pas la valeur correcte pour indiquer le type d'insertion correct, c'est-à-dire le client inséré et/ou le serveur inséré.</p> <p>7794 : Sur les périphériques mobiles (iOS, Android avec Chrome 33 ou version antérieure ou Navigateur natif) où la barre de contrôle par défaut est visible en mode Plein écran, la barre de recherche et les boutons Avance rapide sont disponibles lors de la lecture des publicités.</p> <p>・ 11048: Le passage du contenu en direct HLS à la publicité n’est pas aisé dans le cas des extensions Media Source.</p> <p>・ 16083: Sous Android 4.4 Chrome v52, il arrive que des publicités HLS avec contenu HLS génèrent une erreur de décodage de pipeline après une lecture bloquée.</p> <p>・ 16097: Les erreurs survenues pendant la coupure publicitaire ne sont pas gérées, ce qui peut entraîner l’arrêt de la lecture du flux principal.</p> <p>・ 18095 : Les publicités MP4 ne sont pas prises en charge avec le contenu en direct HLS.</p> <p>19120 : Plusieurs recherches sur des annonces HLS avec contenu HLS peuvent entraîner l’arrêt de la lecture du flux.</p> <p>・ 19131 : L’incrustation de mise en mémoire tampon peut s’afficher lors du passage d’une coupure publicitaire preroll au contenu.</p> <p>・ 20296 : Dans le cas des flux HLS Live, la recherche dans la fenêtre DVR suivie de la recherche sur les rouleaux moyens résolus peut entraîner un blocage de la lecture.</p> <p>・ 20298:HLS Flux en direct avec des rouleaux moyens bloquent dès que le premier rouleau moyen est sorti de la fenêtre du RVV.</p> <p>・ 20317 : Les flux en direct HLS peuvent bloquer lors du passage à la publicité suivante ou de la publicité au contenu au cas où une coupure publicitaire contiendrait plusieurs publicités.</p> 
    <ul> 
     <li>Les publicités dans la fenêtre DVR des flux en direct HLS ne sont pas résolues.</li> 
    </ul> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>Le SDK ne respecte pas l’attribut de séquence dans la réponse VMAP pour VAST adSource.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VAST 2.0/3.0</td> 
   <td> </td> 
   <td>20779 : Le SDK ne respecte pas l’attribut de séquence dans la réponse VMAP pour VAST adSource.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>VMAP 1.0</td> 
   <td> </td> 
   <td>12014 : L’attribut de répétition VMAP n’est pas pris en charge.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Creative Repackaging</td> 
   <td> </td> 
   <td>21464 : La réponse à la publicité est complètement ignorée si le reconditionnement de la création échoue pour l’une des publicités de la coupure publicitaire.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 20: Fonctionnalités avancées d&#39;insertion d&#39;annonce (CSAI)**

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
   <td>20056 : La propriété de technologie du lecteur n’est pas pertinente, car elle est basée sur le contenu principal, vide en cas de lecture de la publicité uniquement.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>VOD + Live</td> 
   <td>Stratégie d'annonce personnalisée</td> 
   <td> </td> 
   <td><p>・ Les comportements publicitaires ne sont pas pris en charge avec les publicités MP4 et le contenu MP4.</p> <p>・ 13973: Comportements publicitaires personnalisés : la stratégie SKIP ne renvoie pas de  complète lorsqu’elle est utilisée avec MSE.</p> <p>・ 14939 : Les règles de comportement d’annonce personnalisées ignorent et ignorent les coupures publicitaires ne fonctionnent pas pour le contenu DASH.</p> <p>・ 17131: La première image de la publicité est visible, puis le contenu reprend en cas de stratégie de coupure publicitaire SKIP.</p> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>Publicités complémentaires/ bannières publicitaires/ Publicités cliquables</td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td>Les bannières publicitaires ne sont pas visibles lors de l’utilisation du lecteur de référence.</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>VPAID 2.0</td> 
   <td> </td> 
   <td><p>・ Les comportements publicitaires ne sont pas pris en charge pour les annonces VPAID.</p> <p>・ 15032: Les publicités VPAID en combinaison avec les publicités MP4 ou HLS lors d’une coupure publicitaire ne sont pas prises en charge.</p> <p>・ 19001 : Sous Android et iOS, lorsque la publicité VPAID est lue avec le format MP4 comme contenu principal,  les pistes audio sont audibles, l’une du contenu principal et l’autre de la publicité.</p> <p>・ 20762 : Les publicités VPAID ne sont pas prises en charge avec l’option Image dans l’image (PIP).</p> <p>・ 21172: La lecture du complet n’est pas reçue pour le contenu VOD HLS avec des publicités VPAID.</p> <p>・ 21173: onAdBreakCompleteEvent n’est pas reçu pour le contenu VOD HLS et les publicités VPAID post-roll.</p> </td> 
   <td>Le lecteur bascule entre le mode normal et le mode plein écran lors du basculement entre la publicité VPAID et le contenu principal.</td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

**Tableau 21: Intégrations**

| **Type de contenu** | **Fonctionnalité** | **Flash** | **HTML5 dans Firefox, IE, Chrome, Android Chrome** | **HTML5 dans Safari, iOS Safari** | **Chromecast (lecture DASH uniquement)** |
|---|---|---|---|---|---|
| VOD + Live | Intégration d’Adobe Analytics VHL |  | 1904 : Le suivi des analyses vidéo n’est pas disponible via l’outil de configuration de l’interface utilisateur. |  |  |

## Ressources utiles {#helpful-resources}

* Reportez-vous à la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.