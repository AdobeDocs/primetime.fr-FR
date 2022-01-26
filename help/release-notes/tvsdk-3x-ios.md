---
title: Notes de mise à jour de TVSDK 3.13 pour iOS
description: Les notes de mise à jour de TVSDK 3.13 pour iOS décrivent les nouveautés ou les modifications, les problèmes résolus et connus et les problèmes d’appareil dans TVSDK iOS 3.13.
exl-id: adf8ab23-86d6-4113-b243-2709d5f7f829
source-git-commit: 92defeee19a430c8b0b66696c527a6abe377f4b9
workflow-type: tm+mt
source-wordcount: '7587'
ht-degree: 0%

---

# Notes de mise à jour de TVSDK 3.13 pour iOS {#tvsdk-for-ios-release-notes}

Les notes de mise à jour de TVSDK 3.12 pour iOS décrivent les nouveautés ou les modifications, les problèmes résolus et connus et les problèmes d’appareil dans TVSDK iOS 3.12.

## Configuration requise et logiciels {#system-software-requirements}

Avant de télécharger iOS 3.12, assurez-vous que les versions de votre matériel, de votre système d’exploitation et de vos applications répondent aux exigences suivantes :

Système d’exploitation : iOS 8.0 ou version ultérieure.

## iOS TVSDK 3.13

Cette version introduit la prise en charge des publicités &quot;HLS/CMAF&quot; (préroll, midroll et postroll) DEMUXED pour les diffusions LIVE, VOD et FER.

