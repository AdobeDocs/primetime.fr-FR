---
title: Notes de mise à jour de TVSDK 1.4 pour iOS
description: Les notes de mise à jour de TVSDK 1.4 pour iOS décrivent les nouveautés ou les modifications, les problèmes résolus et connus et les problèmes liés aux périphériques dans TVSDK iOS 1.4
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '6549'
ht-degree: 0%

---

# Notes de mise à jour de TVSDK 1.4 pour iOS {#tvsdk-for-ios-release-notes}

Les notes de mise à jour de TVSDK 1.4 pour iOS décrivent les nouveautés ou les modifications, les problèmes résolus et connus et les problèmes d’appareil dans TVSDK iOS 1.4.

## Nouvelles fonctionnalités {#new-features}

**Version 1.4.45**

* Pour se conformer à Xcode10, TVSDK est passé de &quot;`libstdc++`&quot; à &quot;`libc++`&quot;, et par conséquent, la version minimale prise en charge est iOS 7. Auparavant, c’était iOS 6.

**Version 1.4.44**

* Aucune nouvelle fonctionnalité ni amélioration dans cette version.

**Version 1.4.43**

* Expérience de type télévision de possibilité de rejoindre au milieu d’une publicité sans déclencher de suivi de publicité partielle.\
  Exemple : l’utilisateur se joint au milieu (à 40 secondes) d’une coupure publicitaire de 90 secondes composée de trois publicités de 30 secondes. Cette coupure intervient 10 secondes dans la seconde publicité.

   * La deuxième publicité est lue pendant la durée restante (20 secondes), suivie de la troisième publicité.
   * Les dispositifs de suivi des publicités pour la publicité partielle lue (deuxième publicité) ne sont pas déclenchés. Les dispositifs de suivi de la troisième publicité uniquement sont déclenchés.

* Ajout de la propriété enableVodPreroll de type booléen dans l’interface PTAdMetadata. La propriété peut être utilisée pour activer le preroll sur un flux VoD. Si enableVodPreroll a la valeur NO, PSDK ne joue pas de preroll. Ceci, cependant, n&#39;a aucun impact sur les midrolls. La valeur par défaut de enableVodPreroll est YES.
* L’API closedCaptionDisplayEnabled de l’interface PTMediaPlayer est marquée comme obsolète à partir d’iOS v1.4.43. Pour déterminer si des sous-titres sont disponibles pour un élément PTMediaPlayerItem donné, examinez la propriété subtitlesOptions de PTMediaPlayerMediaItem.

**Version 1.4.42**

Aucune nouvelle fonctionnalité n’est ajoutée dans cette version. Pour obtenir une liste des problèmes résolus, voir Problèmes résolus.

**Version 1.4.41**

Modifications des API :

* **isSecure**: une nouvelle API est introduite avec isSecure pour empêcher le lecteur d’enregistrer et de lancer une erreur. La valeur par défaut est true.
* **allowExternalRecording**: une nouvelle API est introduite pour permettre la mise en miroir de la lecture pour un contenu sécurisé. La mise en miroir des diffusions est traitée comme un enregistrement. Par conséquent, la valeur allowExternalRecording doit être définie sur &quot;True&quot; pour permettre la mise en miroir des diffusions ou définie sur &quot;False&quot; pour arrêter la mise en miroir des diffusions pour un contenu sécurisé. Par défaut, la valeur est true.

**Version 1.4.40**

Aucune nouvelle fonctionnalité.

**Version 1.4.39**

* iOS TVSDK est certifié avec VHL 2.0.1 et avec VHL 2.0.1 avec Nielsen.
* iOS TVSDK est mis à jour pour envoyer des requêtes CRS du nouvel hôte Akamai. `primetime-a.akamaihd.net`.
* La nouvelle configuration du nom d’hôte permet la diffusion de ressources CRS via HTTP et HTTPS (SSL) à plus grande échelle.

**Version 1.4.36**

Intégrer et certifier VHL 2.0 dans iOS TVSDK : réduisez la barrière de mise en oeuvre de VideoHeartbeatsLibrary en réduisant la complexité des API.

**Version 1.4.34**

* Informations sur la publicité réseau

  Les API TVSDK fournissent désormais des informations supplémentaires sur les réponses VAST tierces. L’identifiant de publicité, le système d’annonces et les extensions d’annonce VAST sont fournis dans `PTNetworkAdInfo` accessible via  `networkAdInfo`  sur une ressource publicitaire. Ces informations peuvent être utilisées pour l’intégration à d’autres plateformes Ad Analytics telles que **Analyses de cheminement**.

**Version 1.4.31**

* **Mesures de facturation** Pour tenir compte des clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte les mesures d’utilisation et les utilise pour déterminer le montant de facturation des clients.

Chaque fois que TVSDK génère un événement de démarrage de flux, le lecteur commence à envoyer régulièrement des messages HTTP au système de facturation de l’Adobe. La période, appelée durée facturable, peut être différente pour le contenu VOD standard, le pro VOD (publicités mid-roll activées) et le contenu en direct. La durée par défaut de chaque type de contenu est de 30 minutes, mais votre contrat avec Adobe détermine les valeurs réelles.

* **Prise en charge multi-réseau de diffusion de contenu pour les annonces CRS** TVSDK prend désormais en charge le multicanal CDN pour les publicités CRS. En fournissant des détails FTP pour les annonces CRS, vous pouvez spécifier des emplacements de réseau de diffusion de contenu autres que le réseau de diffusion de contenu par défaut détenu par l’Adobe, tel qu’Akamai.

**Version 1.4.29**

Dans la classe PTSDKConfig , l’API forceHTTPS a été ajoutée.

La classe PTSDKConfig fournit des méthodes pour appliquer SSL aux demandes envoyées aux serveurs Adobe Primetime Ad Decisioning, DRM et Video Analytics. Pour plus d’informations, voir `forceHTTPS` et `isForcingHTTPS` sur cette classe. Si un manifeste est chargé via HTTPS, TVSDK conserve l’utilisation du contenu de HTTPS et respecte cette utilisation lors du chargement des URL relatives à partir de ce manifeste.

**Remarque**: les requêtes envoyées à des domaines tiers tels que les pixels de suivi des publicités, les URL de contenu et de publicités, ainsi que les requêtes similaires ne sont pas modifiées. Il incombe aux fournisseurs de contenu et aux serveurs de publicités de fournir les URL prises en charge par HTTPS.

**Version 1.4.18**

Primetime iOS TVSDK prend désormais en charge les créatifs JavaScript VPAID 2.0 pour permettre une expérience publicitaire interactive riche en flux continu.

Pour plus d’informations sur VPAID 2.0, voir [Prise en charge des publicités VPAID](../programming/tvsdk-1.4-for-ios/ad-insertion/c-psdk-ios-1.4-vpaid-2.0-ads.md).

**Version 1.4.17**

* tvOS

  TVSDK prend en charge les applications natives tvOS.
* Les types de contenu suivants peuvent être lus :

   * VOD
   * En direct
   * AES-128
   * Autre audio et sous-titres
   * FER

* Les types de publicités suivants peuvent être affichés :

   * De base
   * VAST2
   * VAST3
   * VMA

* Les fonctionnalités suivantes ne sont actuellement pas prises en charge :

   * Digital Rights Management (DRM)
   * Bannières publicitaires
   * TV Markup Language (TVML)

**Version 1.4.13**

**Remarque**: le module Nielsen a été supprimé de la version TVSDK ; TVSDK sera bientôt mis à jour avec un nouveau module d’intégration Nielsen.