Pour des correctifs des problèmes signalés par les clients, voir [Problèmes résolus](#resolved-issues). Pour connaître les limites, voir [problèmes connus et limites](#known-issues-and-limitations).

### Nouvelles fonctionnalités et correctifs des versions précédentes {#whats-new-previous}

**iOS TVSDK 3.12**

Correction d’un problème en raison duquel la diffusion en direct échouait après 15 minutes de lecture.

**iOS TVSDK 3.11**

Correctifs fournis pour les problèmes client où `isFallbackOnInvalidCreativeEnabled` et méthode `customParams` provoque le blocage de l’application.

**iOS TVSDK 3.10**

* Correction d’un problème en raison duquel le lecteur TVSDK ne se déclenchait pas. `PTMediaPlayerStatusError` lorsque le réseau est indisponible.

**iOS TVSDK 3.9**

* Correction d’un problème en raison duquel la lecture des sous-titres VTT échouait, provoquant le gel de l’application.

* iOS TVSDK 3.9 incluait le certificat de transport d’individualisation mis à jour.

**Correctif iOS TVSDK 3.8.0.83**

Le hotfix avait le certificat de transport d&#39;individualisation mis à jour.

**iOS TVSDK 3.8**

Conformité iOS 13 et gestion d’iOS 13 `UIWebView` obsolescence des API.

**iOS TVSDK 3.7**

Correctif pour un scénario où la lecture s’arrêtait lorsque de nombreuses demandes de résolution de publicité étaient effectuées simultanément.

**iOS TVSDK 3.6**

**Correctifs dans la propriété vasteXML de la classe`PTNetworkAdInfo`**

Le `vastXML` n’était pas correctement définie et renvoyait une valeur nil.

**iOS TVSDK 3.5**

**Activation de l’audio en arrière-plan**

*Configurez votre application pour continuer la lecture audio lorsqu’elle passe en arrière-plan.*

Pour activer cette fonction, nous devons définir la nouvelle API `audioPlaybackInBackground` ajouté dans la variable `PTMediaPlayer` classe . Lorsque cette API est activée, votre application est prête à lire le son en arrière-plan.

**iOS TVSDK 3.4.0.19 (correctif)**

Cette version comporte un correctif pour les blocages d’application qui se produisent dans un scénario de basculement publicitaire.

**iOS TVSDK 3.4**

**Délai d’expiration de la résolution de publicité**

* Avec TVSDK 3.4, les utilisateurs peuvent désormais définir la valeur de délai d’expiration pour la résolution de publicité globale et les téléchargements de manifeste. Si, dans un délai donné, certaines publicités ne sont pas résolues, TVSDK lit les publicités restantes.

* `PTAdMetadata: adRequestTimeout` L’API a été abandonnée et sera supprimée. La valeur par défaut a été définie sur 35 secondes.

* Deux nouvelles API alternatives ont été introduites dans la `PTAdMetadataClass: adResolutionTimeout`  - timeout pour les appels de résolution de publicité globale adManifestTimeout - timeout pour les téléchargements de manifeste de publicité.

**Optimisation des recettes**

Activation de TVSDK pour identifier les zones problématiques liées aux workflows d’insertion de publicités afin de créer des rapports vers un point de terminaison d’analyse de votre choix.

**Version 3.3**

TVSDK 3.3 est désormais conforme au SDK iOS 11. Toutes les API obsolètes ont été remplacées par des alternatives appropriées.

**Version 3.2**

**Prise en charge de la journalisation supplémentaire (phase 2)**

Ajout de la prise en charge des notifications d’erreur, en cas de :

* La version HLS de l’annonce utilise un niveau supérieur au contenu.

* La variante Audio seule est exclue.

* La requête VAST/VMAP a échoué.

**Version 3.1**

* **Prise en charge de la journalisation supplémentaire**
Ajout de la prise en charge des notifications descriptives en cas d’échec de lecture de publicité.

* **Ajout [!DNL Fairplay] Prise en charge de flux CMAF chiffré**
   [!DNL Fairplay] Les flux CMAF chiffrés avec lecture du codec AVC sont désormais pris en charge.

**Version 3.0.1**

Aucune nouvelle fonctionnalité ni amélioration dans cette version.

**Version 3.0**

* TVSDK 3.0 prend en charge les flux HEVC.

* Juste à temps : résolution des publicités plus proches des marqueurs publicitaires.

Ajout `enableDelayAdLoading` de type booléen sur l’interface au niveau de l’application pour activer JIT. If `enableDelayAdLoading` est NON, il le fera `setadMetadata.delayAdLoading`sur True (propriété de l’interface PTAdMetadata).

Lorsque cette propriété est activée, TVSDK résout chaque coupure publicitaire avant sa position en fonction de la valeur de tolérance définie. Par défaut, `delayAdTolerance` est définie sur cinq secondes.

**Version 1.4.45**

Pour se conformer à Xcode10, TVSDK est passé de `libstdc++` to `libc++`, et par conséquent, la version minimale prise en charge est iOS 7. Auparavant, il s’agissait d’iOS 6.

**Version 1.4.44**

Aucune nouvelle fonctionnalité ni amélioration dans cette version.

**Version 1.4.43**

* Expérience de type télévision de possibilité de rejoindre au milieu d’une publicité sans déclencher de suivi de publicité partielle.\
   Exemple : L’utilisateur se joint au milieu (à 40 secondes) d’une coupure publicitaire de 90 secondes composée de trois publicités de 30 secondes. Cette coupure intervient 10 secondes dans la seconde publicité.

   * La deuxième publicité est lue pendant la durée restante (20 secondes), suivie de la troisième publicité.
   * Les dispositifs de suivi des publicités pour la publicité partielle lue (deuxième publicité) ne sont pas déclenchés. Les dispositifs de suivi de la troisième publicité uniquement sont déclenchés.

* Ajout `enableVodPreroll` de type booléen dans l’interface PTAdMetadata . La propriété peut être utilisée pour activer le preroll sur un flux VoD. If `enableVodPreroll` est défini sur NON, PSDK ne joue pas la lecture preroll. Ceci, cependant, n&#39;a aucun impact sur les mid-rolls. La valeur par défaut de `enableVodPreroll` est OUI.
* `closedCaptionDisplayEnabled` API de `PTMediaPlayer` est marquée comme obsolète à partir d’iOS v1.4.43. Pour déterminer si des sous-titres sont disponibles pour une `PTMediaPlayerItem`, examinez la variable `subtitlesOptions` de `PTMediaPlayerMediaItem`.

**Version 1.4.42**

Aucune nouvelle fonctionnalité n’est ajoutée dans cette version. Pour obtenir la liste des problèmes résolus, voir [Problèmes résolus](#resolved-issues).

**Version 1.4.41**

Modifications des API :

* **isSecure**: Une nouvelle API est introduite avec isSecure pour empêcher le lecteur d’enregistrer et de lancer une erreur. La valeur par défaut est true.

* **allowExternalRecording**: Une nouvelle API a été introduite pour permettre la mise en miroir de la lecture pour un contenu sécurisé. La mise en miroir des opérations aériennes est donc traitée comme un enregistrement. `allowExternalRecording` doit être définie sur `True`, pour permettre la mise en miroir des diffusions sur l’écran ou définir sur `False` pour arrêter la mise en miroir de l’affichage pour un contenu sécurisé. Par défaut, `value` est vrai.

**Version 1.4.40**

Aucune nouvelle fonctionnalité.

**Version 1.4.39**

* iOS TVSDK est certifié avec VHL 2.0.1 et avec VHL 2.0.1 avec Nielsen.

* iOS TVSDK est mis à jour afin d’effectuer des requêtes CRS à partir du nouvel hôte Akamai. `primetime-a.akamaihd.net`.

* La nouvelle configuration du nom d’hôte permet la diffusion de ressources CRS via HTTP et HTTPS (SSL) à plus grande échelle.

**Version 1.4.36**

Intégrez et certifiez VHL 2.0 dans iOS TVSDK : Réduisez la barrière de la `VideoHeartbeatsLibrary` en réduisant la complexité des API.

**Version 1.4.34**

**Informations sur la publicité réseau**

Les API TVSDK fournissent désormais des informations supplémentaires sur les réponses VAST tierces. L’identifiant de publicité, le système d’annonces et les extensions d’annonce VAST sont fournis dans `PTNetworkAdInfo` accessible via  `networkAdInfo`  sur une ressource publicitaire. Ces informations peuvent être utilisées pour l’intégration à d’autres plateformes Ad Analytics telles que **Analyses de cheminement**.

**Version 1.4.31**

* **Mesures de facturation** Pour tenir compte des clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte les mesures d’utilisation et les utilise pour déterminer le montant de facturation des clients.

   Chaque fois que TVSDK génère un événement de démarrage de flux, le lecteur commence à envoyer régulièrement des messages HTTP au système de facturation de l’Adobe. La période, appelée durée facturable, peut être différente pour le contenu VOD standard, le pro VOD (publicités mid-roll activées) et le contenu en direct. La durée par défaut de chaque type de contenu est de 30 minutes, mais votre contrat avec Adobe détermine les valeurs réelles.

* **Prise en charge multi-CDN pour les annonces CRS** TVSDK prend désormais en charge le multicanal CDN pour les publicités CRS. En fournissant des détails FTP pour les publicités CRS, vous pouvez spécifier des emplacements CDN autres que le CDN par défaut détenu par l’Adobe, comme [!DNL Akamai].

**Version 1.4.29**

Dans le `PTSDKConfig` , `forceHTTPS` API a été ajoutée.

Le `PTSDKConfig` fournit des méthodes pour appliquer SSL sur les demandes envoyées aux serveurs Adobe Primetime Ad Decisioning, DRM et Video Analytics. Pour plus d’informations, voir `forceHTTPS` et `isForcingHTTPS` sur cette classe. Si un manifeste est chargé via HTTPS, TVSDK conserve l’utilisation du contenu de HTTPS et respecte cette utilisation lors du chargement des URL relatives à partir de ce manifeste.

>[!NOTE]
>
>Les requêtes envoyées à des domaines tiers tels que les pixels de suivi des publicités, les URL de contenu et de publicités, ainsi que les requêtes similaires ne sont pas modifiées. Il est de la responsabilité des fournisseurs de contenu et des serveurs de publicités de fournir les URL prises en charge par HTTPS.

**Version 1.4.18**

Primetime iOS TVSDK prend désormais en charge les créatifs JavaScript VPAID 2.0 pour permettre une expérience publicitaire interactive riche en flux continu. Pour plus d’informations sur VPAID 2.0, voir Prise en charge des publicités VPAID.

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

>[!NOTE]
>
>Le module Nielsen a été supprimé de la version TVSDK. TVSDK sera bientôt mis à jour avec un nouveau module d’intégration Nielsen.

**Secours de la publicité, enchaînement des publicités dans la logique de sélection des publicités (Zendesk #3103)**

Pour les publicités VAST (créatives) avec la règle de secours activée, TVSDK traite une publicité avec un type MIME non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours. Pour plus d’informations, reportez-vous à la section Rebonds de publicité pour les publicités VAST et VMAP.

**Version 1.4.9**

**Signalisation par blackout avec remplacement de contenu alternatif**

Dans le cadre de la mise à jour de la version 1.4 de TVSDK, Adobe prend également en charge l’entrée et le retour des pannes régionales de contenu linéaire. TVSDK peut désormais traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d’interruption même lorsque des programmes alternatifs sont affichés à la place de la programmation d’origine.

**Version 1.4.8**

**Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.5**

* Possibilité d’envoyer des métadonnées avec le démarrage de la vidéo ou le démarrage de la vidéo/publicité/chapitre en tant que données contextuelles.

* Moins de trafic réseau : les pulsations sont moins nombreuses en moyenne et de taille inférieure.

**Version 1.4.7**

* **Prise en charge de l’individualisation sur site**

Prise en charge des installations on-premise du serveur d’individualisation Adobe pour personnaliser la demande d’individualisation du client afin d’accéder à un autre point de terminaison.

* **Protection des sorties basée sur la résolution**

Les stratégies DRM peuvent désormais spécifier la résolution la plus élevée autorisée, en fonction des fonctionnalités de protection de sortie de l’appareil. Par exemple : _Si HDCP est disponible, autorisez la lecture du contenu jusqu’à une résolution de 1 080 p, et si HDCP n’est pas disponible, autorisez la lecture du contenu jusqu’à une résolution de 480 p._

**Version 1.4.4**

* **Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.4.1.1**

   * Ajout de la possibilité de regrouper différents cas d’utilisation d’analyse, à partir d’autres SDK ou lecteurs, avec les composants vidéo essentiels d’Adobe Analytics.
   * Le suivi des publicités a été optimisé en supprimant la variable `trackAdBreakStart` et `trackAdBreakComplete` méthodes. La coupure publicitaire est déduite de la variable `trackAdStart` et `trackAdComplete` appels de méthode .
   * Le `playhead` n’est plus nécessaire lors du suivi des publicités.
   * Ajout de la prise en charge du service d’ID d’Experience Cloud.

* **Intégration du SDK Nielsen**

TVSDK prend désormais en charge l’envoi de balises mTVR et MDPR ID3 au SDK Nielsen sans intégration personnalisée. Pour commencer, téléchargez le SDK d’application Nielsen iOS 3.1.2.19 et suivez les instructions figurant ici dans le guide des programmeurs iOS.

**Version 1.4.0**

* **Signalisation par blackout avec remplacement de contenu alternatif**

Dans le cadre de la mise à jour de la version 1.4 de TVSDK, TVSDK prend également en charge l’entrée et le retour de pannes régionales de contenu linéaire. TVSDK peut désormais traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d’interruption même lorsque des programmes alternatifs sont affichés à la place de la programmation d’origine.

* **Supprimer/Remplacer des publicités C3**

Désormais, aucun travail de préparation supplémentaire n’est nécessaire pour insérer dynamiquement de nouvelles publicités dans les ressources vidéo à la demande (VOD) qui sortent de la fenêtre C3. TVSDK fournit désormais une API pour supprimer des plages de contenu personnalisées et insérer dynamiquement de nouvelles publicités. Cette nouvelle fonctionnalité puissante est également utile dans les cas où le contenu en direct/linéaire est diffusé pendant la diffusion et est immédiatement retiré pour être utilisé comme contenu à la demande sans temps approprié pour nettoyer la ressource.

## Problèmes résolus {#resolved-issues}

Lorsque la résolution est associée à un problème signalé, une référence Zendesk s’affiche, par exemple ZD#xxxxx.

<!-- 

Comment Type: draft

 <p>All TVSDK customers who use CRS are strongly encouraged to upgrade to TVSDK 1.4.39 or latest on iOS and Android. This upgrade is a drop-in replacement to the existing app implementation. After the upgrade, check for the CRS creative URL requests in a proxy tool (for example, Charles) to verify that the version in the path reflects version 3.1. For example:</p> 
 <p><span class="code">https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8</span></p> 

-->

<!--
Comment Type: draft

 <p>TVSDK versions earlier than version 1.4.28 sometimes exhibit a long delay in the startup time when ad-enabled content is played on devices that are running on iOS 10. To resolve this issue, upgrade to version 1.4.28 or later. Version 1.4.28 was released on August 31, 2016, and iOS 10 was released on September 13, 2016.</p> 
-->

**iOS TVSDK 3.13**

* (ZD 42085) - Problèmes de lecture sur les flux CMAF.

* (ZD-43215) - Blocage lors de la fermeture du lecteur alors qu’une publicité est en cours.

* (ZD 43210) - La lecture HLS iOS se bloque lorsque le sous-titre WebVTT est activé.

**iOS TVSDK 3.12**

* La diffusion en direct échoue après 15 minutes de lecture lors de l’utilisation de TVSDK pour iOS 3.10.

### Problèmes résolus dans les versions précédentes {#resolved-issues-previous}

**iOS TVSDK 3.11**

* (ZD#40998) - Le `isFallbackOnInvalidCreativeEnabled` entraîne le blocage de l’application.

* (ZD#41289) - `NSInvalidArgumentException` est observé avec la méthode `customParams` provoquant le blocage de l’application.

**iOS TVSDK 3.10**

(ZD#40943) - Le lecteur TVSDK ne se déclenche pas `PTMediaPlayerStatusError` lorsque le réseau est indisponible.

**iOS TVSDK 3.9**

(ZD#40272) - iOS TVSDK ne parvient pas à lire les sous-titres VTT avec une erreur 101001 et entraîne le gel de l’application.

**iOS TVSDK 3.8**

* (ZD#40087) - iOS se bloque avec une erreur de lecteur pour le contenu VOD expiré.

* (ZD#40083) - Les publicités preroll ne sont pas lues pour le flux vidéo en direct avec `OpportunityGenerator` et le lecteur renvoie une erreur.

* (ZD#39828) - `CurrentItem` n’a pas l’annotation d’invalidation, ce qui provoque un blocage du lecteur lorsque l’état du lecteur contenu dans la notification est `PTMediaPlayerStatusStopped`.

**iOS TVSDK 3.7**

(ZD#38961) - La lecture du contenu dans la fenêtre &quot;Image dans l’Image&quot; (PiP) échoue une fois la lecture d’un contenu terminée, lorsque plusieurs contenus sont configurés pour être lus dans le PiP.

**iOS TVSDK 3.6**

Aucun nouveau problème dans cette version.

**iOS TVSDK 3.5**

Aucun nouveau problème dans cette version.

**Version 3.3**

(ZD#37820) - Ajout de la liste autorisée pour l’en-tête personnalisé HS-Id, HS-SSAI-TAG.

**Version 3.2**

* **Ticket#36588** - Un plantage du lecteur est observé lorsque la méthode MediaPlayer STOP est appelée.

Correction d’un blocage intermittent observé lorsque la méthode STOP est appelée pour quelques diffusions avec sous-titres.

* **Ticket#37080** - Requêtes en double affichées pour les appels Manifest.
Correction des demandes en double pour les URL de manifeste lors de la lecture. TVSDK effectue désormais un appel par manifeste.

* **Ticket#37** - Échec de la règle de normalisation CRS avec le type de correspondance eq Correction d’un cas où le lecteur se bloquait lorsqu’il était rencontré avec la dernière règle de normalisation définie pour les noms d’hôtes avec un type de correspondance &quot;eq&quot;.

**Version 3.1**

**Ticket #36313** - Résultats intermittents imprévisibles pendant les coupures publicitaires linéaires Correction de la lecture intermittente pendant les coupures publicitaires linéaires dans le flux en direct.

**Version 3.0.1**

**Ticket36948** - CRS - Ordre de sélection des ressources incohérent sur iOS 12 La ressource sélectionnée pour CRS n’est pas toujours la variante de qualité la plus élevée renvoyée dans une réponse VAST ou VMAP.

**Version 3.0**

* **Ticket35311** - L’état du lecteur ne passe pas en PAUSE lors d’une interruption d’appel téléphonique Ajout d’un gestionnaire d’interruption pour empêcher le lecteur de s’interrompre. En cas d’interruption, l’état du lecteur devient EN PAUSE, puis la lecture reprend en cliquant sur le bouton de lecture.

* **Ticket36685** - Ressources en direct : l’incohérence temporelle avec la progression de l’heure du lecteur et l’heure du marqueur de l’éditeur de texte enrichi sont calculées pour les marqueurs de l’éditeur de texte enrichi qui sont en avance sur le point de production.

* **Ticket36492** - `currentTime` et `localTime` ne sont pas mises à jour lors de la recherche d’une nouvelle position pendant l’heure en pause du lecteur peut désormais être définie sur zéro au cas où le lecteur serait en pause ; auparavant, l’heure actuelle était définie sur zéro uniquement en état de lecture.

**Version 1.4.45**

* **Ticket36294** - iOS TVSDK non fonctionnel avec Xcode 10 Correction des problèmes de compilation avec TVSDK sur XCode 10. En raison des dix exigences Xcode, les applications créées à partir de TVSDK pour iOS 1.4.45 nécessitent une cible de déploiement minimale comme iOS 7.0.

* **Ticket36321** - Incohérence observée dans la plage pouvant faire l’objet d’une recherche entre `PTMediaPlayer` et `AVPlayer` instance dans _Jouer_ état.

* **Ticket36493** - `libstdc++` Prise en charge sur iOS 12 Correction des problèmes de compilation avec TVSDK sur iOS 12. Les applications créées à partir de TVSDK pour iOS 1.4.45 requièrent une cible de déploiement minimale comme iOS 7.0.

**Version 1.4.44**

* **Ticket34683** - Le Temps De Progression De La Lecture De La Publicité Est Négatif

Des vérifications supplémentaires sont effectuées pour gérer le cas lorsqu’il existe une incohérence entre la durée signalée par le serveur de publicités et le contenu réel de la publicité.

* **Ticket34801** - `currentTime` et `localTime` n’étaient pas mis à jour lors de la recherche d’une nouvelle position pendant l’état en pause L’heure actuelle du lecteur peut désormais être définie sur zéro au cas où le lecteur serait en pause ; auparavant, l’heure actuelle était définie sur zéro uniquement en état de lecture.

* **Ticket35037** - Lire les étals avec une URL incorrecte lors du retour d’une insertion de publicités basée sur un signal.
Correctif amélioré fourni pour le problème fermé #34385 dans la version 1.4.42. Ajout du code de gestion des exceptions et des vérifications annulées pour rendre la file d’attente des opérations plus robuste.

**Version 1.4.43**

* (ZD#32990) - iOS : Lecture du contenu au lieu de publicités sur certains points de repère. `selectedMediaOptionInMediaSelectionGroup` L’API qui faisait partie de l’interface AVPlayerItem a maintenant été déplacée sous `AVMediaSelection` dans iOS 11. Le problème a été résolu à l’aide de cette nouvelle API.

* (ZD#33683) Suppression de TVSDK `==` suffixe des chaînes de métadonnées. Le problème est résolu dans la logique d’analyse.

* (ZD#33905) - iOS TVSDK appelle les fichiers de manifeste avec deux agents utilisateurs. Le problème de l’agent utilisateur a été corrigé dans le premier appel m3u8 (nouveau cas d’installation). Les M3u8 ont maintenant les mêmes agents utilisateur pour tous les appels.

* (ZD#34293) - Les pré-roulements insérés sur les flux LINEAR ne s’exécutent pas correctement sur iOS11. Le problème est résolu pour les publicités preroll.

* (ZD#34684) : lorsque la stratégie de saut de publicité est appliquée, les images de publicité preroll s’affichent pendant quelques secondes. une nouvelle API, `enableVodPreroll` a été introduit pour désactiver la lecture preroll dans la lecture vod. La valeur par défaut de cette API est _Oui_. L’API assure le saut du groupement de contenu publicitaire dans le contenu principal.

* (ZD#34765) - Après avoir appelé `stop()`, peu de segments de flux de transport sont toujours téléchargés. Amélioration de la fonction `Stop()` API pour éviter de télécharger les segments supplémentaires.

* (ZD#34865) - Publicités preroll pour [!DNL Livestream] sont tronquées sur iOS. En ce qui concerne iOS11 et l’ajout d’une vérification supplémentaire pour confirmer si le flux est pré-roll ou de contenu principal, résout ce problème.

* (ZD#35093) - Correction d’un scénario de basculement en raison duquel, si la variante Principale du flux échoue au démarrage (renvoie 404), la lecture ne passe pas au flux de sauvegarde.

**1.4.42 (1.4.42.118)**

* (ZD#34385) - La lecture se bloque avec une URL incorrecte lors du retour d’une insertion de publicités basée sur un signal.

   Augmentation du nombre maximal de répétitions pour `CustomAVAssetLoaderOperations`, de sorte que les lectures du manifeste puissent continuer à s’exécuter.

* (ZD#34373) - Les utilisateurs finaux ne peuvent pas diffuser vers des appareils connectés au HDMI lorsque l’enregistrement de diffusion est interdit.

* (ZD#32678) - TVSDK ne collecte pas les ID de publicité corrects sur iOS.

   L’ID de publicité de la publicité finale est maintenant récupéré dans les pings VHL s’il existe des redirections VAST/VMAP.

* (ZD#33904) - TVSDK n’est pas enregistré pour les notifications AVFfoundation `AVAudioSessionMediaServicesWereLostNotification` et `AVAudioSessionMediaServicesWereResetNotification`.

   `PTMediaServicesWereLostNotification` et `PTMediaServicesWereResetNotification` peut désormais être enregistré sur l’application du lecteur afin d’obtenir les notifications lorsque les services Media sont réinitialisés ou perdus.

* (ZD#33815) - Les clients ne peuvent pas mettre à jour leurs règles CRS de normalisation et de hiérarchisation sans avoir à mettre à jour l’application.

   Ajout de la fonction `getCRSRulesJsonURL` et `setCRSRulesJsonURL` API vers le TVSDK iOS .

**Version 1.4.41 (1.4.41.76)**

* (ZD #34464) - Problèmes de création d’une application de référence avec TVSDK version 1.4.41

   À compter de cette version, Xcode 9 est requis pour compiler TVSDK pour iOS.
* (ZD #29456) - Le début de la lecture dans un état en pause

   Correction du problème de mise en pause qui se produisait lorsque la vidéo était en pause lors de la saisie d’un élément Airplay.
* (ZD #30371) - L’heure de début d’AdBreak change lorsque nous insérons plus de deux publicités dans un flux linéaire.

   Correction de l’erreur lors de la tentative de lecture de contenu sur Apple TV, qui empêchait complètement la lecture.
* (ZD #32146) - Non `PTMediaPlayerStatusError` est reçu pour le contenu HLS Live lors du blocage d’iOS 11 dev beta

   Non `PTMediaPlayerStatusError` est reçu pour le contenu HLS Live et VOD sur le blocage à l’aide de Charles (Déposer la connexion et 403).

* (ZD #29242) - Échec de la lecture vidéo lors de la lecture des diffusions avec les publicités activées.

   Lorsque les publicités sont activées et qu’AirPlay est activé au démarrage de la lecture d’une vidéo, la lecture vidéo ne démarre jamais et aucune erreur n’est affichée.

* (ZD#33341) - `DRMInterface.h` déclenche des avertissements de création dans Xcode 9.

   Correction de deux prototypes de blocs dans `DRMInterface.h` qui manquaient le mot &quot;void&quot; dans leurs listes de paramètres.

* (ZD#31979) - Ne compile/n’exécute pas lorsqu’il s’agit d’iOS 10 ou d’une version ultérieure pour iPhone 7/iPhone7+.

   Correction de la compilation des documents IB pour les versions antérieures à iOS 7 qui n’est plus prise en charge.

* (ZD#32920) - Écran vierge au sein d’une coupure publicitaire et sans fin de la coupure publicitaire.

   Lorsqu’une coupure publicitaire présente des instances de publicité et qu’une fois l’instance de publicité terminée, un écran vide s’affiche.

* (ZD#32509) - Désactiver l’enregistrement d’écran d’iOS 11 Désactivez l’enregistrement d’écran sur iOS 11.

* (ZD#33179) - Échec d’événement intermittent sur iOS11.

   Correction de l’échec de l’événement sur iOS 11.

**Version 1.4.40** (1.4.40.72)

* (ZD #32465) - Le lecteur ne peut pas gérer les listes de lecture fusionnées.

   Appeler `finishLoadingWithError`(avec : Erreur) pour la fondation A/V afin d’essayer d’autres diffusions/de déclencher le basculement.

* (ZD #31951) - Erreur TVSDK pendant les rotations de licence.

   Correction du problème de rotation des licences.
* (ZD #31951) : écran vierge au sein d’une coupure publicitaire, sans fin de la coupure publicitaire.

   Correction d’un problème en raison duquel les publicités Facebook VPAID renvoyaient souvent plusieurs blocs CDATA dans une seule `<AdParameters>` Noeud VAST.
* (ZD #33336) - iOS TVSDK - Les capsules publicitaires ne sont pas remplies, bien que suffisamment de publicités aient été renvoyées par la roue libre.

   Création d’une relation parent-enfant entre la publicité de séquence et la publicité de secours, ainsi que d’un tri basé sur la séquence et l’index parents.

**Version 1.4.39** (1.4.39.43)

* (ZD #32178) - La version du TVSDK iOS est incorrecte.

   La sortie de la version TVSDK dans les fichiers journaux était 1.0.211. Elle est corrigée pour générer la version correcte.

* (ZD #32199) - Chargement différé de la publicité - La vidéo ne s’affiche pas pour le contenu.

   La frise chronologique d’Adobe locale qui n’était pas initialisée auparavant est maintenant actualisée avant l’utilisation.

* (ZD #27528) : vidéo, audio ou les deux se figent 1 à 45 secondes après le début de la lecture d’une ressource, si le son secondaire n’est pas défini sur la valeur par défaut sur iOS 1.2.

   Préparez et informez les pistes audio à l’état Prêt .

* (ZD #30411) - Si vous choisissez une langue Sap secondaire, vous risquez d’obtenir des résultats inattendus, comme l’absence d’audio ou d’audio incorrect.

   Préparez et informez les pistes audio à l’état Prêt .

* (ZD #32199) - Chargement différé de la publicité - La vidéo ne s’affiche pas pour le contenu.

   La frise chronologique d’Adobe locale qui n’était pas initialisée auparavant est maintenant actualisée avant l’utilisation.

* (ZD #27528) : vidéo, audio ou les deux se figent 1 à 45 secondes après le début de la lecture d’une ressource, si le son secondaire n’est pas défini sur la valeur par défaut sur iOS 1.2.

   Préparez et informez les pistes audio à l’état Prêt .

* (ZD #30411) - Si vous choisissez une langue Sap secondaire, vous risquez d’obtenir des résultats inattendus, comme l’absence d’audio ou d’audio incorrect.

   Préparez et informez les pistes audio à l’état Prêt .

**Version 1.4.38** (1.4.38.860)

* (ZD #29281) - iOS : Ajout d’AdSystem et d’un ID créatif aux requêtes CRS

Utilisation de l’ID de création et d’AdSystem dans la requête CRS en fonction des règles de normalisation CRS

* (ZD #29176) - Blocage `PTAdPolicyDeligate` `satAdBreakAsWatched:position`

Le blocage dû à un AdBreak vide est maintenant géré.

* (ZD #30125) - Les publicités programmatiques ne fonctionnent pas sur la plateforme iOS

Ajout de la prise en charge des annonces programmatiques dans iOS.

* (ZD #30782) - Notification #EXT-X-PROGRAM-DATE-TIME

L’événement de métadonnées minutée n’est pas déclenché pour la balise # EXT-X-PROGRAM-DATE-TIME avec les flux DRM LIVE.

**Version 1.4.37 (1.4.37.842)**

* (ZD #28950 ) - Problème de lecture VOD

Problème de lecture lorsque la balise # EXT-X-PLAYLIST-TYPE dans le flux est définie sur Événement plutôt que VOD

* (ZD #29281) - iOS : Ajout d’AdSystem et d’un ID créatif aux requêtes CRS

Utilisation de Creative Id et d’AdSystem dans la requête CRS basée sur les règles de normalisation CRS.

* (ZD #29462) - Une publicité TremorHub dans A&amp;E VOD provoque un blocage des applications iOS

**Version 1.4.36 (1.4.36.835)**

* (ZD #29418) - Les erreurs de durée 0 (#EXT-X-CUE-OUT:0.000) provoquent l’arrêt ou le blocage de la lecture du TVSDK iOS.

Le problème est résolu et la lecture démarre correctement.

* (ZD #29462) - Publicité dans VOD provoquant un blocage sur iOS TVSDK .

Le problème est résolu. iOS TVSDK génère une `exception(AUDNetworkAdInfo::initWithAdId)` et de ne pas le gérer. L’exception est due à un identifiant de publicité vide.

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

* (ZD #28481) - Pause libre en raison de l’ajout d’une clé incorrecte à la fin d’une coupure publicitaire pour ces flux FER

Pour un flux FER, la clé avant la coupure publicitaire est insérée après la fin de la coupure publicitaire. Ce problème a été résolu en ajoutant la variable *Dernière clé vue* à la fin de la coupure publicitaire.

**Version 1.4.3** (1.4.33.803 pour iOS 6.0+)

* (ZD# 21701) Activation de CRS pour les sous-comptes

Activé en envoyant l’URL de création d’origine pour la demande 1401 CRS au lieu de l’URL normalisée, conformément aux exigences du serveur principal CRS.

* (ZD# 26218) - `PSDKResources.bundle` problème de chargement

Ce problème a été résolu en mettant à jour le chargement des ressources pour qu’il recherche tous les lots disponibles.

* (ZD# 27460) Premier appel publicitaire mid-roll - POST à `cdn.auditude.com` retour 403.

Le nouveau compte CDN ne peut pas gérer une requête CDN de POST. Ce problème a été résolu en mettant à jour le code pour que la variable `cdn.auditude.com` demande d’annonce à GET au lieu de POST.

**Version 1.4.32** (1.4.32.792 pour iOS 6.0+)

* (ZD# 27132) Prise en charge des valeurs décimales pour les coupures publicitaires VMAP.

Lorsque le contenu n’était pas segmenté le long des coupures publicitaires définies, des entiers provoquaient des emplacements publicitaires inattendus. Le problème a été résolu en ne convertissant pas les valeurs décimales en nombres entiers.

* (ZD# 27189) Le contenu AES avec la balise EXT-X-DISCONTINUITY-SEQUENCE n’est pas lu correctement.

Le problème a été résolu en plaçant la balise au début de la liste de lecture.

**Version 1.4.31** (1.4.31.785 pour iOS 6.0+)

* (ZD# 24528) Mise en oeuvre de mesures d’utilisation du SDK TVSDK pour la facturation

Pour plus d’informations, voir [Mesures de facturation].

* (ZD# 24642) Prise en charge du mode &quot;Image dans l’Image&quot; pour TVSDK

La fonctionnalité d’image dans l’image, qui ne fonctionnait pas parfois correctement, a été corrigée.

* (ZD# 25246) Signaux de coupure publicitaire incorrects

Ce problème a été résolu en alignant les balises de discontinuité entre les manifestes de variantes.

* (ZD# 26218) Le processus de création d’application devient complexe lors de la tentative d’inclusion `PSDKLibrary.framework` dans la structure d’application du client

Ce problème a été résolu en regroupant la variable `PSDKLibrary.framework` sur demande.

* (ZD# 26364) Prise en charge multi-CDN pour les publicités CRS

Pour plus d’informations, voir Prise en charge de plusieurs CDN pour CRS Ad Delivery.

* (ZD# 27028) Délai de lecture de certaines diffusions dans iOS 10.

Ce problème a été résolu en fournissant une solution pour les diffusions qui n’ont pas d’extension M3U8.

**Version 1.4.30** (1.4.30.754 pour iOS 6.0+)

Les problèmes suivants ont été résolus pour TVSDK dans cette version :

* (ZD# 24180) Ajoutez un en-tête personnalisé à placer sur la liste autorisée.

Un nouvel en-tête personnalisé a été ajouté à la liste autorisée TVSDK.

* (ZD# 25016) Le flux de basculement est sélectionné de manière aléatoire lorsque les paramètres de contrôle ABR sont définis.

Ce problème a été résolu en conservant les flux ABR dans l’ordre lorsque les paramètres ABR sont fournis avec la variable `initialBitrate` sur un flux contenant des URL de basculement. Cela évite de lire les flux de basculement plutôt que Principaux.

* (ZD# 25076) Blocage `PTAuditudeAdResolver loadComplete`

Correction du problème de blocage survenant lors du démarrage/de l’arrêt rapide de plusieurs instances PTMediaPlayer avec des publicités.

* (ZD# 25960) Aucune balise d’abonnement supplémentaire n’est nécessaire pour déclencher les diffusions de notification de changement de métadonnées

Correction du problème en raison duquel une balise abonnée n’était pas avertie lorsqu’elle apparaissait avant le premier segment dans le manifeste.

* (ZD# 26084) PSDK lance un 106000.101000.Erreur de décodage -11833 introuvable lors de la transition de la dernière coupure publicitaire vers le contenu de divertissement

Lorsque l’heure de début de la dernière coupure publicitaire du VMAP est antérieure à la fin de la durée totale, dans certaines conditions, la clé n’est pas insérée avant la fin de la dernière coupure publicitaire. Ce problème a été corrigé.

* La bibliothèque Video Heartbeat (VHL) a été mise à jour vers la version 1.5.9 afin de résoudre les problèmes suivants :

* (ZD #22351) VHL - Analytics : Durée de la ressource vidéo en direct

Ce problème a été résolu en ajoutant la variable  `assetDuration`  API vers `PTVideoAnalyticsTrackingMetadata` pour mettre à jour la durée des ressources pour les flux en direct/linéaire et fournir une logique de vérification du flux en direct.

* (ZD# 22675) VHL - Analytics : Mise à jour de la durée des ressources vidéo en direct

Ce problème est le même que ZD #22351.

* (ZD #25908) VHL - Analytics : Blocage de l’événement Adobe Heartbeat

Ce problème a été résolu en mettant à jour la mise en oeuvre afin d’utiliser la dernière version de VHL pour iOS version 1.5.9 afin d’améliorer la stabilité et les performances.

* (ZD #25956) VHL - Analytics : Blocage lors de la lecture répétée de vidéos

Ce problème est le même que ZD #25908.

**Version 1.4.29** (1.4.29.743)

* (ZD# 23901) Les publicités tierces ne sont pas lues

Ce problème a été résolu en passant à la structure d’URL CRS v3 pour inclure l’ID de zone dans l’URL reconditionnée.

* (ZD #25183) Problèmes liés à la lecture DRM sur tvOS et iOS

Ce problème a été résolu en fournissant la prise en charge de plusieurs balises clés nécessaires pour la prise en charge de DRM multiple.

* (ZD# 25334) TVSDK ne parvient pas à lire un contenu partagé cDVR

Ce problème a été résolu en empêchant TVSDK de convertir des chaînes vides en URL absolues.

* (ZD# 25347) Définition de l’en-tête HTTP personnalisé sur AVURLAset

Prise en charge des en-têtes personnalisés sur ses requêtes de segment via le `PTNetworkConfiguration` a été ajoutée.

**Version 1.4.28** (1.4.28.722)

* (ZD #24549) Plusieurs appels de suivi des publicités

Ce problème a été résolu en mettant à jour le gestionnaire de chronologie afin d’écouter les notifications sur un objet spécifique lorsque plusieurs lecteurs sont créés.

* (ZD #24758) `PTManifestLogger` ne prend pas en charge iOS 8

Ce problème a été résolu en mettant à jour la bibliothèque de l’utilitaire de journalisation vers la cible de déploiement de la version 7.0.

* (ZD #24775) Diffusion différée en raison de publicités

Ce problème a été résolu en calculant correctement la dérive de durée sur les listes de lecture d’événements.

* (ZD #24799) Certains épisodes ne sont pas lus sur l’application iOS

Ce problème a été résolu en utilisant le serveur web local pour les sous-titres lorsque les fichiers WebVTT sont géolimités.

**Version 1.4.27** (1.4.27.711) pour iOS 6.0+

* (ZD #24089) - Optimisations de la résolution des publicités sur les diffusions DVR longues

Ce problème a été résolu en ajoutant plusieurs optimisations afin de réduire le temps nécessaire au traitement de la fenêtre de l’enregistrement numérique dans les flux linéaire/en direct.

* (ZD #21554) - Balises d’erreur TVSDK non déclenchées pour `application-type = video/mp4`

Ce problème a été résolu en permettant au lecteur d’envoyer un ping aux URL de suivi des erreurs correctes sur les formats de ressources non valides.

* (ZD #24424) - Blocage de type `EXC_BAD_ACCESS KERN_INVALID_ADDRESS` provient de l’intérieur `PSDKLib` pour iOS sur les appareils plus récents.

Le blocage qui s’est produit en raison d’une instance de lecteur multimédia déallouée, lorsque la lecture est basculée rapidement entre les différentes diffusions, a été corrigé.

* (ZD #24575) - Blocage dans TVSDK sur les périphériques 32 bits lors de la `enableDebugLog=true`

Correction du problème dans le format de journal qui provoquait le blocage sur les appareils 32 bits lorsque la journalisation était activée.

**Version 1.4.26** (1.4.26.702) pour iOS 6.0+

* (ZD# 20213) - TVSDK FW doit être dynamique/modulaire pour XCode7

Corrigé en mettant à jour les bibliothèques avec la prise en charge des modules

**Version 1.4.25** (1.4.25.684) pour iOS 6.0+

* (ZD #19629) - Une vidéo en direct se met en pause lors de la saisie d’un élément Airplay sur ATV 4

Ce problème a été résolu en ajoutant une période d’attente après la suppression des anciens éléments, mais avant l’ajout de nouveaux éléments à la variable `AVQueuePlayer`. En l’absence de délai d’attente, les notifications sont envoyées à l’élément incorrect.

* (ZD #19856) - Aucun sous-titre ne s’affiche lorsqu’il est activé par défaut.

Les problèmes de la liste de lecture webvtt, qui empêchait l’affichage correct des sous-titres, ont été corrigés.

* (ZD #21590) - Performances vidéo et suivi dans les dernières versions d’origine

Problème lié à la longueur de la vidéo manquante dans `VideoAnalytics` a été corrigé.

* (ZD #20202) - La définition d’un style de sous-titres personnalisés bloque l’application iOS.

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

Ce problème a été résolu en mettant à jour la logique afin d’afficher le lecteur si la lecture d’une publicité VPAID échoue.

* (ZD #20101) - L’implémentation de chapitre personnalisée déclenche l’événement de début de chapitre pendant la lecture de la publicité.

Ce problème a été résolu en mettant à jour `VideoAnalyticsTracker` pour détecter correctement le début/la fin du chapitre lors de la transition entre les limites de chapitre et non-chapitre.

* (ZD #20784) - Analytics : Déclenchement du contenu terminé pour les transitions vidéo en direct

Ce problème a été résolu en ajoutant une logique pour déclencher manuellement la fin du contenu au cours d’une session de suivi vidéo.

Les bibliothèques suivantes ont été mises à jour :

* Bibliothèque AdobeMobile vers 4.10.0
* Bibliothèque VHL vers 1.5.6
* Bibliothèque VHL-Nielsen vers la version 1.6.7
* (ZD #21855) - Les sous-titres ne sont pas lus après le mid-roll

Dans ce problème, les balises de discontinuité en double n’affichaient pas les sous-titres après le parcours intermédiaire. Ce problème a été résolu en supprimant les balises de discontinuité les unes à côté des autres.

* (ZD #21994) - Chaîne hors limites dans `PTHLSUtils`

La cause la plus probable du blocage est lorsqu’une clé EXT-X-KEY comporte une URL entourée de guillemets.

* ZD #22074) - `AUDVAST` Blocage une fois par minute sur iOS

Dans la version 1.4.23, le blocage dû à la présence de caractères non sûrs dans une URL de redirection VAST a été corrigé. Toutefois, TVSDK continuait à ignorer ces publicités.

Ce problème a été résolu en gérant les caractères non sûrs et en autorisant la lecture des publicités.

* (ZD #22694) - `PTMediaPlayer`.  La vue est masquée par le lecteur

Ce problème a été résolu en mettant à jour la logique afin d’afficher le lecteur si la lecture d’une publicité VPAID échoue.

**Version 1.4.23** (1.4.23.641) pour iOS 6.0+

* (ZD #18016) - Aucune réponse du SDK Primetime avec une mauvaise condition réseau

Ce problème a été résolu en améliorant la notification d’erreur lors d’une erreur fatale de `AVFoundation` se produit et pour permettre à l’application de gérer le redémarrage après l’erreur.

* (ZD #20580) - Blocage `PTSplicerManager`

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

* (ZD #21224) - Prise en charge de la lecture pour les diffusions à jetons en provenance d’Akamai

Des API ont été ajoutées au `PTNetworkConfiguration` pour ajouter des cookies en tant que paramètres d’URL pour les segments de certains flux segmentés en jetons Akamai.

* (ZD #21287) - Journal externe

Correction d’un problème lié à certaines instructions de journal affichées par défaut dans la console xcode même lorsque la journalisation est désactivée.

* (ZD #21446) - Les événements de coupure publicitaire ne sont parfois pas déclenchés par TVSDK

Dans les flux EVENT, les coupures publicitaires ne sont pas déclenchées correctement dans la version précédente. Ce build résout ce problème.

**Version 1.4.21** (1.4.21.605) pour iOS 6.0+

* (ZD #20749) - Les secours ignorent les réponses VAST non vides ; Déclenchement des URL de suivi des publicités supplémentaires

Un problème lié aux pings en double sur les annonces de secours a été résolu.

**Version 1.4.20** (1.4.20.590) pour iOS 6.0+

* (ZD #18639) - Le TVSDK utilise un processeur/des ressources excessifs sur une longue ressource d’enregistrement à chaud.

L’utilisation excessive du processeur/des ressources a été corrigée dans les deux niveaux. Tout d’abord en laissant la fonction de mise à jour de l’heure s’exécuter sur une file d’attente globale, au lieu du thread principal, et en optimisant l’utilisation du processeur pour analyser le manifeste avec le m3u8 traité et mis en cache précédemment.

* (ZD #19349) - Les publicités preroll sont ignorées lors du ralentissement de la connexion réseau.

Ce problème a été résolu en fournissant un événement de délai d’expiration (requestTimeout) à l’application et à la variable `adMetadata.adRequestTimeout` API pour remplacer le délai d’expiration de 10 secondes par défaut.

* (ZD #19446) - Notification manquante sur les flux en direct

Ce problème a été résolu en permettant à l’application de s’abonner à la variable `EXT-X-PROGRAM-DATE-TIME` sur les flux en direct.

* (ZD #19459) - Blocage lors de la préparation d’un fichier audio alternatif avec `PTMediaPlayerItem` `prepareAudioOptionsWithAVMediaSelectionOptions`
* (ZD #19460) - Blocage - `[PTMediaPlayerItem prepareSubtitlesOptionsWithAVMediaSelectionOptions:nonForcedOptions:]`

Ce problème est le même que Zendesk #19459.

* (ZD #19574) - Le TVSDK ne renvoie pas de données de réponse M3U8 pour le contenu DRM ou non DRM.

Au chargement initial du fichier manifeste dans `PTMediaPlayerItem.prepareToPlay`, si le chargement du manifeste a échoué, TVSDK ne signale pas le corps de la réponse d’échec à l’application.

Ce problème a été résolu en permettant à TVSDK de signaler la réponse à l’échec comme une erreur à l’application.

* (ZD #19615) - La logique de secours ne fonctionne pas

Dans l’implémentation actuelle, les publicités de secours ont été ignorées et n’ont pas été reconditionnées, sauf si elles sont au format m3u8. Ce problème a été résolu en ajoutant également la prise en charge du reconditionnement des annonces de secours.

* (ZD #19770) - TVSDK ne parvient pas à lire le contenu AES protégé avec une redirection 302.

Le problème de redirection a été corrigé, car l’URL de redirection était effacée par `cleanConnectionData` avant de pouvoir être utilisé pour analyser le manifeste.

* (ZD #19856) - Les sous-titres ne s’affichent pas pour certains débits lorsqu’ils sont activés par défaut.

Ce problème a été résolu en gérant l’erreur provenant d’iOS pour les segments des diffusions dans lesquels les sous-titres ne s’affichent pas.

* (ZD #19868) - Le TVSDK se bloque lorsqu’un créatif non valide fait l’objet d’un trafic.

Le blocage dans TVSDK qui désaffectait incorrectement une instance de l’analyseur vaste a été corrigé.

* (ZD #20180) - Les publicités VPAID sont parfois ignorées.

Le type MIME JavaScript n’était pas toujours inclus ou considéré comme un type MIME valide. Ce problème a été résolu en incluant JavaScript comme type MIME valide.

* (ZD #20749) - Les secours ignorent les réponses VAST non vides ; Déclenchement des URL de suivi des publicités supplémentaires

Le problème où certains créatifs ne sont pas reconditionnés a été corrigé.

**Version 1.4.19** (1.4.19.563) pour iOS 6.0+

* ZD #18639) - Le TVSDK utilise un processeur/des ressources excessifs sur une longue ressource d’enregistrement à chaud.

Ce problème a été résolu en optimisant la réécriture de la liste de lecture DRM m3u8 pour mettre en cache les bits de la liste de lecture qui ont été précédemment réécrits. Cela est particulièrement pertinent lorsque vous lisez des flux m3u8 en direct pour lesquels le m3u8 est téléchargé après chaque téléchargement de segment.

* (ZD#18956) - `player.drmManager` est nul lorsque le point d’arrêt est défini dans le lecteur de démonstration iOS

Ce problème a été résolu en mettant à jour la variable `PTMediaPlayer.drmManager` Mise en oeuvre de l’API pour sélectionner DRM Manager dans la structure DRM.

**Version 1.4.18** ( 1.4.18.557) pour iOS 6.0+

* (ZD #18844) Suivi du curseur de lecture pour le contenu en direct dans le lecteur iOS.

Ce problème a été résolu en permettant aux applications de définir leur propre valeur de curseur de lecture.

* (Zendesk #18518) - Si le nom de la vidéo n’est pas spécifié, le nom de TVSDK est défini par défaut sur * PSDK Player.*

Ce problème a été résolu en supprimant la valeur par défaut du nom du lecteur.

**Version 1.4.17** (1.4.17.545) pour iOS 6.0+

* (Zendesk #2228) - Amélioration de TVSDK pour renvoyer la réponse JSON de la récupération d’un manifeste

Au lieu d’envoyer une erreur lorsque le contenu n’est pas M3U8, la structure DRM renvoie une valeur nil DRMMetadata. Le problème a été résolu en ajoutant des métadonnées pour exposer le contenu lorsque la notification M3U8_PARSER_ERROR se produit.

* (Zendesk #2231) - Erreur retournée lors de la récupération du manifeste non disponible dans MediaPlayerNotification

Même résolution que Zendesk #2228

* (Zendesk #3304) - VAST 3.0 `[ERRORCODE]` macro non renseignée

Le problème où la variable [!DNL Auditude] Le SDK ne parvient pas à envoyer un ping lorsque l’URL de suivi comporte des espaces au début, mais qu’elle a été résolue.

* (Zendesk #17294) - Blocage [!DNL SecKeyRawSign]

Un blocage possible lorsque le code du client utilise la chaîne de clé a été résolu.

* (Zendesk #18008) - Prise en charge des cookies pour iOS 8+ pour la prise en charge des flux segmentés en unités lexicales

Les flux segmentés en jetons Akamai exigent que les cookies soient envoyés sur les demandes de segments, ce qui n’était pas possible sur iOS 7 et versions antérieures. Depuis iOS 8, Apple a ajouté une API qui permet la transmission de cookies pour les demandes de segments. Cette prise en charge est désormais disponible dans TVSDK. Une prise en charge a également été ajoutée pour l’envoi d’un agent-utilisateur, le cas échéant.

* (Zendesk #18166) - TVSDK 1.4.15 fournit des centaines d’avertissements lors de la compilation avec `DWARF` avec `dSYM` options de fichier

Tous les avertissements ont été résolus.

**Remarque**: Des bibliothèques compatibles avec tvOS ont été ajoutées pour TVSDK .

**Version 1.4.16** (1.4.16.1454)

* Zendesk #3875 - Blocages S de l’onglet pendant la lecture

Restauration de la dépendance d’OKHTTP sur [!DNL Auditude] pour CRS, car TVSDK utilise désormais directement la variable `httpurlconnection` au lieu de curl. Le problème a été résolu en effaçant les exceptions avant d’effectuer un autre appel JNI.

* (Zendesk #4487) - Suivi du canal linéaire de contenu

Le problème a été résolu en réinitialisant le suivi de pulsation vidéo au cours d’une session de lecture de flux linéaire.

* (Zendesk #17919) - Android : la recherche de contenu entraîne une erreur de pulsation.

Le problème était de résoudre la pulsation dans un état d’erreur lorsqu’il y a une recherche dans un chapitre.

* (Zendesk #18053) - Application utilisant le TVSDK se bloque sur Marshmallow

Le TVSDK se bloquait sur Android™ M OS lorsque la bibliothèque TVSDK utilisait du code néon qui fait YUV. `->` Conversion des couleurs du RGB. Ce problème a été résolu en mettant à jour les fonctions à l’origine de ce problème à l’aide d’une version non néon de `code`.

* (Zendesk #18072) - Android M - Panne d’application

Ce plantage survient lors de l’appel de `MediaCodecList` et `MediaCodecInfo` API lors de la vérification de la prise en charge du profil et du niveau. Adobe recherche la prise en charge de Google pour obtenir des informations supplémentaires. Ce problème a été résolu en fournissant une solution temporaire en chargeant toutes les informations de codec à l’avance afin d’éviter d’appeler ces API uniquement lorsque des informations de codec sont nécessaires.

* (Zendesk #18074) - Les sous-titres arabes ne fonctionnent pas sur Nexus avec Android™ 6.0

Ce problème a été résolu en prenant en charge la carte des polices Android™ CTS.

**Version 1.4.15** (1.4.15.512) pour iOS 6.0+

**Remarque**: Le module Nielsen a été supprimé de la version TVSDK, mais le SDK sera bientôt mis à jour avec un nouveau module d’intégration Nielsen.

* (ZD #2228) - Erreur retournée lors de la récupération du manifeste non disponible dans `MediaPlayerNotification`

Ajout de métadonnées pour exposer le contenu lors de la notification `M3U8_PARSER_ERROR` survient.

* (ZD #4437) - Blocages dans le SDK Adobe Primetime

Correction d’un blocage signalé lors de la préparation des sous-titres/fichiers audio alternatifs.

* (ZD #4487) - Suivi du canal linéaire de contenu

Réinitialisation autorisée de l’outil de suivi de pulsation vidéo au cours d’une session de lecture de flux linéaire.

**Version 1.4.14** (1.4.14.498) pour iOS 6.0+

* (ZD #17260) - Blocage `playlistManagerForURL`

Correction d’un blocage intermittent en raison de problèmes de simultanéité.

**Version 1.4.13** (iOS 6.0+)

* (ZD #3304) - VAST 3.0 `[ERRORCODE]` macro non renseignée

   * Le code d’erreur 400 est révélé si la publicité intégrée comporte un contenu créatif incorrect.
   * `[ERRORCODE]` est codée au format URL.

* (ZD #3865) Intégration Heartbeat avec les annonces IMA

Correction d’un bogue en raison duquel la durée de la vidéo était incorrectement signalée.

* Mise à jour du lecteur de démonstration TVSDK pour la prise en charge d’iOS 9

Pour prendre correctement en charge iOS 9, vous devez configurer les exceptions de la sécurité du transport des applications. Pour la démonstration, ATS est complètement désactivé.

**Version 1.4.12** (1.4.12.464) pour iOS 6.0+

* (ZD #4521) CRS Test côté client et SSAI

Correction d’un MD5 inversé dans l’URL 3P.

**Version 1.4.12** (1.4.12.463) pour iOS 6.0+

* (ZD #2751) CSAI et CRS / Amélioration : Gérez les éléments dynamiques dans certaines URL de fichier multimédia.

Mise à jour de Creative Repackaging Service pour gérer correctement les annonces avec des URL de création dynamiques.

* (ZD #3654) Fuite de mémoire dans la version PSDK après la version 1.3.4.166

Correction d’une fuite de mémoire dans `drmFramework` avec lecture normale sur les appareils iOS 8.2

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

Mise à jour `PTPlaybackInformation` pour afficher le débit indiqué mis à jour. Mise à jour `BITRATE_CHANGE` pour être plus fiable et précis par rapport aux débits signalés du M3U8.

* (ZD #3324) Problème de reporting des publicités Primetime lorsqu’aucun média publicitaire n’est dans VMAP

Prise en charge des URL de suivi de coupure publicitaire vide Ping. TVSDK vérifie désormais les pings de début et de fin de coupure publicitaire pour les coupures publicitaires vides.

**Version 1.4.8** (1.4.8.402)

* (ZD #3158) Blocages d’IOS 7 lors des relectures d’événements complets

**Version 1.4.7** (1.4.7.382)

* (ZD #2197) Suivi des erreurs de publicité. Ajout d’une notification pour le chargement du manifeste de la ressource.
* (ZD #2894) Player Effectue quatre demandes de manifeste de niveau supérieur pendant la lecture.
* (ZD #2992) [!DNL Auditude] Signaler des durées et des identifiants bizarres.

**Version 1.4.6**(1.4.6.325)

* (ZD #2197) Suivi des erreurs de publicité. Ajout d’une notification pour l’échec du chargement du manifeste

**Version 1.4.5** (1.4.5.283)

* (ZD #2141) Mise en oeuvre d’Analytics pour [!DNL TreeHouse] app, ajouté `AdobeAnalyticsPlugin.a` pour créer un package .
* Mise à jour de la bibliothèque Video Heartbeats vers la version 1.4.1.2
* (PTPALY-4226) (lié à ZD #2423) L’exécution de la réinitialisation DRM peut entraîner la suppression des données du document d’application.

**Version 1.4.4** (1.4.4.242)

* Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.4.1.

* (ZD #2435) Documentation du SDK TV sur les mises à jour des besoins d’analyse

**Version 1.4.2** (1.4.2.210 : iOS 6.0+)

* (ZD #1129) `_player.currentItem.audioOptions` return empty
* (ZD #2109) Primetime PSDK 1.4.1.125 ne fonctionne pas avec Xcode 5.1.1
* (ZD #2137) Blocage dans PSDK sur iOS lorsque les métadonnées DRM ne peuvent pas être chargées

**Version 1.4.1**(1.4.1.125)

* (ZD #1107) [!DNL CocoaLumberjack] doublons de symboles
* (ZD #1644) Modification de l’agent utilisateur iOS pour le ciblage et la création de rapports
* (ZD #1850) Fichiers Cocoa Lumberjack inclus dans le SDK iOS
* (ZD#1908) Les balises personnalisées sont ignorées par le PSDK s’il en existe plus de 1

**Version 1.4.0** (1.4.0.32)

* Zendesk #1024 - Fonctionnalité de suppression de la publicité du flux via le manifeste

## Certification et prise en charge des périphériques {#device-certification-and-support}

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
* Prise en charge de DRM pour forcer HTTPS en ajoutant  `forceHTTPS`  et `isForcingHTTPS` API.
* Mise à jour des bibliothèques VHL vers la version 1.5.8, Adobe des bibliothèques mobiles vers la version 4.8.4 et de la bibliothèque d’utilitaire de journalisation vers la cible de déploiement de la version 7.0.

**Version 1.4.19**

Cette version de TVSDK a été certifiée avec le support FairPlay pour iOS et tvOS.

**Version 1.4.17**

* tvOS

   Cette version de TVSDK inclut la prise en charge de tvOS et a été certifiée pour les flux HLS non chiffrés.

   **Remarque**: Gardez à l’esprit les instructions de compilation suivantes :

   * La prise en charge de TVSDK tvOs est limitée aux diffusions cryptées DRM non Adobes. Vous devez supprimer la référence à `drmNativeInterface.framework` dans les paramètres de génération de tvOS. Les diffusions cryptées AES sont toujours prises en charge.
   * Apple exige que toutes les applications Apple TV soient activées pour le code binaire. Vous devez donc activer cet indicateur dans les paramètres de votre projet.

## Problèmes connus et limites {#known-issues-and-limitations}

* En raison de l’obsolescence de la classe iOS UIWebView, dans iOS TVSDK 3.6 et versions ultérieures :
   * Les publicités VPAID ne sont pas lues comme prévu dans iPad 13.
   * Les publicités d’accompagnement ne sont pas lues comme prévu.

* Dans iOS TVSDK, toutes les publicités sont regroupées dans le manifeste de contenu. Les comportements publicitaires sont implémentés en effectuant des recherches en fonction de la durée du contenu et des segments de publicité. Ainsi, si les durées de segment ne sont pas exactes, la recherche peut ne pas toujours se terminer à l’image exacte du début ou de la fin de la coupure publicitaire. Même si les durées correspondent au cadre, la plate-forme elle-même impose une certaine tolérance à la recherche et quelques images ou publicités ou contenus peuvent être affichés. Il s’agit d’une limitation de la plateforme et du fonctionnement de l’insertion de publicités avec TVSDK sur iOS.
* Dans ce cas, la décision d’ignorer se produit sur l’événement de recherche. Cependant, comme les durées du segment publicitaire dans le manifeste ne représentent pas exactement la durée réelle de la publicité, la recherche n’est pas précise. Par conséquent, vous voyez quelques images d’annonce lorsque les stratégies de publicité sont appliquées.
* Il se peut que la vidéo de rotation de licence ne soit pas lue sur iOS 11 et qu’elle soit correctement lue sur iOS 9.x et iOS 10.x.
* Dans la prise en charge de VPAID 2.0, si la lecture est principale sur AirPlay, les publicités VPAID sont ignorées.
* Le `drmNativeInterface.framework` ne se lie pas correctement lorsque la cible minimale est définie sur iOS7 (ou version ultérieure).
Solution : Spécifiez explicitement la variable `libstdc++.6.dylib` comme suit : Accédez à **[!UICONTROL Target]** > **[!UICONTROL Build Phases]** > **[!UICONTROL Link Binary With Libraries]** et ajouter `libstdc++.6.dylib`.
* La publicité post-roll n’est pas insérée pour l’API de remplacement.
* La recherche dans une coupure publicitaire (sans en sortir) génère une notification de début et de coupure publicitaire en double.
* Paramètre `currentTimeUpdateInterval` n’a aucun effet.
Remarque : Dans certaines versions d’iOS, le système d’exploitation ne charge pas les ressources dans la variable `PSDKLibrary.framework` automatiquement. Il est important de copier manuellement la variable `PSDKResources.bundle` aux ressources du lot de l’application : Accédez à **Phases de création** et copiez les ressources du lot.
* L’application de référence ne peut pas être créée à l’aide de Xcode 8 ou de versions antérieures. iOS TVSDK version 1.4.41 et ultérieure, compilez Xcode 9.
* Les publicités VPAID n&#39;honorent pas `delayAdLoadingTolerance` .
* 24077 - Pour certains contenus HLS avec sous-titres, le lecteur se bloque sur _Arrêter_ ou _Réinitialiser_ .
* Les notifications d’erreur détaillées ne sont pas disponibles lorsque la résolution de publicités juste à temps est activée.
* Les notifications d’erreur sont consignées selon l’heure de résolution de la publicité et non selon la séquence publicitaire.
* La prise en charge de HEVC présente les limites suivantes dans cette version
   * DRM non pris en charge
   * La prise en charge du CC (CEA 608/708) n’est pas disponible, car elle n’est pas prise en charge dans le CMAF.
   * La prise en charge de 4K n’est pas encore présente.
   * La prise en charge des balises ID3 n’est pas disponible, car elle n’est pas prise en charge dans CMAF.
   * Diffusions en direct non muxées en continu HVC non vérifiées.
   * La prise en charge des publicités HEVC n’est pas vérifiée.
* Si JIT est activé et que la tolérance est définie sur 10 secondes, aucun appel VAST n’est affiché pour la première coupure publicitaire au milieu en cas de publicités de redirection VMAP > VAST.
* Pour que le délai d’expiration de la résolution de la publicité fonctionne correctement, chaque fois que la liste de lecture est mise à jour pendant la lecture de la diffusion en continu active, le lecteur attend une liste de lecture groupée dans les 20 secondes. S’il ne reçoit pas de liste de lecture groupée au cours de cet intervalle, une erreur interne est générée et le lecteur s’arrête.

## Ressources utiles {#helpful-resources}

* [Guide du programmeur iOS : TVSDK 3.4](https://experienceleague.adobe.com/docs/primetime/programming/tvsdk-3x-ios-prog/introduction/ios-3x-overview.html?lang=en)
* [Référence de l’API TVSDK iOS 3.4](https://help.adobe.com/en_US/primetime/api/psdk/appledoc_v34/index.html)
* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://experienceleague.adobe.com/docs/primetime.html) page.