* **Secours de la publicité, enchaînement des publicités dans la logique de sélection des publicités (Zendesk #3103)**

Pour les publicités VAST (créatives) avec la règle de secours activée, TVSDK traite une publicité avec un type MIME non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.

Pour plus d’informations, voir [Reprise de publicité pour les publicités VAST et VMAP](../programming/tvsdk-1.4-for-ios/ad-insertion/c-psdk-ios-1.4-ad-fallback.md).

**Version 1.4.9**

* **Signalisation par blackout avec remplacement de contenu alternatif**

Dans le cadre de la mise à jour de la version 1.4 de TVSDK, nous prenons également en charge le passage et le retour de pannes régionales contre le contenu linéaire. TVSDK peut désormais traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d’interruption même lorsque des programmes alternatifs sont affichés à la place de la programmation d’origine.

**Version 1.4.8**

* **Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.5**

   * Possibilité d’envoyer des métadonnées avec le démarrage de la vidéo et/ou vidéo/ad/chapitre en tant que données contextuelles
   * Moins de trafic réseau : les pulsations sont moins nombreuses en moyenne et de taille inférieure.

**Version 1.4.7**

* **Prise en charge de l’individualisation sur site**

Prise en charge des installations on-premise du serveur d’individualisation Adobe pour personnaliser la demande d’individualisation du client afin d’accéder à un autre point de terminaison.

* **Protection des sorties basée sur la résolution**

Les stratégies DRM peuvent désormais spécifier la résolution la plus élevée autorisée, en fonction des fonctionnalités de protection de sortie de l’appareil. Par exemple, &quot;Si HDCP est disponible, autorisez la lecture du contenu jusqu’à une résolution 1 080p, et si HDCP n’est pas disponible, autorisez la lecture du contenu jusqu’à une résolution 480p&quot;.

**Version 1.4.4**

* **Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.4.1.1**

   * Ajout de la possibilité de regrouper différents cas d’utilisation d’analyse, à partir d’autres SDK ou lecteurs, avec les composants vidéo essentiels d’Adobe Analytics.
   * Le suivi des publicités a été optimisé en supprimant les méthodes trackAdBreakStart et trackAdBreakComplete . La coupure publicitaire est déduite des appels des méthodes trackAdStart et trackAdComplete .
   * La propriété playhead n’est plus nécessaire lors du suivi des publicités.
   * Ajout de la prise en charge de l’identifiant visiteur Marketing Cloud.

* **Intégration du SDK Nielsen**

   * TVSDK prend désormais en charge l’envoi de balises mTVR et MDPR ID3 au SDK Nielsen sans intégration personnalisée. Pour commencer, téléchargez le SDK de l’application Nielsen iOS 3.1.2.19.

**Version 1.4.0**

* **Signalisation par blackout avec remplacement de contenu alternatif**

   * Dans le cadre de la mise à jour de la version 1.4 de TVSDK, TVSDK prend également en charge l’entrée et le retour de pannes régionales de contenu linéaire. TVSDK peut désormais traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d’interruption même lorsque des programmes alternatifs sont affichés à la place de la programmation d’origine.

* **Supprimer/Remplacer des publicités C3**

   * Désormais, aucun travail de préparation supplémentaire n’est nécessaire pour insérer dynamiquement de nouvelles publicités dans les ressources vidéo à la demande (VOD) qui sortent de la fenêtre C3. TVSDK fournit désormais une API pour supprimer des plages de contenu personnalisées et insérer dynamiquement de nouvelles publicités. Cette nouvelle fonctionnalité puissante est également utile dans les cas où le contenu en direct/linéaire est diffusé pendant la diffusion et est immédiatement retiré pour être utilisé comme contenu à la demande sans temps approprié pour &quot;nettoyer&quot; la ressource.

## Certification et prise en charge des périphériques dans la version 1.4 {#device-certification-and-support-in}

>[!NOTE]
>
>Les fonctionnalités suivantes sont disponibles : **not** pris en charge dans TVSDK :
>
>* Déplacement lent, sur n’importe quelle plateforme ou version.
>* Jouer aux tours en direct.

**Version 1.4.43**

* TVSDK 1.4.43 est certifié pour iOS 11.

**Version 1.4.29**

* TVSDK 1.4.29 a été certifié pour iOS 10.

**Version 1.4.28**

* TVSDK 1.4.28 a été certifié pour iOS 10 bêta 7.
* Prise en charge de DRM pour forcer HTTPS en ajoutant les API forceHTTPS et isForcingHTTPS.
* Mise à jour des bibliothèques VHL vers la version 1.5.8, Adobe des bibliothèques mobiles vers la version 4.8.4 et de la bibliothèque d’utilitaire de journalisation vers la cible de déploiement de la version 7.0.

**Version 1.4.19**

Cette version de TVSDK a été certifiée avec le support FairPlay pour iOS et tvOS.

**Version 1.4.17**

* tvOS

  Cette version de TVSDK inclut la prise en charge de tvOS et a été certifiée pour les flux HLS non chiffrés.

  **Remarque**: Gardez à l’esprit les instructions de compilation suivantes :

   * La prise en charge de TVSDK tvOs est limitée aux diffusions cryptées DRM non Adobes. Vous devez supprimer la référence à drmNativeInterface.framework dans les paramètres de génération tvOS. Les diffusions cryptées AES sont toujours prises en charge.
   * Apple exige que toutes les applications Apple TV soient activées pour le code binaire. Vous devez donc activer cet indicateur dans les paramètres de votre projet.

## Problèmes résolus dans 1.4 {#resolved-issues-in}

<!-- 

Comment Type: draft

 <p>All TVSDK customers who use CRS are strongly encouraged to upgrade to TVSDK 1.4.39 or latest on iOS and Android. This upgrade is a drop-in replacement to the existing app implementation. After the upgrade, check for the CRS creative URL requests in a proxy tool (for example, Charles) to verify that the version in the path reflects version 3.1. For example:</p> 
 <p><span class="code">https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8</span></p> 
-->

<!-- 

Comment Type: draft

 <p>TVSDK versions earlier than version 1.4.28 sometimes exhibit a long delay in the startup time when ad-enabled content is played on devices that are running on iOS 10. To resolve this issue, upgrade to version 1.4.28 or later. Version 1.4.28 was released on August 31, 2016, and iOS 10 was released on September 13, 2016.</p> 

-->

**Version 1.4.45{#ios-tvsdk}**

* Ticket #36294 - iOS TVSDK non fonctionnel avec Xcode 10

   * Correction des problèmes de compilation avec TVSDK sur XCode 10. En raison des exigences de Xcode 10, les applications créées à partir de TVSDK pour iOS 1.4.45 nécessitent une cible de déploiement minimale comme iOS 7.0.

* Ticket #36321 - Incohérence observée entre l’instance PTMediaPlayer et l’instance AVPlayer en état &quot;Lecture&quot;.
* Ticket #36493 - `libstdc++` Prise en charge sur iOS 12

   * Correction des problèmes de compilation avec TVSDK sur iOS 12. Les applications créées à partir de TVSDK pour iOS 1.4.45 requièrent une cible de déploiement minimale comme iOS 7.0.

**Version 1.4.44**

* Ticket #34683 - Le Temps De Progression De La Lecture De La Publicité Est Négatif

   * Des vérifications supplémentaires sont effectuées pour gérer le cas lorsqu’il existe une incohérence entre la durée signalée par le serveur de publicités et le contenu réel de la publicité.

* Ticket #34801 - currentTime et localTime n’étaient pas mis à jour lors de la recherche d’une nouvelle position pendant l’état en pause.

   * L’heure actuelle du lecteur peut désormais être définie sur zéro si le lecteur est en pause ; auparavant, l’heure actuelle était définie sur zéro uniquement en état de lecture.

* Ticket #35037 : la lecture se bloque avec une URL incorrecte lors du retour d’une insertion de publicités basée sur un signal.

   * Correctif amélioré fourni pour le problème fermé #34385 dans la version 1.4.42. Ajout du code de gestion des exceptions et des vérifications annulées pour rendre la file d’attente des opérations plus robuste.

**Version 1.4.43**

* (ZD#32990) - iOS : lecture de contenu au lieu de publicités sur certains points de repère. L’API &#39;selectedMediaOptionInMediaSelectionGroup&#39; qui faisait partie de l’interface AVPlayerItem a désormais été déplacée sous AVMediaSelection dans iOS 11. Le problème a été résolu à l’aide de cette nouvelle API.
* (ZD#33683) TVSDK a supprimé == suffixe des chaînes de métadonnées. Le problème est résolu dans la logique d’analyse.
* (ZD#33905) - iOS TVSDK appelle les fichiers de manifeste avec deux agents utilisateurs. Le problème de l’agent utilisateur a été corrigé dans le premier appel m3u8 (nouveau cas d’installation). Les M3u8 ont maintenant les mêmes agents utilisateur pour tous les appels.
* (ZD#34293) - Les pré-roulements insérés sur les flux LINEAR ne s’exécutent pas correctement sur iOS11. Le problème est résolu pour les publicités preroll.
* (ZD#34684) - Lorsque la stratégie de saut de publicité est appliquée, les images de publicité preroll s’affichent pendant quelques secondes. Une nouvelle API, enableVodPreroll, a été introduite pour désactiver la lecture preroll dans la lecture vod. La valeur par défaut de cette API est &quot;Oui&quot;. L’API assure le saut du groupement de contenu publicitaire dans le contenu principal.
* (ZD#34765) - Après avoir appelé stop(), quelques segments de flux de transport sont toujours téléchargés. Amélioration de l’API Stop() pour éviter le téléchargement des segments supplémentaires.
* (ZD#34865) - Les publicités preroll pour la diffusion en direct sont tronquées sur iOS. En ce qui concerne iOS11 et l’ajout d’une vérification supplémentaire pour confirmer si le flux est pré-roll ou de contenu principal, résout ce problème.
* (ZD#35093) - Correction d’un scénario de basculement où, si la variante par Principal du flux échoue au démarrage (renvoie 404), la lecture ne passe pas au flux de sauvegarde.

**Version 1.4.42 (1.4.42.118)**

* (ZD#34385) - La lecture se bloque avec une URL incorrecte lors du retour d’une insertion de publicités basée sur un signal.

  Augmentez le nombre maximal de répétitions simultanées pour CustomAVAssetLoaderOperations, de sorte que les lectures du manifeste puissent continuer à s’exécuter.
* (ZD#34373) - Les utilisateurs finaux ne peuvent pas diffuser vers des appareils connectés au HDMI lorsque l’enregistrement de diffusion est interdit.
* (ZD#32678) - TVSDK ne collecte pas les ID de publicité corrects sur iOS.

  L’identifiant de publicité final de l’élément créatif publicitaire est désormais récupéré dans les pings VHL en cas de redirections VAST/VMAP.
* (ZD#33904) - TVSDK n’est pas enregistré pour les notifications AVAudioSessionMediaServicesWereLostNotification et AVAudioSessionMediaServicesWereResetNotification.

  PTMediaServicesWereLostNotification et PTMediaServicesWereResetNotification peuvent désormais être enregistrés sur l’application du lecteur afin d’obtenir les notifications lorsque les services multimédia sont réinitialisés ou perdus.

* (ZD#33815) - Les clients ne peuvent pas mettre à jour leurs règles CRS de normalisation et de hiérarchisation sans avoir à mettre à jour l’application.

  Ajout des API getCRSRulesJsonURL et setCRSRulesJsonURL aux API TVSDK iOS .

**Version 1.4.41 (1.4.41.76)**

* (ZD #34464) - Problèmes de création d’une application de référence avec TVSDK version 1.4.41

  À compter de cette version, Xcode 9 est requis pour compiler TVSDK pour iOS.
* (ZD #29456) - Le début de la lecture dans un état en pause

  Correction du problème de mise en pause qui se produisait lorsque la vidéo était en pause lors de la saisie d’un élément Airplay.
* (ZD #30371) - L’heure de début d’AdBreak change lorsque nous insérons plus de 2 publicités dans un flux linéaire.

  Correction de l’erreur lors de la tentative de lecture de contenu sur Apple TV, qui empêchait complètement la lecture.
* (ZD #32146) - Aucune erreur PTMediaPlayerStatusError n’est reçue pour le contenu HLS Live lors du blocage de la version de développement iOS 11

  Aucun PTMediaPlayerStatusError n’est reçu pour le contenu HLS Live et VOD sur le blocage à l’aide de Charles (Déposer la connexion et 403).
* (ZD #29242) - Échec de la lecture vidéo de la lecture avec les publicités activées

  Lorsque les publicités sont activées et qu’AirPlay est activé au démarrage de la lecture d’une vidéo, la lecture vidéo ne démarre jamais et aucune erreur n’est affichée.
* (ZD#33341) - DRMInterface.h déclenche des avertissements de génération dans Xcode 9

  Correction de deux prototypes de blocs dans DRMInterface.h qui manquaient le mot &quot;void&quot; dans leurs listes de paramètres.
* (ZD#31979) - Ne compile/n’exécute pas lorsqu’il s’agit d’iOS 10 ou d’une version ultérieure pour iPhone 7/iPhone7+.

  Correction de la compilation des documents IB pour les versions antérieures à iOS 7 qui n’est plus prise en charge
* (ZD#32920) : écran vierge au sein d’une coupure publicitaire et sans fin de la coupure publicitaire

  Lorsqu’une coupure publicitaire présente des instances de publicité et qu’une fois l’instance de publicité terminée, un écran vide s’affiche.
* (ZD#32509) - Désactivation de l’enregistrement d’écran iOS 11 Désactivation de l’enregistrement d’écran sur iOS 11

* (ZD#33179) - Échec d’événement intermittent sur iOS11

  Correction de l’échec de l’événement sur iOS 11

**Version 1.4.40** (1.4.40.72)

* (ZD #32465) - Le lecteur ne peut pas gérer les listes de lecture fusionnées.

  Appelez terminerLoadingWithError (avec : erreur) pour la fondation AV afin d’essayer d’autres diffusions/de déclencher le basculement.

* (ZD #31951) - Erreur TVSDK pendant les rotations de licence.

  Correction du problème de rotation des licences.
* (ZD #31951) : écran vierge au sein d’une coupure publicitaire, sans fin de la coupure publicitaire.

  Correction d’un problème en raison duquel les publicités Facebook VPAID renvoyaient souvent plusieurs blocs CDATA dans un seul noeud \&amp;lt;AdParameters\&amp;gt; VAST .
* (ZD #33336) - [iOS] TVSDK - Les capsules publicitaires ne sont pas remplies, bien que suffisamment de publicités aient été renvoyées par la roue libre.

  Création d’une relation parent-enfant entre la publicité de séquence et la publicité de secours, ainsi que d’un tri basé sur la séquence et l’index parents.

**Version 1.4.39** (1.4.39.43)

* (ZD #32178) - La version du TVSDK iOS est incorrecte.

  La sortie de la version TVSDK dans les fichiers journaux était 1.0.211. Elle est fixe pour générer la version correcte.

* (ZD #32199) - Chargement différé de la publicité - La vidéo ne s’affiche pas pour le contenu.

  La frise chronologique d’Adbreak local qui n’était pas initialisée auparavant est maintenant actualisée avant l’utilisation.

* (ZD #27528) : vidéo, audio ou les deux se figent 1 à 45 secondes après le début de la lecture d’une ressource, si le son secondaire n’est pas défini sur la valeur par défaut sur iOS 1.2.

  Préparez et informez les pistes audio à l’état Prêt .

* (ZD #30411) - Si vous choisissez une langue Sap secondaire, vous risquez d’obtenir des résultats inattendus, comme l’absence d’audio ou d’audio incorrect.

  Préparez et informez les pistes audio à l’état Prêt .

* (ZD #32199) - Chargement différé de la publicité - La vidéo ne s’affiche pas pour le contenu.

  La frise chronologique d’Adbreak local qui n’était pas initialisée auparavant est maintenant actualisée avant l’utilisation.

* (ZD #27528) : vidéo, audio ou les deux se figent 1 à 45 secondes après le début de la lecture d’une ressource, si le son secondaire n’est pas défini sur la valeur par défaut sur iOS 1.2.

  Préparez et informez les pistes audio à l’état Prêt .

* (ZD #30411) - Si vous choisissez une langue Sap secondaire, vous risquez d’obtenir des résultats inattendus, comme l’absence d’audio ou d’audio incorrect.

  Préparez et informez les pistes audio à l’état Prêt .

**Version 1.4.38** (1.4.38.860)

* (ZD #29281) - iOS : Ajout d’AdSystem et d’ID de création aux demandes CRS

Utilisation de l’ID de création et d’AdSystem dans la requête CRS en fonction des règles de normalisation CRS

* (ZD #29176) - Blocage sur PTAdPolicyDeligate satAdBreakAsWatched:position

Le blocage dû à un AdBreak vide est maintenant géré.

* (ZD #30125) - Les publicités programmatiques ne fonctionnent pas sur la plateforme iOS

Ajout de la prise en charge des annonces programmatiques dans iOS.

* (ZD #30782) - Notification #EXT-X-PROGRAM-DATE-TIME

L’événement de métadonnées minutée n’est pas déclenché pour la balise # EXT-X-PROGRAM-DATE-TIME avec les flux DRM LIVE.

**Version 1.4.37 (1.4.37.842)**

* (ZD #28950 ) - Problème de lecture VOD

Problème de lecture lorsque la balise # EXT-X-PLAYLIST-TYPE dans le flux est définie sur Événement plutôt que VOD

* (ZD #29281) - iOS : Ajout d’AdSystem et d’ID de création aux demandes CRS

Utilisation de Creative Id et d’AdSystem dans la requête CRS basée sur les règles de normalisation CRS.

* (ZD #29462) - Une publicité TremorHub dans A&amp;E VOD provoque un blocage des applications iOS

**Version 1.4.36 (1.4.36.835)**

* (ZD #29418) - Les erreurs de durée 0 (#EXT-X-CUE-OUT:0.000) provoquent l’arrêt ou le blocage de la lecture du TVSDK iOS.

Le problème est résolu et la lecture démarre correctement.

* (ZD #29462) - Publicité dans VOD provoquant un blocage sur iOS TVSDK .

Le problème est résolu. iOS TVSDK génère une exception (AUDNetworkAdInfo::initWithAdId) et ne la gère pas. L’exception est due à un ID de publicité vide.

* (ZD #29281) - Ajoutez AdSystem et Creative ID aux demandes CRS.

Incluez AdSystem et CreativeId comme nouveaux paramètres dans les requêtes 1401 et 1403 (tous les autres paramètres restent les mêmes).

**Version 1.4.35** (1.4.35.830)

* (ZD #27830) - Doit déterminer par programmation la différence entre les sous-titres et les sous-titres dans iOS.

TVSDK expose désormais les deux types qui peuvent être utilisés pour filtrer le type de légende requis.

* (ZD #29160) - Les signaux publicitaires EXT-X-CUE-OUT ne sont pas correctement répliqués sur TVSDK iOS.

Avec la publicité du milieu EXT-X-CUE-OUT en cours de lecture.

* (ZD #29100) - L’application se bloque lorsque l’utilisateur passe à la fin d’un film.

Correction de plusieurs blocages liés à la synchronisation.

* (ZD #28785), (ZD #27712) et (ZD #25076) - L’application iOS se bloque pendant les grands événements en direct.

Correction de plusieurs blocages liés à la synchronisation.

**Version 1.4.34** (1.4.34.815 pour iOS 6.0+)

* (ZD# 28481) - Pénurie liée à une clé incorrecte ajoutée à la fin d’une coupure publicitaire pour ces flux FER

Pour un flux FER, la clé avant la coupure publicitaire est insérée après la fin de la coupure publicitaire. Ce problème a été résolu en ajoutant la variable *Dernière clé vue* à la fin de la coupure publicitaire.

**Version 1.4.3** (1.4.33.803 pour iOS 6.0+)

* (ZD# 21701) Activation de CRS pour les sous-comptes

Activé en envoyant l’URL de création d’origine pour la demande 1401 CRS au lieu de l’URL normalisée, conformément aux exigences du serveur principal CRS.

* (ZD# 26218) - Problème de chargement PSDKResources.bundle

Ce problème a été résolu en mettant à jour le chargement des ressources pour qu’il recherche tous les lots disponibles.

* (ZD# 27460) Premier appel publicitaire mid-roll - POST à cdn.auditude<span></span>.com retournant 403.

Le nouveau compte CDN ne peut pas gérer une requête CDN de POST. Ce problème a été résolu en mettant à jour le code pour que la variable `cdn.auditude.com` demande d’annonce à GET au lieu de POST.

**Version 1.4.32** (1.4.32.792 pour iOS 6.0+)

* (ZD# 27132) Prise en charge des valeurs décimales pour les coupures publicitaires VMAP.

Lorsque le contenu n’était pas segmenté le long des coupures publicitaires définies, des entiers provoquaient des emplacements publicitaires inattendus. Le problème a été résolu en ne convertissant pas les valeurs décimales en nombres entiers.

* (ZD# 27189) Le contenu AES avec la balise EXT-X-DISCONTINUITY-SEQUENCE n’est pas lu correctement.

Le problème a été résolu en plaçant la balise au début de la liste de lecture.

**Version 1.4.31** (1.4.31.785 pour iOS 6.0+)

* (ZD# 24528) Mise en oeuvre de mesures d’utilisation du SDK pour la facturation

Pour plus d’informations, voir [Mesures de facturation](../programming/tvsdk-1.4-for-ios/c-psdk-ios-1.4-billing/c-psdk-ios-1.4-billing.md).

* (ZD# 24642) Prise en charge du mode &quot;Image dans l’Image&quot; pour TVSDK

La fonctionnalité d’image dans l’image, qui ne fonctionnait pas correctement dans certains cas, a été corrigée.

* (ZD# 25246) Signaux de coupure publicitaire incorrects

Ce problème a été résolu en alignant les balises de discontinuité entre les manifestes de variantes.

* (ZD# 26218) Le processus de création d’application devient complexe lorsque vous essayez d’inclure PSDKLibrary.framework dans la structure d’application du client.

Ce problème a été résolu en regroupant PSDKLibrary.framework comme demandé.

* (ZD# 26364) Prise en charge multi-CDN pour les publicités CRS
<!-- 
Comment Type: draft
For more information, see [Multiple CDN support for CRS Ad Delivery](http://help.adobe.com/en_US/primetime/psdk/ios/1.4/index.html#PSDKs-concept-Multiple_CDN_support_for_CRS_ad_delivery).
-->
* (ZD# 27028) Délai de lecture de certains flux dans iOS 10.

Ce problème a été résolu en fournissant une solution pour les diffusions qui n’ont pas d’extension M3U8.

**Version 1.4.30** (1.4.30.754 pour iOS 6.0+)

Les problèmes suivants ont été résolus pour TVSDK dans cette version :

* (ZD# 24180) Ajout d’un en-tête personnalisé à liste autorisée

Un nouvel en-tête personnalisé a été ajouté à la liste autorisée TVSDK.

* (ZD# 25016) Le flux de basculement est sélectionné de manière aléatoire lorsque les paramètres de contrôle ABR sont définis.

Ce problème a été résolu en conservant les flux ABR dans l’ordre lorsque les paramètres ABR sont fournis avec le paramètre initialBitrate sur un flux qui inclut des URL de basculement. Cela permet d’éviter de lire les flux de basculement plutôt que les flux principaux.

* (ZD# 25076) Blocage sur PTAuditudeAdResolver loadComplete

Correction du problème de blocage survenant lors du démarrage/de l’arrêt rapide de plusieurs instances PTMediaPlayer avec des publicités.

* (ZD# 25960) Aucune balise d’abonnement supplémentaire n’est nécessaire pour déclencher les diffusions de notification de changement de métadonnées

Correction du problème en raison duquel une balise abonnée n’était pas avertie lorsqu’elle apparaissait avant le premier segment dans le manifeste.

* (ZD# 26084) PSDK lance un 106000.101000.Erreur de décodage -11833 introuvable lors de la transition de la dernière coupure publicitaire vers le contenu de divertissement

Lorsque l’heure de début de la dernière coupure publicitaire du VMAP est antérieure à la fin de la durée totale, dans certaines conditions, la clé n’est pas insérée avant la fin de la dernière coupure publicitaire. Ce problème a été corrigé.

* La bibliothèque Video Heartbeat (VHL) a été mise à jour vers la version 1.5.9 afin de résoudre les problèmes suivants :

   * (ZD #22351) VHL - Analytics : durée de la ressource vidéo en direct

Ce problème a été résolu en ajoutant l’API assetDuration à `PTVideoAnalyticsTrackingMetadata` pour mettre à jour la durée des ressources pour les flux en direct/linéaire et fournir une logique de vérification du flux en direct.

* (ZD# 22675) VHL - Analytics : mise à jour de la durée des ressources vidéo en direct

Ce problème est le même que ZD #22351.

* (ZD #25908) VHL - Analytics : Adobe Heartbeat Event Crash

Ce problème a été résolu en mettant à jour la mise en oeuvre afin d’utiliser la dernière version de VHL pour iOS version 1.5.9 afin d’améliorer la stabilité et les performances.

* (ZD #25956) VHL - Analytics : blocage lors de la lecture répétée de vidéos

Ce problème est le même que ZD #25908.

**Version 1.4.29** (1.4.29.743)

* (ZD# 23901) Les publicités tierces ne sont pas lues

Ce problème a été résolu en passant à la structure d’URL CRS v3 pour inclure l’ID de zone dans l’URL reconditionnée.

* (ZD #25183) Problèmes de lecture DRM sur tvOS et iOS

Ce problème a été résolu en fournissant la prise en charge de plusieurs balises clés nécessaires à la prise en charge de la gestion multiDRM.

* (ZD# 25334) TVSDK ne parvient pas à lire un contenu partagé cDVR

Ce problème a été résolu en empêchant TVSDK de convertir des chaînes vides en URL absolues.

* (ZD# 25347) Définition de l’en-tête HTTP personnalisé sur AVURLAset

La prise en charge des en-têtes personnalisés sur ses requêtes de segment par le biais de la classe PTNetworkConfiguration a été ajoutée.

**Version 1.4.28** (1.4.28.722)

* (ZD #24549) Plusieurs appels de suivi des publicités

Ce problème a été résolu en mettant à jour le gestionnaire de chronologie afin d’écouter les notifications sur un objet spécifique lorsque plusieurs lecteurs sont créés.

* (ZD #24758) PTManifestLogger ne prend pas en charge iOS 8

Ce problème a été résolu en mettant à jour la bibliothèque de l’utilitaire de journalisation vers la cible de déploiement de la version 7.0.

* (ZD #24775) Diffusion différée en raison de publicités

Ce problème a été résolu en calculant correctement la dérive de durée sur les listes de lecture d’événements.

* (ZD #24799) Certains épisodes ne sont pas lus sur l’application iOS

Ce problème a été résolu en utilisant le serveur web local pour les sous-titres lorsque les fichiers WebVTT sont géolimités.

**Version 1.4.27** (1.4.27.711) pour iOS 6.0+

* (ZD #24089) - Optimisations de la résolution des publicités sur les diffusions DVR longues

Ce problème a été résolu en ajoutant plusieurs optimisations afin de réduire le temps nécessaire au traitement de la fenêtre de l’enregistrement numérique dans les flux linéaire/en direct.

* (ZD #21554) - Balises d’erreur TVSDK non déclenchées pour application-type = video/mp4

Ce problème a été résolu en permettant au lecteur d’envoyer un ping aux URL de suivi des erreurs correctes sur les formats de ressources non valides.

* (ZD #24424) - Un plantage de type EXC_BAD_ACCESS KERN_INVALID_ADDRESS provient de PSDKLib pour iOS sur les appareils plus récents.

Le blocage qui s’est produit en raison d’une instance de lecteur multimédia désaffectée, lorsque la lecture est basculée rapidement entre les différentes diffusions, a été corrigé.

* (ZD #24575) - Blocage dans TVSDK sur les appareils 32 bits lorsque enableDebugLog=true

Correction du problème dans le format de journal qui provoquait le blocage sur les appareils 32 bits lorsque la journalisation était activée.

**Version 1.4.26** (1.4.26.702) pour iOS 6.0+

* (ZD# 20213) - TVSDK FW doit être dynamique/modulaire pour XCode7

   * Corrigé en mettant à jour les bibliothèques avec la prise en charge des modules

**Version 1.4.25** (1.4.25.684) pour iOS 6.0+

* (ZD #19629) - Une vidéo en direct se met en pause lors de la saisie d’un élément Airplay sur ATV 4

Ce problème a été résolu en ajoutant une période d’attente après la suppression des anciens éléments, mais avant l’ajout de nouveaux éléments à AVQueuePlayer. En l’absence de délai d’attente, les notifications sont envoyées à un élément incorrect.

* (ZD #19856) - Aucun sous-titre ne s’affiche lorsqu’il est activé par défaut.

Les problèmes de la liste de lecture webvtt, qui empêchait l’affichage correct des sous-titres, ont été corrigés.

* (ZD #21590) - Performances vidéo et suivi dans les dernières versions d’origine

Le problème concernant la longueur de la vidéo manquante dans VideoAnalytics a été corrigé.

* (ZD #20202) - La définition du style de sous-titres personnalisés bloque l’application iOS.

Ce problème a été résolu en ajoutant d’autres vérifications d’objets nuls lors de la définition des styles de sous-titre.

* (ZD #20709) : durée de la vidéo indiquée comme 0 dans le suivi de démarrage de la vidéo

Ce problème est le même que (ZD #21590).

* (ZD #22280) - Longueur de la vidéo Analytics définie sur 0

Ce problème est le même que (ZD #21590).

* (ZD #22592) - Problèmes liés à Airplay dans Primetime

Ce problème est le même que (ZD #19629).

* (ZD#22922) - Changement de débit manuel pour iOS

Ce problème a été résolu en fournissant une option permettant de spécifier le débit maximal.

* (ZD #23084) - Conformité Apple aux réseaux uniquement IPv6

Les symboles qui n’étaient pas recommandés par Apple pour la compatibilité IPv6 ont été supprimés.

**Version 1.4.24** (1.4.24.661) pour iOS 6.0+

* ZD #2548) - Prise en charge de Primetime pour la publicité interactive sur mobile - VPAID 2.0

Ce problème a été résolu en mettant à jour la logique pour afficher le lecteur si une publicité VPAID ne parvient pas à être lue.

* (ZD #20101) - L’implémentation de chapitre personnalisée déclenche l’événement de début de chapitre pendant la lecture de la publicité.

Ce problème a été résolu en mettant à jour VideoAnalyticsTracker pour détecter correctement le début/la fin du chapitre lors de la transition entre les limites de chapitre et non-chapitre.

* (ZD #20784) - Analytics : Déclenchement du contenu terminé pour les transitions vidéo en direct

Ce problème a été résolu en ajoutant une logique pour déclencher manuellement la fin du contenu au cours d’une session de suivi vidéo.

Les bibliothèques suivantes ont été mises à jour :

* Bibliothèque AdobeMobile vers 4.10.0
* Bibliothèque VHL vers 1.5.6
* Bibliothèque VHL-Nielsen vers 1.6.7
* (ZD #21855) - Les sous-titres ne sont pas lus après le mid-roll

Dans ce problème, les balises de discontinuité en double n’affichaient pas les sous-titres après le parcours intermédiaire. Ce problème a été résolu en supprimant les balises de discontinuité les unes à côté des autres.

* (ZD #21994) - Chaîne hors limites dans PTHLSUtils

La cause la plus probable du blocage est lorsqu’une clé EXT-X-KEY comporte une URL entourée de guillemets.

* ZD #22074) - Un plantage AUDVAST se produit une fois par minute sur iOS

Dans la version 1.4.23, le blocage dû à la présence de caractères non sûrs dans une URL de redirection VAST a été corrigé. Toutefois, TVSDK continuait à ignorer ces publicités.

Ce problème a été résolu en gérant les caractères non sûrs et en autorisant la lecture des publicités.

* (ZD #22694) - PTMediaPlayer.  La vue est masquée par le lecteur

Ce problème a été résolu en mettant à jour la logique pour afficher le lecteur si une publicité VPAID ne parvient pas à être lue.

**Version 1.4.23** (1.4.23.641) pour iOS 6.0+

* (ZD #18016) - Aucune réponse du SDK Primetime avec une mauvaise condition réseau

Ce problème a été résolu en améliorant la notification d’erreur lorsqu’une erreur fatale d’AVFoundation se produit et afin de permettre à l’application de gérer le redémarrage après l’erreur.

* (ZD #20580) - Blocage dans PTSplicerManager

Ce problème a été résolu en fournissant une protection supplémentaire contre les problèmes de simultanéité qui provoquent le blocage.

* (ZD #21782) - Code d’erreur iOS 10100

Le problème en raison duquel TVSDK renvoyait une erreur 101000 lors du démarrage de la lecture sur les flux DRM d’accès Adobe a été corrigé.

* (ZD #21889) - Échec de la lecture des publicités en ligne et du contenu hors ligne

Le problème d’échec de la lecture après correction d’une publicité sur du contenu hors ligne chiffré AES.

* (ZD #22074) - Un plantage AUDVAST se produit une fois par minute sur iOS

Ce problème a été résolu en améliorant la gestion des balises publicitaires VAST tierces qui contiennent des caractères non valides dans l’URL.

* (ZD #22257) - TVSDK ne parvient pas à lire le flux DRM

Le problème en raison duquel le TVSDK renvoyait une erreur 101000 lors du démarrage de la lecture sur les flux DRM d’accès Adobe a été corrigé.

**Version 1.4.22** (1.4.22.627) pour iOS 6.0+

* (ZD #18709) - Blocage dans TVSDK pour iOS

Le problème d’un blocage survenant sur certains flux protégés DRM d’accès aux Adobes a été corrigé.

* (ZD #18850) - Mettre à jour la logique de sélection créative en fonction des règles CRS

Ce problème a été résolu en ajoutant un fichier de configuration .json pour spécifier la priorité de sélection créative.

* (ZD #19770) - Le flux vidéo AES protégé ne s’exécute plus

Le problème où certains flux redirigés 302 ne fonctionnaient pas a été corrigé.

* (ZD #19629) - Une vidéo en direct se met en pause lors de la saisie d’un élément Airplay sur ATV 4

Ce problème a été résolu en ajoutant une solution pour la mise en pause de la vidéo en direct lorsque la lecture est activée pour les appareils Apple TV 4. Le problème semble être un problème d’Apple TV 4.

* (ZD #21119) - Le TVSDK est bloqué après la lecture de la publicité.

Ajout de la prise en charge des flux chiffrés AES avec une séquence IV lors de l’utilisation de l’insertion de publicités.

* (ZD #21125) - Revenez de la coupure publicitaire linéaire/en direct tôt

Ajout de la prise en charge du retour d’une coupure publicitaire tôt avant la fin de la coupure publicitaire. Un retour anticipé est indiqué par le biais d’une balise de manifeste personnalisée.

* (ZD #21224) - Prise en charge de la lecture pour les diffusions à jetons depuis Akamai

Des API ont été ajoutées à la classe PTNetworkConfiguration pour ajouter des cookies en tant que paramètres d’URL sur les segments pour certains flux segmentés en jetons Akamai.

* (ZD #21287) - Journal externe

Correction d’un problème lié à certaines instructions de journal affichées par défaut dans la console xcode même lorsque la journalisation est désactivée.

* (ZD #21446) - Les événements de coupure publicitaire ne sont parfois pas déclenchés par TVSDK

Dans les flux EVENT, les coupures publicitaires ne sont pas déclenchées correctement dans la version précédente. Ce build résout ce problème.

**1.4.21** (1.4.21.605) pour iOS 6.0+

* (ZD #20749) - Les secours ignorent les réponses VAST non vides ; les URL de suivi des publicités supplémentaires se déclenchent.

Un problème lié aux pings en double sur les annonces de secours a été résolu.

**1.4.20** (1.4.20.590) pour iOS 6.0+

* (ZD #18639) - Le TVSDK utilise un processeur/des ressources excessifs sur une longue ressource d’enregistrement à chaud.

L’utilisation excessive du processeur/des ressources a été corrigée dans les deux niveaux. Tout d’abord en laissant la fonction de mise à jour de l’heure s’exécuter sur une file d’attente globale, au lieu du thread principal, et en optimisant l’utilisation du processeur pour analyser le manifeste avec le m3u8 traité et mis en cache précédemment.

* (ZD #19349) - Les publicités preroll sont ignorées lors du ralentissement de la connexion réseau.

Ce problème a été résolu en fournissant un événement de délai d’expiration (requestTimeout) à l’application et à adMetadata .  API adRequestTimeout pour remplacer le délai d’expiration par défaut de 10 secondes.

* (ZD #19446) - Notification manquante sur les flux en direct

Ce problème a été résolu en permettant à l’application de s’abonner à EXT-X-PROGRAM-DATE-TIME sur les flux en direct.

* (ZD #19459) - Blocage lors de la préparation audio de remplacement avec PTMediaPlayerItem prepareAudioOptionsWithAVMediaSelectionOptions
* (ZD #19460) - Blocage - [PTMediaPlayerItem prepareSousOptionsWithAVMediaSelectionOptions:nonForcedOptions:]

Ce problème est le même que Zendesk #19459.

* (ZD #19574) - Le TVSDK ne renvoie pas de données de réponse M3U8 pour le contenu DRM ou non DRM.

Lors du chargement initial du fichier manifeste dans PTMediaPlayerItem.prepareToPlay, si le chargement du manifeste a échoué, le TVSDK ne signale pas le corps de la réponse d’échec à l’application.

Ce problème a été résolu en permettant à TVSDK de signaler la réponse à l’échec comme une erreur à l’application.

* (ZD #19615) - La logique de secours ne fonctionne pas

Dans l’implémentation actuelle, les publicités de secours ont été ignorées et n’ont pas été reconditionnées, sauf si elles sont au format m3u8. Ce problème a été résolu en ajoutant également la prise en charge du reconditionnement des annonces de secours.

* (ZD #19770) - TVSDK ne parvient pas à lire le contenu AES protégé avec une redirection 302.

Le problème de redirection a été corrigé, car l’URL de redirection était effacée par cleanConnectionData avant de pouvoir être utilisée pour analyser le manifeste.

* (ZD #19856) - Les sous-titres ne s’affichent pas pour certains débits lorsqu’ils sont activés par défaut.

Ce problème a été résolu en gérant l’erreur provenant d’iOS pour les segments des diffusions dans lesquels les sous-titres ne s’affichent pas.

* (ZD #19868) - Le TVSDK se bloque lorsqu’un créatif non valide est victime de trafic.

Le blocage dans TVSDK qui désaffectait incorrectement une instance de l’analyseur de grande taille a été corrigé.

* (ZD #20180) - Les publicités VPAID sont parfois ignorées.

Le type MIME JavaScript n’était pas toujours inclus ou considéré comme un type MIME valide. Ce problème a été résolu en incluant JavaScript comme type MIME valide.

* (ZD #20749) - Les secours ignorent les réponses VAST non vides ; les URL de suivi des publicités supplémentaires se déclenchent.

Le problème où certains créatifs ne sont pas reconditionnés a été corrigé.

**Version 1.4.19** (1.4.19.563) pour iOS 6.0+

* ZD #18639) - Le TVSDK utilise un processeur/des ressources excessifs sur une longue ressource d’enregistrement à chaud.

Ce problème a été résolu en optimisant la réécriture de la liste de lecture DRM m3u8 pour mettre en cache les bits de la liste de lecture qui ont été précédemment réécrits. Cela est particulièrement pertinent lorsque vous lisez des flux m3u8 en direct pour lesquels le m3u8 est téléchargé après chaque téléchargement de segment.

* (ZD#18956) - player.drmManager est nul lorsque le point d’arrêt est défini dans le lecteur de démonstration iOS

Ce problème a été résolu en mettant à jour l’implémentation de l’API PTMediaPlayer.drmManager afin de sélectionner DRM Manager dans la structure DRM.

**Version 1.4.18** ( 1.4.18.557) pour iOS 6.0+

* (ZD #18844) Suivi du curseur de lecture pour le contenu en direct dans le lecteur iOS.

Ce problème a été résolu en permettant aux applications de définir leur propre valeur de curseur de lecture.

* Zendesk #18518 - Si le nom de la vidéo n’est pas spécifié, le nom de la TVSDK est défini par défaut sur *Lecteur basé sur le PSDK.*

Ce problème a été résolu en supprimant la valeur par défaut du nom du lecteur.

**Version 1.4.17** (1.4.17.545) pour iOS 6.0+

* Zendesk #2228 - Amélioration de TVSDK pour renvoyer la réponse JSON de la récupération d’un manifeste

Au lieu d’envoyer une erreur lorsque le contenu n’est pas M3U8, la structure DRM renvoie une valeur nil DRMMetadata. Le problème a été résolu en ajoutant des métadonnées pour exposer le contenu lorsque la notification M3U8_PARSER_ERROR se produit.

* Zendesk #2231 - Erreur retournée lors de la récupération du manifeste non disponible dans MediaPlayerNotification

Même résolution que Zendesk #2228

* Zendesk #3304 - VAST 3.0 `[ERRORCODE]` macro non renseignée

Le problème en raison duquel le SDK Auditude n’envoie pas de ping lorsque l’URL de suivi comporte des espaces au début a été résolu.

* Zendesk #17294 - Crash SecKeyRawSign

Un blocage possible lorsque le code du client utilise la chaîne de clé a été résolu.

* Zendesk #18008 - Prise en charge des cookies pour iOS 8+ pour la prise en charge des flux segmentés en unités lexicales

Les flux segmentés en jetons Akamai exigent que les cookies soient envoyés sur les demandes de segments, ce qui n’était pas possible sur iOS 7 et versions antérieures. Depuis iOS 8, Apple a ajouté une API qui permet la transmission de cookies pour les demandes de segments. Cette prise en charge est désormais disponible dans TVSDK . Une prise en charge a également été ajoutée pour l’envoi d’un agent-utilisateur, le cas échéant.

* Zendesk #18166 - TVSDK 1.4.15 donne des centaines d’avertissements lors de la compilation avec DWARF avec les options de fichier dSYM

Tous les avertissements ont été résolus.

**Remarque**: des bibliothèques compatibles avec tvOS ont été ajoutées pour TVSDK .

**Version 1.4.16** (1.4.16.1454)

* Zendesk #3875 - Blocages S de l’onglet pendant la lecture

Rétablissement de la dépendance d’OKHTTP à l’auditude pour CRS car TVSDK utilise désormais directement le httpurlconnection au lieu de curl. Le problème a été résolu en effaçant les exceptions avant d’effectuer un autre appel JNI.

* Zendesk #4487 - Tracking du canal linéaire de contenu

Le problème a été résolu en réinitialisant le suivi de pulsation vidéo au cours d’une session de lecture de flux linéaire.

* Zendesk #17919 - Android - la recherche de contenu provoque une erreur de pulsation

Le problème était de résoudre la pulsation dans un état d’erreur lorsqu’il y a une recherche dans un chapitre.

* Zendesk #18053 - Application utilisant le TVSDK se bloque sur Marshmallow

TVSDK se bloquait sur Android M OS lorsque la bibliothèque TVSDK utilisait du code neon qui convertissait les couleurs YUV -> RGB. Ce problème a été résolu en mettant à jour les fonctions à l’origine de ce problème à l’aide d’une version non néon du code .

* Zendesk #18072 - Android M - Blocage d’application

Ce blocage se produit lors de l’appel des API MediaCodecList et MediaCodecInfo lors de la vérification de la prise en charge du profil et du niveau. Adobe recherche la prise en charge de Google pour obtenir des informations supplémentaires. Ce problème a été résolu en fournissant une solution temporaire en chargeant toutes les informations de codec à l’avance afin d’éviter d’appeler ces API uniquement lorsque des informations de codec sont nécessaires.

* Zendesk #18074 - Les sous-titres arabes ne fonctionnent pas avec Nexus avec Android 6.0

Ce problème a été résolu en fournissant la prise en charge de la carte des polices Android CTS.

**Version 1.4.15** (1.4.15.512) pour iOS 6.0+

**Remarque**: le module Nielsen a été supprimé de la version TVSDK, mais le SDK sera mis à jour prochainement avec un nouveau module d’intégration Nielsen.

* (ZD #2228) - Erreur retournée lors de la récupération du manifeste non disponible dans MediaPlayerNotification

Ajout de métadonnées pour exposer le contenu lorsque la notification M3U8_PARSER_ERROR se produit.

* (ZD #4437) - Blocages dans le SDK Adobe Primetime

Correction d’un blocage signalé lors de la préparation de sous-titres/d’audio alternatif.

* (ZD #4487) - Suivi du canal linéaire de contenu

Réinitialisation autorisée de l’outil de suivi de pulsation vidéo au cours d’une session de lecture de flux linéaire.

**Version 1.4.14** (1.4.14.498) pour iOS 6.0+

* (ZD #17260) - Blocage sur playlistManagerForURL

Correction d’un blocage intermittent en raison de problèmes de simultanéité.

**Version 1.4.13** (iOS 6.0+)

* (ZD #3304) - VAST 3.0 `[ERRORCODE]` macro non renseignée

   * Le code d’erreur 400 sera révélé si la publicité intégrée comporte un contenu créatif incorrect.
   * `[ERRORCODE]` La macro sera codée en URL.

* (ZD #3865) Intégration de Heartbeat avec les annonces IMA

Correction d’un bogue en raison duquel la durée de la vidéo était incorrectement signalée.

* Mise à jour du lecteur de démonstration TVSDK pour prendre en charge iOS 9

Pour prendre correctement en charge iOS 9, vous devez configurer les exceptions de la sécurité du transport des applications. Pour les besoins de la démonstration, l’ATS est complètement désactivé.

**Version 1.4.12** (1.4.12.464) pour iOS 6.0+

* (ZD #4521) CRS Test côté client et SSAI

Correction d’un MD5 inversé dans l’URL 3P.

**Version 1.4.12** (1.4.12.463) pour iOS 6.0+

* (ZD #2751) CSAI et CRS | Améliorer : gérez les éléments dynamiques dans certaines URL de fichier multimédia.

Mise à jour de Creative Repackaging Service pour gérer correctement les annonces avec des URL de création dynamiques.

* (ZD #3654) Fuite de mémoire dans la version PSDK après 1.3.4.166

Correction d’une fuite de mémoire dans drmFramework avec lecture régulière sur les appareils iOS 8.2.

* (ZD #3988) La fonction Preroll est ignorée lors de la recherche de nouveau dedans après la première lecture.

Correction d’un bogue afin que les stratégies publicitaires puissent être correctement désactivées.

* (ZD #4017) Demande de l’API iOS pour forcer la lecture de la publicité lors de la recherche vers l’arrière

Résolu avec un correctif pour ZD #4279

* (ZD #4279) Problème d’insertion de publicité HLS TVSDK -302 de redirection sur iOS et Desktop

Correction d’un bogue lorsqu’une ressource publicitaire utilisait une URL de redirection relative.

**Version 1.4.9** (1.4.9.427) pour iOS 6.0+

* (ZD #3075) Problème de disponibilité Internet - iOS

Ajout d’une notification pour détecter le blocage de la lecture.

* (ZD #3193) Demande d’une API de changement de profil dans TVSDK

Mise à jour de PTPlaybackInformation afin d’exposer la valeur mise à jour de l’indicateurBitrate. Mise à jour de la notification BITRATE_CHANGE pour qu’elle soit plus fiable et plus précise en termes de temps par rapport aux débits signalés par le M3U8.

* (ZD #3324) Problème de reporting des publicités Primetime lorsqu’aucun média publicitaire n’est dans VMAP

Prise en charge des URL de suivi de coupure publicitaire vide pour les pings, TVSDK vérifie désormais les pings de début et de fin de coupure publicitaire pour les coupures publicitaires vides.

**Version 1.4.8** (1.4.8.402)

* (ZD #3158) Blocages d’IOS 7 lors des relectures d’événements complets

**Version 1.4.7** (1.4.7.382)

* (ZD #2197) Suivi des erreurs de publicité. Ajout d’une notification pour le chargement du manifeste de la ressource.
* (ZD #2894) Player Effectue 4 demandes de manifeste de niveau supérieur pendant la lecture.
* (ZD #2992) Auditude Signalant des durées et identifiants bizarres.

**Version 1.4.6**(1.4.6.325)

* (ZD #2197) Suivi des erreurs de publicité. Ajout d’une notification pour l’échec du chargement du manifeste

**Version 1.4.5** (1.4.5.283)

* (ZD #2141) Mise en oeuvre d’Analytics pour l’application TreeHouse, ajout de la bibliothèque AdobeAnalyticsPlugin.a pour créer un module .
* Mise à jour de la bibliothèque Video Heartbeats vers la version 1.4.1.2
* (PTPALY-4226) (lié à ZD #2423) L’exécution de la réinitialisation DRM peut entraîner la suppression des données du document d’application.

**Version 1.4.4** 1.4.4.242

* Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.4.1.

* (ZD #2435) Documentation du SDK TV sur les mises à jour des besoins d’analyse

**Version 1.4.2** (1.4.2.210 : iOS 6.0+)

* (ZD #1129) _player.currentItem.audioOptions, renvoi vide
* (ZD #2109) Primetime PSDK 1.4.1.125 ne fonctionne pas avec Xcode 5.1.1
* (ZD #2137) Blocage dans PSDK sur iOS lorsque les métadonnées DRM ne peuvent pas être chargées

**Version 1.4.1** (1.4.1.125)

* (ZD #1107) CocoaLumberjack symboles de duplication
* (ZD #1644) Modification de l’agent utilisateur iOS pour le ciblage et la création de rapports
* (ZD #1850) Fichiers Cocoa Lumberjack inclus dans le SDK iOS
* (ZD#1908) Les balises personnalisées sont ignorées par le PSDK s’il en existe plus de 1

**Version 1.4.0** (1.4.0.32)

* Zendesk #1024 - Fonctionnalité de suppression de la publicité du flux via le manifeste

## Problèmes connus dans la version 1.4 {#known-issues-in}

* Dans iOS TVSDK , toutes les publicités sont regroupées dans le manifeste de contenu. Les comportements publicitaires sont implémentés en effectuant des recherches en fonction de la durée du contenu et des segments de publicité. Ainsi, si les durées de segment ne sont pas exactes, la recherche peut ne pas toujours se terminer à l’image exacte du début ou de la fin de la coupure publicitaire. Même si les durées correspondent au cadre, la plate-forme elle-même impose une certaine tolérance à la recherche et quelques images ou publicités ou contenus peuvent être affichés. Il s’agit d’une limitation de la plateforme et du fonctionnement de l’insertion de publicités avec TVSDK sur iOS.
* Dans ce cas, la décision d’ignorer se produit sur l’événement de recherche. Cependant, comme les durées du segment publicitaire dans le manifeste ne représentent pas exactement la durée réelle de la publicité, la recherche n’est pas précise. Par conséquent, vous voyez quelques images de la publicité lorsque les stratégies de publicité sont appliquées.
* RECORDING_ERROR : une erreur s’est produite lors de l’enregistrement de l’écran.
* Il se peut que la vidéo de rotation de licence ne soit pas lue sur iOS 11 et qu’elle soit correctement lue sur iOS 9.x et iOS 10.x.
* Dans la prise en charge de VPAID 2.0, si la lecture est active sur AirPlay, les publicités VPAID sont ignorées.
* La structure drmNativeInterface.framework ne se connecte pas correctement lorsque la cible minimale est définie sur iOS7 (ou version ultérieure).\
  Solution : indiquez explicitement la variable `libstdc++6`.  Bibliothèque dylib comme suit : accédez à Target->Créer des phases->Lier le fichier binaire avec les bibliothèques et ajoutez `libstdc++.6.dylib`.

* La publicité post-roll n’est pas insérée pour remplacer l’API.
* La recherche dans une coupure publicitaire (sans en sortir) génère une notification de coupure publicitaire en double.
* La définition de currentTimeUpdateInterval n’a aucun effet.\
  Remarque : dans certaines versions d’iOS, le système d’exploitation ne charge pas automatiquement les ressources dans PSDKLibrary.framework. Il est important de copier manuellement le fichier PSDKResources.bundle dans les ressources du lot de l’application : accédez à &quot;Créer les phases&quot; et copiez les ressources du lot.
* L’application de référence ne peut pas être créée à l’aide de Xcode 8 ou de versions antérieures. iOS TVSDK version 1.4.41 et ultérieure, compilez Xcode 9.

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://helpx.adobe.com/support/primetime.html) page.
