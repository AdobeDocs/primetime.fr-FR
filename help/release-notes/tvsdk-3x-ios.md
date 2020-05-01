---
title: Notes de mise à jour de TVSDK 3.11 pour iOS
description: Les Notes de mise à jour de TVSDK 3.11 pour iOS décrivent les nouveautés ou les modifications, les problèmes résolus et connus et les problèmes de périphérique dans TVSDK iOS 3.11.
translation-type: tm+mt
source-git-commit: ac75f63f98060e1937570476362bb5d4458d1f85

---


# Notes de mise à jour de TVSDK 3.11 pour iOS {#tvsdk-for-ios-release-notes}

Les Notes de mise à jour de TVSDK 3.11 pour iOS décrivent les nouveautés ou les modifications, les problèmes résolus et connus et les problèmes de périphérique dans TVSDK iOS 3.11.

## Configuration système et logiciel requise {#system-software-requirements}

Avant de télécharger iOS 3.11, assurez-vous que les versions de votre matériel, de votre système d’exploitation et de vos applications répondent aux exigences suivantes :

Système d’exploitation : iOS 8.0 ou version ultérieure.

## iOS TVSDK 3.11

Correctifs fournis pour les problèmes des clients qui provoquent le blocage de l’application `isFallbackOnInvalidCreativeEnabled` et `customParams` de la méthode.

Pour les correctifs de la version actuelle, reportez-vous à la section Problèmes [client résolus](#resolved-issues) et pour les limitations, reportez-vous à la section Problèmes [connus et limitations](#known-issues-and-limitations) .

### Nouvelles fonctionnalités et correctifs des versions précédentes {#whats-new-previous}

**iOS TVSDK 3.10**

* Correction d’un problème en raison duquel le lecteur TVSDK ne déclenchait pas `PTMediaPlayerStatusError` de notification lorsque le réseau n’était pas disponible.

**iOS TVSDK 3.9**

* Correction d’un problème en raison duquel la lecture des sous-titres VTT échouait et provoquait le blocage de l’application.

* iOS TVSDK 3.9 incluait le certificat de transport d’individualisation mis à jour.

**Correctif logiciel iOS TVSDK 3.8.0.83**

Le correctif logiciel avait mis à jour le certificat de transport d&#39;individualisation.

**iOS TVSDK 3.8**

Conformité iOS 13 et prise en charge de l’obsolescence de l’API UIWebView iOS 13.

**iOS TVSDK 3.7**

Correctif d’un scénario dans lequel la lecture s’arrêtait lorsqu’un grand nombre de demandes de résolution d’annonce étaient effectuées simultanément.

**iOS TVSDK 3.6**

**Correctifs dans la propriété vasteXML de la classe`PTNetworkAdInfo`**

La propriété vasteXML n’était pas correctement définie et renvoyait une valeur nulle.

**iOS TVSDK 3.5**

**Activation de l’audio en arrière-plan**

*Configurez votre application pour qu’elle continue à lire du son lorsqu’elle passe en arrière-plan.*

Pour activer cette fonctionnalité, nous devons définir la nouvelle API `audioPlaybackInBackground` ajoutée à la classe PTMediaPlayer. Cette API étant activée, votre application est prête à lire le son en arrière-plan.

**iOS TVSDK 3.4.0.19 (Correctif)**

Cette version comprend un correctif pour les blocages d’application survenant dans un scénario de basculement publicitaire.

**iOS TVSDK 3.4**

**Expiration de la résolution de la publicité**

* Avec TVSDK 3.4, les utilisateurs peuvent désormais définir la valeur du délai d’expiration pour la résolution globale de la publicité et les téléchargements de manifeste. Si, dans un délai donné, certaines publicités ne sont pas résolues, TVSDK lit les publicités restantes.

* PTAdMetadata : L’API adRequestTimeout a été abandonnée et sera supprimée. La valeur par défaut a été définie à 35 secondes.

* Deux nouvelles API alternatives ont été introduites dans la classe PTAdMetadataClass : adResolutionTimeout - délai d’expiration pour les appels de résolution publicitaire globaux adManifestTimeout - délai d’expiration pour les téléchargements de manifeste publicitaire.

**Optimisation des recettes**

Activation de TVSDK pour identifier les zones à problème liées aux workflows d’insertion publicitaire à signaler à un point de terminaison de choix d’analyse.

**Version 3.3**

TVSDK 3.3 est désormais compatible avec le SDK iOS 11. Toutes les API obsolètes ont été remplacées par des alternatives appropriées.

**Version 3.2**

**Prise en charge supplémentaire de la journalisation (phase 2)**

Ajout de la prise en charge des notifications d’erreur en cas de :

* La version HLS de la publicité utilise un niveau supérieur à celui du contenu.

* La variante audio uniquement est exclue.

* Échec de la demande VAST/VMAP.

**Version 3.1**

* **Prise en charge** de la journalisation supplémentaire Ajout de la prise en charge des notifications descriptives en cas d’échec de la lecture de la publicité.

* **Ajout de la prise en charge** des flux CMAF chiffrés Fairplay Les flux CMAF chiffrés Fairplay avec lecture de codec AVC sont maintenant pris en charge.

**Version 3.0.1**

Aucune nouvelle fonctionnalité ou amélioration dans cette version.

**Version 3.0**

* TVSDK 3.0 prend en charge les flux HEVC.

* Juste à temps : résolution des publicités plus proches des marqueurs publicitaires.

Ajout `enableDelayAdLoading` d’une propriété de type booléen dans l’interface au niveau de l’application pour activer JIT. Si `enableDelayAdLoading` la valeur NO est affectée, elle est affectée `setadMetadata.delayAdLoading`de la valeur True (propriété de l’interface PTAdMetadata).

Lorsque cette propriété est activée, TVSDK résout chaque coupure publicitaire avant sa position en fonction de la valeur de tolérance définie. Par défaut, `delayAdTolerance` est défini sur 5 secondes.

**Version 1.4.45**

Pour se conformer à Xcode10, TVSDK est passé de &quot;`libstdc++`&quot; à &quot;`libc++`&quot; et, par conséquent, la version minimale prise en charge est iOS 7. Auparavant, il s’agissait d’iOS 6.

**Version 1.4.44**

Aucune nouvelle fonctionnalité ou amélioration dans cette version.

**Version 1.4.43**

* Expérience TV de possibilité de se joindre au milieu d’une publicité sans déclencher de suivi partiel de la publicité.\
   Exemple : L’utilisateur se joint au milieu (à 40 secondes) d’une coupure publicitaire de 90 secondes composée de trois publicités de 30 secondes. Ceci est 10 secondes après la seconde publicité pendant la coupure.

   * La seconde publicité est lue pour la durée restante (20 s), suivie de la troisième publicité.
   * Les suivis publicitaires pour la publicité partielle lue (deuxième publicité) ne sont pas déclenchés. Les suivis pour la troisième publicité seulement sont déclenchés.

* Ajout de la propriété enableVodPreroll de type booléen dans l’interface PTAdMetadata. La propriété peut être utilisée pour activer le pré-roll sur un flux VoD. Si enableVodPreroll a la valeur NO, PSDK ne lit pas le pré-roll. Cela n&#39;a cependant aucun impact sur les midrolls. La valeur par défaut de enableVodPreroll est YES.
* L’API closeCaptionDisplayEnabled de l’interface PTMediaPlayer est marquée comme obsolète à partir de la version 1.4.43 d’iOS. Pour déterminer si des sous-titres sont disponibles pour un élément PTMediaPlayerItem donné, examinez la propriété subtitlesOptions de PTMediaPlayerMediaItem.

**Version 1.4.42**

Aucune nouvelle fonctionnalité n’est ajoutée dans cette version. Pour une liste de problèmes résolus, voir Problèmes [](#resolved-issues)résolus.

**Version 1.4.41**

Modifications de l&#39;API :

* **isSecure**: Une nouvelle API est introduite dans isSecure pour empêcher le lecteur d’enregistrer et de lancer une erreur. La valeur par défaut est true.

* **allowExternalRecording**: Une nouvelle API est introduite pour permettre la mise en miroir des diffusions pour un contenu sécurisé. La mise en miroir de l&#39;espace aérien est traitée comme un enregistrement. Par conséquent, `allowExternalRecording` la valeur doit être définie sur `True`, pour permettre la mise en miroir de l&#39;espace ou pour `False` arrêter la mise en miroir de l&#39;espace pour un contenu sécurisé. Par défaut, `value` est true.

**Version 1.4.40**

Aucune nouvelle fonctionnalité.

**Version 1.4.39**

* iOS TVSDK est certifié avec VHL 2.0.1 et avec VHL 2.0.1 avec Nielsen.

* Le SDK iOS TVSDK est mis à jour afin d’envoyer des requêtes CRS du nouvel hôte Akamai `primetime-a.akamaihd.net`.

* La nouvelle configuration du nom d’hôte fournit une diffusion de ressources CRS via HTTP et HTTPS (SSL) à plus grande échelle.

**Version 1.4.36**

Intégrez et certifiez VHL 2.0 dans le SDK iOS TVSDK : Réduisez les obstacles à l’ `VideoHeartbeatsLibrary` implémentation en réduisant la complexité des API.

**Version 1.4.34**

**Informations sur les publicités réseau**

Les API TVSDK fournissent désormais des informations supplémentaires sur les réponses VAST tierces. L’identifiant de publicité, le système d’annonces et les extensions d’annonce VAST sont fournis dans la `PTNetworkAdInfo` classe accessible par le biais `networkAdInfo` de la propriété sur une ressource d’annonce. Ces informations peuvent être utilisées pour l’intégration à d’autres plates-formes d’analyses des publicités, telles que **Moat Analytics**.

**Version 1.4.31**

* **Mesures** de facturation Afin d’accommoder les clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.

   Chaque fois que TVSDK génère un événement de début de diffusion en continu, le lecteur début à envoyer régulièrement des messages HTTP au système de facturation d’Adobe. La période, appelée durée facturable, peut être différente pour le contenu VOD standard, le contenu pro VOD (publicités mid-roll activées) et le contenu en direct. La durée par défaut de chaque type de contenu est de 30 minutes, mais votre contrat avec Adobe détermine les valeurs réelles.

* **Prise en charge multi-CDN pour CRS Ads** TVSDK prend désormais en charge Multi-CDN pour les annonces CRS. En fournissant des détails FTP pour les annonces CRS, vous pouvez spécifier des emplacements CDN autres que le CDN par défaut détenu par Adobe, tel qu’Akamai.

**Version 1.4.29**

Dans la `PTSDKConfig` classe, l&#39;API forceHTTPS a été ajoutée.

La `PTSDKConfig` classe fournit des méthodes pour appliquer SSL sur les requêtes envoyées aux serveurs Adobe Primetime de prise de décision publicitaire, DRM et Video Analytics. Pour plus d&#39;informations, consultez les méthodes `forceHTTPS` et `isForcingHTTPS` sur cette classe. Si un manifeste est chargé via HTTPS, TVSDK conserve l’utilisation du contenu HTTPS et respecte cette utilisation lors du chargement d’URL relatives à partir de ce manifeste.

>[!NOTE] Les requêtes envoyées à des domaines tiers tels que les pixels de suivi des publicités, les URL de contenu et de publicité et les requêtes similaires ne sont pas modifiées et il incombe aux fournisseurs de contenu et aux serveurs d’annonces de fournir les URL prises en charge par HTTPS.

**Version 1.4.18**

Primetime iOS TVSDK prend désormais en charge les éléments créatifs JavaScript VPAID 2.0 pour permettre une expérience publicitaire interactive riche en flux continu. Pour plus d’informations sur VPAID 2.0, voir Prise en charge des publicités VPAID.

**Version 1.4.17**

* tvOS

   TVSDK prend en charge les applications natives tvOS.
* Les types de contenu suivants peuvent être lus :

   * VOD
   * Live
   * AES-128
   * Autre audio et sous-titres
   * FER

* Les types de publicités suivants peuvent être affichés :

   * Basic
   * VAST2
   * VAST3
   * VMA

* Actuellement, les fonctionnalités suivantes ne sont pas prises en charge :

   * Gestion des droits numériques (DRM)
   * Bannières publicitaires
   * TVML (TV Markup Language)

**Version 1.4.13**

>[!NOTE] Le module Nielsen a été supprimé de la version TVSDK, TVSDK sera mis à jour prochainement avec un nouveau module d’intégration Nielsen.

**Abandon de publicité, chaînement de la marguerite dans la logique de sélection des publicités (Zendesk #3103)**

Pour les publicités VAST (créatives) avec la règle de secours activée, TVSDK traite une publicité avec un type MIME non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours. Pour plus d’informations, reportez-vous à la section Baisse de publicité pour les annonces VAST et VMAP.

**Version 1.4.9**

**Signalisation par coupure de courant avec remplacement de contenu alternatif**

Dans le cadre de la mise à jour de TVSDK 1.4, nous soutenons désormais le recours à des pannes régionales pour éviter les émissions linéaires. TVSDK peut maintenant traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d&#39;arrêt même lorsque la programmation alternative est présentée à la programmation originale.

**Version 1.4.8**

**Mise à jour de la bibliothèque Video Heartbeats Library (VHL) vers la version 1.5**

* Capacité d’envoyer des métadonnées avec un début vidéo et/ou un début vidéo/publicitaire/chapitre en tant que données contextuelles.

* Moins de trafic réseau : les pulsations sont moins nombreuses en moyenne et de taille plus petite.

**Version 1.4.7**

* **Prise en charge de l’individualisation sur site**

Prise en charge des installations sur site d’Adobe Individualization Server pour personnaliser la demande d’individualisation du client afin d’accéder à un autre point de terminaison.

* **Protection de la sortie basée sur la résolution**

Les stratégies DRM peuvent désormais spécifier la résolution maximale autorisée, en fonction des fonctionnalités Output Protection du périphérique. Par exemple, &quot;Si HDCP est disponible, autorisez la lecture d&#39;un contenu jusqu&#39;à une résolution de 1080p, et si HDCP n&#39;est pas disponible, autorisez la lecture d&#39;un contenu jusqu&#39;à une résolution de 480p&quot;.

**Version 1.4.4**

* **Mise à jour de la bibliothèque Video Heartbeats Library (VHL) vers la version 1.4.1.1**

   * Ajout de la possibilité de regrouper différents cas d’utilisation des analyses, provenant d’autres kits SDK ou lecteurs, avec Adobe Analytics Video Essentials.
   * Le suivi des publicités a été optimisé en supprimant les `trackAdBreakStart` méthodes et `trackAdBreakComplete` les. La coupure publicitaire est déduite des appels `trackAdStart` et de la `trackAdComplete` méthode.
   * La `playhead` propriété n’est plus nécessaire lors du suivi des publicités.
   * Ajout de la prise en charge de l’identifiant de Visiteur Marketing Cloud.

* **Intégration du SDK Nielsen**

TVSDK prend désormais en charge l’envoi de balises mTVR et MDPR ID3 au SDK Nielsen sans intégration personnalisée. Pour commencer, téléchargez le SDK d’application iOS 3.1.2.19 Nielsen et suivez les instructions figurant ici dans le Guide des programmeurs iOS.

**Version 1.4.0**

* **Signalisation par coupure de courant avec remplacement de contenu alternatif**

Dans le cadre de la mise à jour de TVSDK 1.4, TVSDK prend également en charge le recours à des pannes régionales et le retour de celles-ci contre du contenu linéaire. TVSDK peut maintenant traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d&#39;arrêt même lorsque la programmation alternative est présentée à la programmation originale.

* **Supprimer/Remplacer les publicités C3**

Désormais, aucun travail de préparation supplémentaire n’est nécessaire pour insérer dynamiquement de nouvelles publicités dans des ressources vidéo à la demande (VOD) qui sortent de la fenêtre C3. TVSDK fournit désormais une API permettant de supprimer des plages de contenu personnalisées et d’insérer dynamiquement de nouvelles publicités. Cette nouvelle fonctionnalité puissante est également utile dans les cas où du contenu en direct/linéaire est diffusé pendant la diffusion et est immédiatement retiré pour être utilisé comme contenu à la demande sans le temps nécessaire pour &quot;nettoyer&quot; la ressource.

## Problèmes résolus {#resolved-issues}

Lorsque la résolution est associée à un problème signalé, une référence Zendesk s’affiche, par exemple ZD#xxxxx.

<!-- 

Comment Type: draft

<note type="note"> 
 <p>All TVSDK customers who use CRS are strongly encouraged to upgrade to TVSDK 1.4.39 or latest on iOS and Android. This upgrade is a drop-in replacement to the existing app implementation. After the upgrade, check for the CRS creative URL requests in a proxy tool (for example, Charles) to verify that the version in the path reflects version 3.1. For example:</p> 
 <p><span class="code">https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8</span></p> 
</note>

 -->

<!--
Comment Type: draft

<note type="note"> 
 <p>TVSDK versions earlier than version 1.4.28 sometimes exhibit a long delay in the startup time when ad-enabled content is played on devices that are running on iOS 10. To resolve this issue, upgrade to version 1.4.28 or later. Version 1.4.28 was released on August 31, 2016, and iOS 10 was released on September 13, 2016.</p> 
</note>
 -->

**iOS TVSDK 3.11**

* (ZD#40998) - L’application `isFallbackOnInvalidCreativeEnabled` se bloque.

* (ZD#41289) - `NSInvalidArgumentException` est observé avec la méthode `customParams` conduisant au blocage de l&#39;application.

### Problèmes résolus dans les versions précédentes {#resolved-issues-previous}

**iOS TVSDK 3.10**

(ZD#40943) - Le lecteur TVSDK ne déclenche pas la notification PTMediaPlayerStatusError lorsque le réseau n’est pas disponible.

**iOS TVSDK 3.9**

(ZD#40272) - Le SDK iOS TVSDK ne parvient pas à lire les sous-titres VTT avec l’erreur 101001 et entraîne le gel de l’application.

**iOS TVSDK 3.8**

* (ZD#40087) - iOS se bloque avec une erreur du lecteur pour le contenu VOD expiré.

* (ZD#40083) - Les publicités preroll ne sont pas lues pour la diffusion en direct avec `OpportunityGenerator` et le lecteur affiche une erreur.

* (ZD#39828) : `CurrentItem` l’annotation de nullability est manquante pour la propriété, ce qui provoque un blocage du lecteur lorsque l’état du lecteur contenu dans la notification est `PTMediaPlayerStatusStopped`inactif.

**iOS TVSDK 3.7**

(ZD#38961) - La lecture du contenu échoue dans la fenêtre Image dans l’image (PiP) une fois qu’un contenu a terminé la lecture, lorsque plusieurs contenus sont configurés pour être lus dans le PiP.

**iOS TVSDK 3.6**

Aucun nouveau problème dans cette version.

**iOS TVSDK 3.5**

Aucun nouveau problème dans cette version.

**Version 3.3**

(ZD#37820) - Ajout d’une liste blanche pour l’en-tête personnalisé HS-Id, HS-SSAI-TAG.

**Version 3.2**

* **Billet #36588** - Le blocage du lecteur est observé lorsque la méthode STOP de MediaPlayer est appelée.
Correction d&#39;un blocage intermittent observé lorsque la méthode STOP est appelée pour quelques flux avec sous-titres.

* **Billet #37080** - Demandes de Duplicata affichées pour les appels Manifest.
Correction des demandes de duplicata effectuées pour les URL de manifeste pendant la lecture. TVSDK effectue désormais un appel par manifeste.

* **Billet #37** - Échec de la règle de normalisation CRS avec le type de correspondance eqCorrection d’un cas où le lecteur se bloquait lorsqu’il se trouvait avec la dernière règle de normalisation définie pour les noms d’hôtes avec un type de correspondance eq.

**Version 3.1**

**Billet #36313** - Résultats imprévisibles intermittents pendant les pauses publicitaires linéairesCorrection de la lecture intermittente pendant les pauses publicitaires linéaires dans le flux continu.

**Version 3.0.1**

**Billet36948** - CRS - Ordre de sélection des ressources incohérent sur iOS 12L’actif sélectionné pour CRS n’est pas toujours la variante de qualité la plus élevée renvoyée dans une réponse VAST ou VMAP.

**Version 3.0**

* **Billet35311** - L&#39;état du lecteur n&#39;est pas PAUSÉ lors d&#39;une interruption d&#39;appel téléphoniqueAjout d&#39;un gestionnaire d&#39;interruption pour empêcher l&#39;interruption du lecteur. En cas d’interruption, l’état du lecteur devient PAUSED et la lecture reprend en cliquant sur le bouton Lecture.

* **Ticket36685** - Ressources en direct - Incompatibilité de temps avec la progression du temps du lecteur et temps du marqueur SCTELe temps correct est calculé pour les marqueurs SCTE qui sont en avance sur le point de production.

* **Ticket36492** - `currentTime` et `localTime` ne sont pas mis à jour lors de la recherche d&#39;une nouvelle position au cours de l&#39;heure actuelle de statusPlayer en pause peut désormais être réglée sur zéro au cas où le lecteur serait en pause ; auparavant, l’heure actuelle était définie sur zéro uniquement à l’état de lecture.

**Version 1.4.45**

* **Billet36294** - Le SDK iOS ne fonctionne pas avec Xcode 10 Correction des problèmes de compilation avec TVSDK sur XCode 10. En raison de la configuration requise pour XCode 10, les applications créées à partir de TVSDK pour iOS 1.4.45 nécessitent une cible de déploiement minimale en tant qu’iOS 7.0.

* **Billet36321** - Discrépité observée dans la plage de recherche entre `PTMediaPlayer` et `AVPlayer` l’instance dans l’état &quot;Lecture&quot;.

* **Billet36493** - `libstdc++` prise en charge sur iOS 12 Correction des problèmes de compilation avec TVSDK sur iOS 12. Les applications créées à partir de TVSDK pour iOS 1.4.45 nécessitent une cible de déploiement minimale avec iOS 7.0.

**Version 1.4.44**

* **Ticket34683** - Le Temps De Progression De La Lecture De La Publicité Est Négatif

Vérifications supplémentaires effectuées pour gérer le cas en cas de discordance entre la durée signalée par le serveur d’annonces et le contenu réel de la publicité.

* **Ticket34801** - currentTime et localTime n&#39;étaient pas mis à jour lors de la recherche d&#39;une nouvelle position pendant l&#39;heure en pause statusPlayer peut maintenant être défini sur zéro si le lecteur est en pause ; auparavant, l’heure actuelle était définie sur zéro uniquement à l’état de lecture.

* **Ticket35037** - Les arrêts de lecture avec une URL incorrecte lors du retour d’une insertion publicitaire basée sur le signal.
Correctif fourni pour le numéro fermé 34385 de la version 1.4.42. Ajout du code de contrôle et de gestion des exceptions isAnncelled pour rendre la file d&#39;attente des opérations plus robuste.

**Version 1.4.43**

* (ZD#32990) - iOS : Lecture du contenu au lieu de publicités sur certains indices. `selectedMediaOptionInMediaSelectionGroup` L’API qui faisait partie de l’interface AVPlayerItem a maintenant été déplacée sous AVMediaSelection dans iOS 11. Le problème a été résolu à l’aide de cette nouvelle API.

* (ZD#33683) TVSDK supprimé == suffixe des chaînes de métadonnées. Le problème est corrigé dans la logique d’analyse.

* (ZD#33905) - iOS TVSDK appelle les fichiers de manifeste avec deux agents d’utilisateur. Le problème de l&#39;agent utilisateur a été corrigé dans le premier appel m3u8 (nouveau cas d&#39;installation). Les M3u8 ont les mêmes agents utilisateur pour tous les appels maintenant.

* (ZD#34293) - Les pré-rouleaux insérés dans les flux LINEAR ne se lancent pas correctement sur iOS11. Le problème est corrigé pour les publicités preroll.

* (ZD#34684) - Lorsque la stratégie de saut d’annonce est appliquée, les images de publicité preroll s’affichent pendant quelques secondes. Une nouvelle API, enableVodPreroll, a été introduite pour désactiver la lecture preroll dans la lecture de vod. La valeur par défaut de cette API est &quot;Yes&quot;. L’API permet d’ignorer l’assemblage de contenu publicitaire dans le contenu principal.

* (ZD#34765) - Après avoir appelé stop(), peu de segments de flux de transport sont toujours téléchargés. Amélioration de l’API Stop() pour éviter le téléchargement des segments supplémentaires.

* (ZD#34865) - Les publicités preroll pour diffusion en continu sont tronquées sur iOS. En ce qui concerne iOS11 et l’ajout d’une vérification supplémentaire pour confirmer si le flux est pré-roll ou de contenu principal, résout ce problème.

* (ZD#35093) - Correction d’un scénario de basculement selon lequel, si la variante principale du flux échoue au démarrage (renvoie 404), la lecture ne passe pas au flux de sauvegarde.

**1.4.42 (1.4.42.118)**

* (ZD#34385) - Les arrêts de lecture avec une URL incorrecte lors du retour d’une insertion publicitaire basée sur un signal.

   Augmentez le nombre maximal de répétitions pour `CustomAVAssetLoaderOperations`afin que les lectures du manifeste puissent continuer à s&#39;exécuter.

* (ZD#34373) - Les utilisateurs finaux ne sont pas en mesure de diffuser sur des périphériques connectés au HDMI, lorsque l’enregistrement du flux est interdit.

* (ZD#32678) - TVSDK ne collecte pas les ID publicitaires corrects sur iOS.

   L’identifiant de publicité de la création publicitaire finale est maintenant récupéré dans les pings VHL en cas de redirections VAST/VMAP.

* (ZD#33904) - TVSDK n’est pas enregistré pour les notifications et `AVAudioSessionMediaServicesWereLostNotification` `AVAudioSessionMediaServicesWereResetNotification`notifications AVFFoundation.

   `PTMediaServicesWereLostNotification` et `PTMediaServicesWereResetNotification` peuvent désormais être enregistrés dans l’application du lecteur afin d’obtenir les notifications lorsque les services de médias sont réinitialisés ou perdus.

* (ZD#33815) - Les clients ne peuvent pas mettre à jour leurs règles CRS de hiérarchisation et de normalisation sans avoir à mettre à jour leur application.

   Ajout des `getCRSRulesJsonURL` API et `setCRSRulesJsonURL` des API au SDK iOS.

**Version 1.4.41 (1.4.41.76)**

* (ZD #34464) - Création de problèmes avec l’application de référence avec TVSDK version 1.4.41

   Depuis cette version, Xcode 9 est requis pour compiler TVSDK pour iOS.
* (ZD n° 29456) - Débuts de jeu d’images en pause

   Correction du problème de mise en pause qui se produisait lorsque la vidéo s’interrompait lors de la saisie de la lecture.
* (ZD #30371) - La durée du début d’AdBreak change lorsque nous insérons plus de 2 publicités dans un flux linéaire.

   Correction de l’erreur lors de la tentative de lecture de contenu sur Apple TV, qui empêchait la lecture complète
* (ZD #32146) - Aucun contenu HLS Live n’ `PTMediaPlayerStatusError` est reçu pour le blocage de la version bêta de développement iOS 11

   Aucun contenu HLS Live et VOD n&#39; `PTMediaPlayerStatusError` est reçu sur le blocage à l&#39;aide de Charles (Abandonner la connexion et 403)
* (ZD #29242) - Echec de la lecture vidéo de la lecture en différé avec l’activation des publicités

   Lorsque les publicités sont activées et que AirPlay est activé pour démarrer la lecture d’une vidéo, la lecture vidéo ne se début jamais et aucune erreur n’est affichée.
* (ZD#33341) - `DRMInterface.h` déclenche la création d’avertissements dans Xcode 9

   Correction de deux prototypes de blocs dans `DRMInterface.h` lesquels le mot &#39;void&#39; manquait dans leurs listes de paramètres
* (ZD#31979) - Ne compile/ne s’exécute pas sous iOS 10 ou version ultérieure pour iPhone 7/iPhone7+.

   Correction de la compilation de documents IB pour les versions antérieures à iOS 7 qui n’est plus prise en charge
* (ZD#32920) : écran blanc dans une coupure publicitaire et aucune coupure publicitaire

   Lorsqu’une coupure publicitaire présente des instances de publicité et qu’une fois l’instance de publicité terminée, un écran blanc s’affiche.
* (ZD#32509) - Désactivation de l’enregistrement d’écran iOS 11 Désactivation de l’enregistrement d’écran sous iOS 11

* (ZD#33179) - Panne de événement intermittente sur iOS11

   Correction de l’échec du événement sur iOS 11

**Version 1.4.40** (1.4.40.72)

* (ZD #32465) - Le lecteur ne peut pas gérer les listes de lecture fusionnées.

   Appel `finishLoadingWithError`(avec : Erreur) pour AV foundation afin d&#39;essayer d&#39;autres flux/déclencher le basculement.

* (ZD #31951) - Erreur TVSDK lors des rotations de licence.

   Correction du problème de rotation des licences.
* (ZD #31951) - Ecran blanc au sein d’une coupure publicitaire et aucune coupure publicitaire n’est terminée.

   Correction d’un problème en raison duquel les publicités Facebook VPAID renvoyaient souvent plusieurs blocs CDATA dans un seul noeud `<AdParameters>` VAST.
* (ZD #33336) - TVSDK iOS - Les capsules publicitaires ne sont pas remplies, bien que suffisamment de publicités aient été renvoyées par FreeWheel.

   Création d’une relation parent-enfant entre la publicité de séquence et la publicité de secours et tri basé sur la séquence et l’index parents.

**Version 1.4.39** (1.4.39.43)

* (ZD #32178) - La version du SDK iOS TVSDK est incorrecte.

   La sortie de la version TVSDK dans les fichiers journaux était 1.0.211. Elle est corrigée pour produire la version correcte.

* (ZD #32199) - Chargement de publicités différé - La vidéo n’est pas affichée pour le contenu.

   La chronologie locale d’Adbreak qui n’était pas initialisée auparavant est maintenant actualisée avant l’utilisation.

* (ZD #27528) - Vidéo, audio ou les deux gèlent de 1 à 45 secondes après la lecture d’un fichier début, si le son secondaire n’est pas défini sur non par défaut sur iOS 1.2.

   Préparez et informez les pistes audio à l&#39;état Prêt.

* (ZD #30411) - Vous pouvez obtenir des résultats inattendus, comme l’absence d’audio ou d’audio incorrect, si vous choisissez une langue Sap secondaire.

   Préparez et informez les pistes audio à l&#39;état Prêt.

* (ZD #32199) - Chargement de publicités différé - La vidéo n’est pas affichée pour le contenu.

   La chronologie locale d’Adbreak qui n’était pas initialisée auparavant est maintenant actualisée avant l’utilisation.

* (ZD #27528) - Vidéo, audio ou les deux gèlent de 1 à 45 secondes après la lecture d’un fichier début, si le son secondaire n’est pas défini sur non par défaut sur iOS 1.2.

   Préparez et informez les pistes audio à l&#39;état Prêt.

* (ZD #30411) - Vous pouvez obtenir des résultats inattendus, comme l’absence d’audio ou d’audio incorrect, si vous choisissez une langue Sap secondaire.

   Préparez et informez les pistes audio à l&#39;état Prêt.

**Version 1.4.38** (1.4.38.860)

* (ZD #29281) - iOS : Ajouter d’AdSystem et d’ID de création aux demandes CRS

Utilisation de l’ID de création et d’AdSystem dans la requête CRS en fonction des règles de normalisation CRS

* (ZD #29176) - Blocage `PTAdPolicyDeligate` `satAdBreakAsWatched:position`

Le blocage dû à un AdBreak vide est maintenant géré.

* (ZD #30125) - Les annonces par programmation ne fonctionnent pas sur la plate-forme iOS

Ajout de la prise en charge des annonces par programmation dans iOS.

* (ZD #30782) - #EXT-X-PROGRAMME-DATE-HEURE Notification

Le événement de métadonnées minutées n’est pas déclenché pour la balise # EXT-X-PROGRAMME-DATE-TIME avec les flux DRM EN DIRECT.

**Version 1.4.37 (1.4.37.842)**

* (ZD #28950 ) - Problème de lecture VOD

Problème de lecture lorsque la balise # EXT-X-PLAYLIST-TYPE du flux est définie sur Événement plutôt que VOD

* (ZD #29281) - iOS : Ajouter d’AdSystem et d’ID de création aux demandes CRS

Utilisation de Creative Id et d’AdSystem dans la requête CRS en fonction des règles de normalisation CRS.

* [ ZD #29462) - TremorHub et les VOD A&amp;E provoquent un blocage dans les applications iOS.

**Version 1.4.36 (1.4.36.835)**

* (ZD #29418) - Les cônes de durée 0 (#EXT-X-CUE-OUT:0.000) provoquent l’arrêt ou le blocage de la lecture du TVSDK iOS.

Le problème est corrigé et les débuts de lecture sont corrects.

* (ZD #29462) - Publicité dans VOD provoquant un blocage sur le SDK TVSDK iOS.

Le problème est résolu. Le SDK iOS TVSDK génère un problème `exception(AUDNetworkAdInfo::initWithAdId)` et ne le gère pas. L&#39;exception est due à un identifiant de publicité vide.

* (ZD #29281) - Ajouter les demandes AdSystem et Creative ID pour CRS.

Incluez AdSystem et CreativeId comme nouveaux paramètres dans les requêtes 1401 et 1403 (tous les autres paramètres restent les mêmes).

**Version 1.4.35** (1.4.35.830)

* (ZD #27830) - Nécessité de déterminer par programmation la différence entre les sous-titres et les sous-titres dans iOS.

TVSDK expose désormais les deux types qui peuvent être utilisés pour filtrer le type de légende requis.

* (ZD #29160) - Les signaux publicitaires EXT-X-CUE-OUT ne sont pas correctement épinglés sur TVSDK iOS.

La publicité EXT-X-CUE-OUT est en cours de lecture.

* (ZD #29100) - L’application se bloque lorsque l’utilisateur passe à la fin d’un film.

Correction de plusieurs blocages liés à la synchronisation.

* (ZD #28785), (ZD #27712) et (ZD #25076) - L’application iOS se bloque pendant les grands événements en direct.

Correction de plusieurs blocages liés à la synchronisation.

**Version 1.4.34** (1.4.34.815 pour iOS 6.0+)

* (ZD #28481) - Passez en panne en raison de l’ajout d’une clé incorrecte à la fin d’une coupure publicitaire pour ces flux FER.

Pour un flux FER, la clé avant la coupure publicitaire est insérée après la fin de la coupure publicitaire. Ce problème a été résolu en ajoutant la *dernière clé* affichée à la fin de la coupure publicitaire.

**Version 1.4.33** (1.4.33.803 pour iOS 6.0+)

* (ZD# 21701) Activation de CRS pour les sous-comptes

Activé en envoyant l’URL de création d’origine pour la demande CRS 1401 au lieu de l’URL normalisée, selon les exigences du serveur principal CRS.

* (ZD# 26218) - Problème de chargement du fichier PSDKResources.bundle

Ce problème a été résolu en mettant à jour le chargement des ressources afin de rechercher tous les lots disponibles.

* (ZD# 27460) Premier appel publicitaire - POST au `cdn.auditude.com` retour 403.

Le nouveau compte CDN ne peut pas gérer une demande de CDN POST. Ce problème a été résolu en mettant à jour le code afin que la `cdn.auditude.com` demande d’annonce soit GET (GET) et non POST (POST).

**Version 1.4.32** (1.4.32.792 pour iOS 6.0+)

* (ZD# 27132) Prise en charge des valeurs décimales pour les pauses publicitaires VMAP.

Lorsque le contenu n’était pas segmenté en fonction des coupures publicitaires définies, des entiers provoquaient des emplacements publicitaires inattendus. Le problème a été résolu en ne convertissant pas les valeurs décimales en entiers.

* (ZD# 27189) Le contenu AES avec la balise EXT-X-DISCONTINUITY-SEQUENCE ne se lit pas correctement.

Le problème a été résolu en plaçant la balise au début de la liste de lecture.

**Version 1.4.31** (1.4.31.785 pour iOS 6.0+)

* (ZD# 24528) Mise en oeuvre des mesures d’utilisation du SDK TVSDK pour la facturation

Pour plus d’informations, voir Mesures [de]facturation.

* (ZD# 24642) Prise en charge de l’image pour TVSDK

La fonction d&#39;image dans l&#39;image, qui ne fonctionnait pas correctement dans certains cas, a été corrigée.

* (ZD# 25246) Signaux de coupures publicitaires incorrects

Ce problème a été résolu en alignant les balises de discontinuité entre les manifestes de variantes.

* (ZD# 26218) Le processus de création d’applications se complique lorsque vous essayez d’inclure PSDKLibrary.framework dans la structure d’applications du client.

Ce problème a été résolu en assemblant le fichier PSDKLibrary.framework comme demandé.

* (ZD# 26364) Prise en charge de plusieurs CDN pour les publicités CRS

Pour plus d’informations, voir Prise en charge de CDN multiples pour CRS Ad Diffusion.

* (ZD# 27028) Délai de lecture de certains flux dans iOS 10.

Ce problème a été résolu en fournissant une solution pour les flux qui n&#39;ont pas d&#39;extension M3U8.

**Version 1.4.30** (1.4.30.754 pour iOS 6.0+)

Les problèmes suivants ont été résolus pour TVSDK dans cette version :

* (ZD# 24180) Ajouter un en-tête personnalisé en liste blanche

Un nouvel en-tête personnalisé a été ajouté à la liste blanche TVSDK.

* (ZD# 25016) Le flux de basculement est sélectionné de manière aléatoire lorsque les paramètres de contrôle ABR sont définis

Ce problème a été résolu en maintenant les flux ABR dans l’ordre lorsque les paramètres ABR sont fournis avec le paramètre initialBitrate sur un flux qui inclut des URL de basculement. Cela évite de lire les flux de basculement plutôt que les flux principaux.

* (ZD# 25076) Crash sur PTAuditudeAdResolver loadComplete

Le problème qui se produisait lors d’un début/arrêt rapide de plusieurs instances PTMediaPlayer avec publicités a été résolu.

* (ZD# 25960) Aucune balise d’abonnement supplémentaire n’est vide, ce qui déclenche des diffusions de notification de modification des métadonnées.

Le problème qui se produit lorsqu’une balise abonnée n’est pas avertie lorsqu’elle apparaît avant le premier segment dans le manifeste a été corrigé.

* (ZD# 26084) PSDK lance un 106000.101000.Erreur de décodage de -11833 lors de la transition entre la dernière coupure publicitaire et le contenu de divertissement

Lorsque le dernier début de coupure publicitaire du VMAP tombe avant que la durée totale ne soit terminée, dans certaines conditions, la clé n&#39;est insérée qu&#39;après la fin de la dernière coupure publicitaire. Ce problème a été corrigé.

* La bibliothèque Video Heartbeat (VHL) a été mise à jour vers la version 1.5.9 afin de résoudre les problèmes suivants :

* (ZD #22351) VHL - Analyses : Durée de la ressource vidéo en direct

Ce problème a été résolu en ajoutant l’API assetDuration à PTVideoAnalyticsTrackingMetadata afin de mettre à jour la durée de la ressource pour les flux en direct/linéaires et de fournir une logique de vérification du flux en direct.

* (ZD# 22675) VHL - Analyses : Mise à jour de la durée des fichiers vidéo en direct

Ce problème est identique à celui du ZD #22351.

* (ZD #25908) VHL - Analyses : Corbeille du Événement Adobe Heartbeat

Ce problème a été résolu en mettant à jour l’implémentation pour utiliser la dernière version de VHL pour iOS version 1.5.9 afin d’améliorer la stabilité et les performances.

* (ZD #25956) VHL - Analyses : Blocage lors de la lecture répétée de vidéos

Ce problème est identique à celui du ZD #25908.

**Version 1.4.29** (1.4.29.743)

* (ZD# 23901) Les publicités tierces ne sont pas lues

Ce problème a été résolu en passant à la structure d’URL CRS v3 pour inclure l’ID de zone dans l’URL reconditionnée.

* (ZD #25183) Problèmes de lecture DRM sur tvOS et iOS

Ce problème a été résolu en prenant en charge plusieurs balises clés nécessaires à la prise en charge de DRM multiples.

* (ZD# 25334) TVSDK ne parvient pas à lire un contenu partagé cDVR

Ce problème a été résolu en empêchant TVSDK de convertir des chaînes vides en URL absolues.

* (ZD# 25347) Définition de l’en-tête HTTP personnalisé sur AVURLAsset

La prise en charge des en-têtes personnalisés sur ses demandes de segment par le biais de la classe PTNetworkConfiguration a été ajoutée.

**Version 1.4.28** (1.4.28.722)

* (ZD n° 24549) Plusieurs appels de suivi d’annonce

Ce problème a été résolu en mettant à jour le gestionnaire de chronologies afin d’écouter les notifications sur un objet spécifique lors de la création de plusieurs lecteurs.

* (ZD #24758) PTManifestLogger ne prend pas en charge iOS 8

Ce problème a été résolu en mettant à jour la bibliothèque de l’utilitaire de journalisation vers la cible de déploiement de la version 7.0.

* (ZD #24775) Flux retardé en raison de publicités

Ce problème a été résolu en calculant correctement la dérive de durée sur les listes de lecture de événement.

* (ZD #24799) Certains épisodes ne sont pas lus sur l’application iOS

Ce problème a été résolu en utilisant le serveur Web local pour les sous-titres lorsque les fichiers WebVTT sont géolimités.

**Version 1.4.27** (1.4.27.711) pour iOS 6.0+

* (ZD #24089) - Optimisations pour la résolution des publicités sur les flux DVR longs

Ce problème a été résolu en ajoutant plusieurs optimisations afin de réduire le temps nécessaire au traitement de la fenêtre DVR dans les flux en direct/linéaire.

* (ZD #21554) - Balises d’erreur TVSDK non déclenchées pour le type d’application = video/mp4

Ce problème a été résolu en permettant au lecteur de tester les URL de suivi des erreurs correctes sur des formats de fichier non valides.

* (ZD #24424) - Un blocage de type EXC_BAD_ACCESS KERN_INVALID_ADDRESS est originaire de PSDKLib pour iOS sur les périphériques matériels plus récents.

Le blocage qui s’est produit en raison d’une instance de lecteur multimédia délocalisée, lorsque la lecture est changée rapidement entre les différents flux, a été corrigé.

* (ZD #24575) - Blocage dans TVSDK sur les périphériques 32 bits lorsque enableDebugLog=true

Le problème du format de journal qui provoquait le blocage des périphériques 32 bits lorsque la journalisation était activée a été résolu.

**Version 1.4.26** (1.4.26.702) pour iOS 6.0+

* (ZD# 20213) - TVSDK FW doit être dynamique/modulaire pour XCode7

Corrigé en mettant à jour les bibliothèques avec la prise en charge des modules

**Version 1.4.25** (1.4.25.684) pour iOS 6.0+

* (ZD #19629) - Interruption de la vidéo en direct lors de la saisie d’un fichier Airplay sur ATV 4

Ce problème a été résolu en ajoutant une période d&#39;attente après la suppression des anciens éléments, mais avant l&#39;ajout de nouveaux éléments à AVQueuePlayer. Sans la période d’attente, les notifications sont envoyées à l’élément incorrect.

* (ZD #19856) - Aucun sous-titre ne s’affiche lorsqu’il est activé par défaut.

Les problèmes de la liste de lecture webvtt, qui entraînait l’affichage incorrect des sous-titres, ont été corrigés.

* (ZD #21590) - Performances vidéo et suivi dans les derniers créateurs d’Origines

Le problème de longueur de vidéo manquante dans VideoAnalytics a été résolu.

* (ZD #20202) - La définition du style des sous-titres personnalisés bloque l’application iOS.

Ce problème a été résolu en ajoutant d’autres vérifications d’objets nuls lors de la définition des styles de sous-titres.

* (ZD #20709) - la longueur de la vidéo est signalée comme 0 dans le suivi du début vidéo.

Ce problème est identique à (ZD #21590).

* (ZD #22280) - La longueur de la vidéo Analytics est définie sur 0.

Ce problème est identique à (ZD #21590).

* (ZD n° 22592) - Problèmes liés à l’espace dans Primetime

Ce problème est le même que (ZD #19629).

* (ZD#22922) - Changement de débit manuel pour iOS

Ce problème a été résolu en proposant une option permettant de spécifier le débit maximal.

* (ZD n° 23084) - Conformité Apple pour les réseaux IPv6 uniquement

Les symboles qui n’étaient pas recommandés par Apple pour la compatibilité IPv6 ont été supprimés.

**Version 1.4.24** (1.4.24.661) pour iOS 6.0+

* ZD #2548) - Prise en charge Primetime de la publicité interactive sur mobile - VPAID 2.0

Ce problème a été résolu en mettant à jour la logique afin d’afficher la vue du lecteur en cas d’échec de lecture d’une publicité VPAID.

* (ZD #20101) - L’implémentation de chapitre personnalisé déclenche le événement de chapitre pendant la lecture de la publicité.

Ce problème a été résolu en mettant à jour VideoAnalyticsTracker afin de détecter correctement le début/la fin du chapitre lors de la transition entre les limites de chapitre et les limites autres que les chapitres.

* (ZD n° 20784) - Analyses : Déclenchement du contenu terminé pour les transitions de vidéo en direct

Ce problème a été résolu en ajoutant une logique pour déclencher manuellement la fin du contenu au cours d’une session de suivi vidéo.

Les bibliothèques suivantes ont été mises à jour :

* Bibliothèque AdobeMobile vers la version 4.10.0
* Bibliothèque VHL vers 1.5.6
* Bibliothèque VHL-Nielsen à 1.6.7
* (ZD #21855) - Les sous-titres ne sont pas lus après le milieu du rouleau

Dans ce problème, les balises de discontinuité du duplicata empêchaient l’affichage des sous-titres après le roulement moyen. Ce problème a été résolu en supprimant les balises de discontinuité les unes à côté des autres.

* (ZD #21994) - Chaîne hors limites dans les PTHLSUtils

La cause la plus probable du blocage est lorsqu&#39;une EXT-X-KEY a une URL entourée de guillemets.

* ZD #22074) - Un blocage AUDVAST se produit une fois par minute sur iOS

Dans la version 1.4.23, le blocage provoqué par la présence de caractères non sûrs dans une URL de redirection VAST a été corrigé. Toutefois, TVSDK continuait à ignorer ces publicités.

Ce problème a été résolu en gérant les caractères non sûrs et en autorisant la lecture des publicités.

* (ZD #22694) - PTMediaPlayer.  La Vue est masquée par le lecteur

Ce problème a été résolu en mettant à jour la logique afin d’afficher la vue du lecteur en cas d’échec de lecture d’une publicité VPAID.

**Version 1.4.23** (1.4.23.641) pour iOS 6.0+

* (ZD #18016) - Aucune réponse du SDK Primetime présentant une mauvaise condition réseau

Ce problème a été résolu en améliorant la notification d&#39;erreur lorsqu&#39;une erreur irrécupérable d&#39;AVFFoundation se produit et en permettant à l&#39;application de gérer le redémarrage après l&#39;erreur.

* (ZD #20580) - Blocage dans PTSplicerManager

Ce problème a été résolu en offrant une protection supplémentaire contre les problèmes de concurrence qui provoquent le blocage.

* (ZD #21782) - Code d’erreur iOS 10100

Le problème en raison duquel TVSDK renvoyait une erreur 101000 lors du démarrage de la lecture sur les flux DRM d’Adobe Access a été résolu.

* (ZD #21889) - Echec de la lecture des publicités en ligne et du contenu hors ligne

Le problème de l’échec de la lecture après la correction d’une publicité sur un contenu hors ligne chiffré AES.

* (ZD #22074) - Un blocage AUDVAST se produit une fois par minute sur iOS

Ce problème a été résolu en améliorant la gestion des balises publicitaires VAST tierces qui contiennent des caractères non valides dans l’URL.

* (ZD #22257) - TVSDK ne parvient pas à lire le flux DRM

Le problème en raison duquel TVSDK renvoyait une erreur 101000 lors du démarrage de la lecture sur les flux DRM d’Adobe Access a été résolu.

**Version 1.4.22** (1.4.22.627) pour iOS 6.0+

* (ZD #18709) - Blocage du SDK TVSDK pour iOS

Le problème de blocage survenant sur certains flux protégés DRM d&#39;Adobe Access a été résolu.

* (ZD #18850) - Mettre à jour la logique de sélection créative en fonction des règles CRS

Ce problème a été résolu en ajoutant un fichier de configuration .json pour spécifier la priorité de sélection créative.

* (ZD #19770) - Le flux vidéo AES protégé ne s’affiche plus

Le problème où certains 302 flux redirigés échouaient à jouer a été résolu.

* (ZD #19629) - Interruption de la vidéo en direct lors de la saisie d’un fichier Airplay sur ATV 4

Ce problème a été résolu en ajoutant une solution pour la mise en pause de la vidéo en direct lorsque la lecture vidéo est activée pour les périphériques Apple TV 4. Le problème semble être un problème d&#39;Apple TV 4.

* (ZD #21119) - Le SDK TVSDK est bloqué après la lecture de la publicité.

La prise en charge des flux chiffrés AES a été ajoutée avec une séquence IV lors de l’utilisation de l’insertion publicitaire.

* (ZD #21125) - Retour d’une coupure publicitaire linéaire/en direct tôt

La prise en charge du retour d’une coupure publicitaire tôt avant la lecture de la coupure publicitaire est désormais terminée. Un retour anticipé est indiqué par le biais d’une balise de manifeste personnalisée.

* (ZD #21224) - Prise en charge des jeux d’air pour les flux jetés d’Akamai

Des API ont été ajoutées à la classe PTNetworkConfiguration pour ajouter des cookies en tant que paramètres d’URL sur les segments de certains flux jetés Akamai.

* (ZD n° 21287) - Journal extérieur

Correction d’un problème en raison duquel certaines instructions de journal s’affichaient par défaut dans la console xcode même si la journalisation était désactivée.

* (ZD #21446) - Les événements de coupures publicitaires ne sont parfois pas déclenchés par TVSDK

Dans les flux de ÉVÉNEMENT, les coupures publicitaires ne sont pas déclenchées correctement dans la version précédente. Cette version résout ce problème.

**Version 1.4.21** (1.4.21.605) pour iOS 6.0+

* (ZD n° 20749) - Les abandons ignorent les réponses VAST non vides ; Déclenchement des URL de suivi des publicités supplémentaires

Un problème lié aux pings de duplicata sur les publicités de secours a été résolu.

**Version 1.4.20** (1.4.20.590) pour iOS 6.0+

* (ZD #18639) - Le TVSDK utilise un processeur/ressources excessifs sur une longue ressource d’enregistrement à chaud.

L&#39;utilisation excessive du processeur/des ressources a été corrigée dans les deux niveaux. Tout d&#39;abord en laissant la fonction de mise à jour temporelle s&#39;exécuter sur une file d&#39;attente globale, au lieu du thread principal, et en optimisant l&#39;utilisation de l&#39;UC pour analyser le manifeste avec le m3u8 précédemment traité et mis en cache.

* (ZD #19349) - Les publicités preroll sont ignorées lors du ralentissement de la connexion réseau.

Ce problème a été résolu en fournissant un événement de temporisation (requestTimeout) à l’application et aux métadonnées adMetadata.  API adRequestTimeout pour remplacer le délai d’attente de 10 secondes par défaut.

* (ZD #19446) - Notification manquante sur les flux en direct

Ce problème a été résolu en permettant à l&#39;application de s&#39;abonner à EXT-X-PROGRAMME-DATE-TIME sur les flux en direct.

* (ZD #19459) - Blocage lors de la préparation d’un fichier audio alternatif avec PTMediaPlayerItem prepareAudioOptionsWithAVMediaSelectionOptions
* (ZD #19460) - Crash - `[PTMediaPlayerItem prepareSubtitlesOptionsWithAVMediaSelectionOptions:nonForcedOptions:]`

Ce problème est le même que Zendesk #19459.

* (ZD #19574) - Le TVSDK ne renvoie pas de données de réponse M3U8 pour le contenu DRM ou non DRM.

Lors du chargement initial du fichier manifeste dans PTMediaPlayerItem.prepareToPlay, en cas d’échec du chargement du manifeste, TVSDK ne signale pas le corps de la réponse d’échec à l’application.

Ce problème a été résolu en permettant à TVSDK de signaler la réponse à l’échec comme une erreur à l’application.

* (ZD #19615) - La logique de secours ne fonctionne pas

Dans l’implémentation actuelle, les publicités de secours ont été ignorées et n’ont pas été reconditionnées à moins que ces publicités ne soient au format m3u8. Ce problème a été résolu en ajoutant également la prise en charge du reconditionnement des annonces de secours.

* (ZD #19770) - TVSDK ne parvient pas à lire un contenu AES protégé avec une redirection 302.

Le problème de redirection a été résolu, car l&#39;URL de redirection était effacée par cleanConnectionData avant de pouvoir être utilisée pour analyser le manifeste.

* (ZD #19856) - Les sous-titres ne s’affichent pas pour certains débits lorsqu’ils sont activés par défaut.

Ce problème a été résolu en gérant l’erreur provenant d’iOS pour les segments des flux dans lesquels les sous-titres ne s’affichent pas.

* (ZD #19868) - Le TVSDK se bloque lorsqu’un élément créatif non valide fait l’objet d’un trafic.

Le blocage de TVSDK qui délocalisait incorrectement une instance de l’analyseur étendu a été corrigé.

* (ZD #20180) - Les publicités VPAID sont parfois ignorées.

Le type MIME JavaScript n’était pas toujours inclus ou considéré comme un type MIME valide. Ce problème a été résolu en incluant JavaScript comme type MIME valide.

* (ZD n° 20749) - Les abandons ignorent les réponses VAST non vides ; Déclenchement des URL de suivi des publicités supplémentaires

Le problème de non-reconditionnement de certains éléments créatifs a été résolu.

**Version 1.4.19** (1.4.19.563) pour iOS 6.0+

* ZD #18639) - Le TVSDK utilise un processeur/ressources excessifs sur un long fichier d’enregistrement à chaud.

Ce problème a été résolu en optimisant la réécriture de la liste de lecture DRM m3u8 pour mettre en cache les bits de la liste de lecture qui ont été précédemment réécrits. Ceci est particulièrement pertinent lorsque vous lisez des flux m3u8 en direct pour lesquels le m3u8 est téléchargé après chaque téléchargement de segment.

* (ZD#18956) - player.drmManager est nul lorsque le point d’arrêt est défini dans le lecteur de démonstration iOS.

Ce problème a été résolu en mettant à jour l’implémentation de l’API PTMediaPlayer.drmManager pour récupérer DRMManager depuis la structure DRM.

**Version 1.4.18** (1.4.18.557) pour iOS 6.0+

* (ZD #18844) Suivi du curseur de lecture pour le contenu en direct dans le lecteur iOS.

Ce problème a été résolu en permettant aux applications de définir leur propre valeur de curseur de lecture.

* (Zendesk #18518) - Si le nom de la vidéo n’est pas spécifié, le nom de TVSDK est défini par défaut sur * PSDK Player.*

Ce problème a été résolu en supprimant la valeur par défaut du nom du lecteur.

**Version 1.4.17** (1.4.17.545) pour iOS 6.0+

* (Zendesk #2228) - Améliorer TVSDK pour renvoyer la réponse JSON de la récupération d’un manifeste

Au lieu d&#39;envoyer une erreur lorsque le contenu n&#39;est pas M3U8, DRM Framework renvoie une valeur de DRMMetadata nulle. Le problème a été résolu en ajoutant des métadonnées pour exposer le contenu lorsque la notification M3U8_PARSER_ERROR se produit.

* (Zendesk #2231) - Erreur renvoyée en raison de la récupération du manifeste indisponible dans MediaPlayerNotification.

Même résolution que Zendesk #2228

* (Zendesk #3304) - Macro VAST 3.0 `[ERRORCODE]` non renseignée

Le problème en raison duquel le SDK Auditude n’envoie pas de ping lorsque l’URL de suivi comporte des espaces au début a été résolu.

* (Zendesk #17294) - Crash SecKeyRawSign

Un blocage possible lorsque le code du client utilise la chaîne de clé a été résolu.

* (Zendesk #18008) - Prise en charge des cookies pour iOS8+ pour la prise en charge des flux jetés

Les flux jetés d’Akamai nécessitent l’envoi de cookies sur les requêtes de segments, ce qui n’était pas possible sous iOS 7 et versions antérieures. Depuis iOS 8, Apple a ajouté une API qui permet de transmettre des cookies pour les demandes de segments. Cette prise en charge est désormais disponible dans TVSDK. La prise en charge de l’envoi d’un agent-utilisateur a également été ajoutée, le cas échéant.

* (Zendesk #18166) - TVSDK 1.4.15 fournit des centaines d’avertissements lors de la compilation avec DWARF avec des options de fichier dSYM.

Tous les avertissements ont été résolus.

**Remarque**: Des bibliothèques compatibles tvOS ont été ajoutées pour TVSDK.

**Version 1.4.16** (1.4.16.1454)

* Zendesk #3875 - Blocs d’onglet S pendant la lecture

Rétablissement de la dépendance d’OKHTTP à l’auditude pour CRS parce que TVSDK utilise désormais directement la connexion httpurlconnection au lieu de l’option curl. Le problème a été résolu en supprimant les exceptions avant d’effectuer un autre appel JNI.

* (Zendesk n° 4487) - Suivi du Canal linéaire du contenu

Le problème a été résolu en réinitialisant le suivi de pulsation vidéo au cours d’une session de lecture de flux linéaire.

* (Zendesk #17919) - Android - la recherche de contenu provoque une erreur de pulsation

Le problème était de résoudre la pulsation dans un état d’erreur lorsqu’il y a une recherche dans un chapitre.

* (Zendesk #18053) - Application utilisant les blocages de TVSDK sur Marshmallow

TVSDK se bloquait sur Android M OS lorsque la bibliothèque TVSDK utilisait du code néon qui convertissait les couleurs YUV `->` RGB. Ce problème a été résolu en mettant à jour les fonctions à l’origine de ce problème en utilisant une version non néon de `code`.

* (Zendesk #18072) - Android M - Crash d’application

Ce blocage survient lors de l’appel des API MediaCodecList et MediaCodecInfo lors de la vérification de la prise en charge du profil et du niveau. Adobe recherche la prise en charge de Google pour obtenir des informations supplémentaires. Ce problème a été résolu en fournissant une solution temporaire en chargeant toutes les informations de codec à l’avance afin d’éviter d’appeler ces API uniquement lorsque des informations de codec sont nécessaires.

* (Zendesk #18074) - Sous-titres arabes ne fonctionnant pas sur Nexus avec Android 6.0

Ce problème a été résolu en prenant en charge la carte des polices CTS Android.

**Version 1.4.15** (1.4.15.512) pour iOS 6.0+

**Remarque**: Le module Nielsen a été supprimé de la version TVSDK, mais TVSDK sera mis à jour prochainement avec un nouveau module d’intégration Nielsen.

* (ZD #2228) - Erreur renvoyée en raison de la récupération du manifeste non disponible dans MediaPlayerNotification.

Ajout de métadonnées pour exposer le contenu lorsque la notification M3U8_PARSER_ERROR se produit.

* (ZD #4437) - Blocages au sein du SDK Adobe Primetime

Correction d’un blocage signalé lors de la préparation de sous-titres/audio alternatif.

* (ZD n° 4487) - Suivi du Canal linéaire du contenu

Réinitialisation autorisée de l’outil de suivi de pulsation vidéo pendant une session de lecture de flux linéaire.

**Version 1.4.14** (1.4.14.498) pour iOS 6.0+

* (ZD #17260) - Blocage sur playlistManagerForURL

Correction d’un blocage intermittent en raison de problèmes d’accès simultané.

**Version 1.4.13** (iOS 6.0+)

* (ZD #3304) - Macro VAST 3.0 `[ERRORCODE]` non renseignée

   * Le code d’erreur 400 sera affiché si la publicité intégrée comporte un élément créatif incorrect.
   * `[ERRORCODE]` sera codée en URL.

* (ZD #3865) Intégration de la pulsation avec les annonces IMA

Correction d’un bogue en raison duquel la longueur de la vidéo était incorrectement reportée.

* Mise à jour du lecteur de démonstration TVSDK pour la prise en charge d’iOS 9

Pour prendre correctement en charge iOS 9, vous devez configurer les exceptions de la sécurité du transport des applications. Aux fins de la démonstration, l&#39;ATS est complètement désactivé.

**Version 1.4.12** (1.4.12.464) pour iOS 6.0+

* (ZD #4521) CRS Testing Client Side and SSAI

Correction d&#39;un MD5 inversé dans l&#39;URL 3P.

**Version 1.4.12** (1.4.12.463) pour iOS 6.0+

* (ZD n° 2751) ISAC et CS Ex / Amélioration : Gérez les éléments dynamiques dans certaines URL de fichier multimédia.

Mise à jour de Creative Repackaging Service afin de gérer correctement les publicités avec des URL créatives dynamiques.

* (ZD #3654) Fuite de mémoire dans la version PSDK après la version 1.3.4.166

Correction d’une fuite de mémoire dans drmFramework avec lecture régulière sur les périphériques iOS 8.2.

* (ZD #3988) Le paramètre Preroll est ignoré lors de la recherche d’un élément de remplacement après la première lecture.

Correction d’un bogue afin que les stratégies publicitaires puissent être correctement désactivées.

* (ZD n° 4017) Demande d’API iOS pour forcer la lecture des publicités à l’envers

Correctif pour ZD #4279 résolu

* (ZD #4279) Problème de redirection HLS TVSDK et d’insertion de -302 problème de redirection sur iOS et sur le bureau

Correction d’un bogue en raison duquel une ressource publicitaire utilisait une URL de redirection relative.

**Version 1.4.9** (1.4.9.427) pour iOS 6.0+

* (ZD #3075) Problème de disponibilité d’Internet - iOS

Ajout d’une notification pour détecter le blocage de la lecture.

* (ZD #3193) Demande d’API de modification de Profil dans TVSDK

Mise à jour de PTPlaybackInformation afin d’exposer la mise à jour de l’indicateurBitrate. Mise à jour de la notification BITRATE_CHANGE afin d’être plus fiable et plus précis en temps pour les débits signalés par M3U8.

* (ZD #3324) Problème de rapports des publicités Primetime lorsqu’aucun média publicitaire n’est présent dans VMAP

Prise en charge de la prise en charge des URL de suivi des coupures publicitaires vides, TVSDK vérifie désormais le début des coupures publicitaires et complète les pings pour les coupures publicitaires vides.

**Version 1.4.8** (1.4.8.402)

* (ZD n° 3158) IOS 7 se bloque lors des relectures en Événement complet

**Version 1.4.7** (1.4.7.382)

* (ZD #2197) Suivi des erreurs et des erreurs. Échec du chargement du manifeste de la notification ajoutée pour l&#39;actif.
* (ZD #2894) Le lecteur effectue 4 demandes de manifeste de niveau supérieur pendant la lecture.
* (ZD #2992) Auditude Rapports des durées et identifiants bizarres.

**Version 1.4.6**(1.4.6.325)

* (ZD #2197) Suivi des erreurs et des erreurs. Échec du chargement du manifeste de la notification ajoutée pour la ressource

**Version 1.4.5** (1.4.5.283)

* (ZD #2141) Mise en oeuvre d’Analytics pour l’application TreeHouse, ajout d’une bibliothèque `AdobeAnalyticsPlugin.a` pour créer un package.
* Mise à jour de la bibliothèque Video Heartbeats vers la version 1.4.1.2
* [PTPALY-4226] [lié au ZD #2423) L’exécution de la réinitialisation DRM peut entraîner la suppression des données du Document d’application.

**Version 1.4.4** (1.4.4.242)

* Mise à jour de la bibliothèque Video Heartbeats Library (VHL) vers la version 1.4.1.

* (ZD #2435) La documentation du SDK TV sur les analyses nécessite des mises à jour

**Version 1.4.2** (1.4.2.210 : iOS 6.0+)

* (ZD #1129) `_player.currentItem.audioOptions` rentrant vide
* (ZD #2109) Le PSDK Primetime 1.4.1.125 ne fonctionne pas avec Xcode 5.1.1
* (ZD n° 2137) Blocage du PSDK sur iOS lorsque les métadonnées DRM ne peuvent pas être chargées

**Version 1.4.1**(1.4.1.125)

* (ZD #1107) Symboles de duplicata CocoaLumberjack
* (ZD #1644) Modifier l’agent utilisateur iOS pour le ciblage et le Rapports
* (ZD n° 1850) Fichiers de prise en charge Cocoa Lumberjack inclus dans le SDK iOS
* (ZD#1908) Les balises personnalisées sont ignorées par PSDK s’il y en a plus de 1

**Version 1.4.0** (1.4.0.32)

* Zendesk #1024 - Fonction permettant de supprimer une publicité du flux via un manifeste

## Certification et prise en charge des périphériques {#device-certification-and-support}

>[!NOTE]
>
>Les fonctionnalités suivantes **ne sont pas** prises en charge dans TVSDK :
>
>* Mouvement lent, sur n’importe quelle plate-forme ou version.
>* Jeu de ficelles en direct.


**Version 1.4.43**

* TVSDK 1.4.43 est certifié pour iOS 11.

**Version 1.4.29**

* TVSDK 1.4.29 a été certifié pour iOS 10.

**Version 1.4.28**

* TVSDK 1.4.28 a été certifié pour la version bêta 7 d’iOS 10.
* Prise en charge de DRM pour forcer HTTPS en ajoutant `forceHTTPS` et `isForcingHTTPS` des API.
* Mise à jour des bibliothèques VHL vers 1.5.8, des bibliothèques Adobe Mobile vers 4.8.4 et de la bibliothèque d’utilitaires de journalisation vers la cible de déploiement de la version 7.0.

**Version 1.4.19**

Cette version de TVSDK a été certifiée avec le support FairPlay pour iOS et tvOS.

**Version 1.4.17**

* tvOS

   Cette version de TVSDK inclut la prise en charge de tvOS et a été certifiée pour les flux HLS non chiffrés.

   **Remarque**: Rappelez-vous des consignes de compilation suivantes :

   * La prise en charge de TVSDK tvOs est limitée aux flux chiffrés DRM non-Adobe. Vous devez supprimer la référence à drmNativeInterface.framework dans vos paramètres de création tvOS. Les flux chiffrés AES sont toujours pris en charge.
   * Apple exige que toutes les applications Apple TV soient activées pour le bitcode. Vous devez donc activer cet indicateur dans les paramètres de votre projet.

## Problèmes et limites connus {#known-issues-and-limitations}

* En raison de l’obsolescence de la classe iOS UIWebView, dans le SDK iOS 3.6 à partir de :
   * Les publicités VPAID ne seront pas lues comme prévu sur iPad 13.
   * Les publicités complémentaires ne seront pas lues comme prévu.

* Dans iOS TVSDK, toutes les publicités sont assemblées dans le manifeste de contenu. Les comportements publicitaires sont implémentés en effectuant des recherches en fonction de la durée du contenu et des segments d’annonces. Ainsi, si les durées des segments ne sont pas précises, la recherche peut ne pas toujours se terminer à l’image exacte du début ou de la fin de la coupure publicitaire. Même si les durées sont au cadre, il y a une tolérance que la plate-forme elle-même impose à la recherche et il peut y avoir quelques cadres ou publicités ou contenu affichés. Il s’agit d’une limitation de la plate-forme et du fonctionnement de l’insertion de publicités avec TVSDK sur iOS.
* Dans ce cas, la décision d’ignorer se produit sur le événement de recherche. Cependant, puisque les durées du segment publicitaire dans le manifeste ne représentent pas exactement la durée réelle de la publicité, la recherche n’est pas précise. Vous voyez donc quelques cadres d’annonce lorsque les stratégies publicitaires sont appliquées.
* Il est possible que la vidéo de rotation sous licence ne soit pas lue sous iOS 11 et qu’elle soit lue correctement sous iOS 9.x et iOS 10.x.
* Dans la prise en charge de VPAID 2.0, si la lecture est active sur AirPlay, les publicités VPAID sont ignorées.
* Le fichier drmNativeInterface.framework ne se lie pas correctement lorsque la cible minimale est définie sur iOS7 (ou version ultérieure).
Solution : Spécifiez explicitement la bibliothèque libstdc++.6.dylib comme suit : Accédez à Cible->Build Phases->Link Binary With Libraries et ajoutez libstdc++.6.dylib.
* La publicité post-restauration n&#39;est pas insérée pour l&#39;API de remplacement.
* La recherche d’une coupure publicitaire (sans en sortir) génère un début publicitaire duplicata et une notification de coupure publicitaire
* La définition de currentTimeUpdateInterval n’a aucun effet.
Remarque : Dans certaines versions d’iOS, le système d’exploitation ne charge pas automatiquement les ressources dans PSDKLibrary.framework. Il est important de copier manuellement le fichier PSDKResources.bundle dans les ressources d&#39;assemblage de l&#39;application : Accédez à &quot;Build Phases&quot; (Créer des phases) et copiez les ressources d’assemblage.
* L’application de référence ne peut pas être créée à l’aide de Xcode 8 ou de versions inférieures. iOS TVSDK version 1.4.41 et ultérieure, utilisez Xcode 9 pour compiler.
* Les publicités VPAID ne respectent pas la valeur delayAdLoadingTolerance.
* 24077- Pour certains contenus HLS avec sous-titres, le lecteur se bloque lors de la méthode Stop ou Reset.
* Les notifications d’erreur détaillées ne sont pas disponibles au cas où la résolution de publicités juste à temps est activée.
* Les notifications d’erreur sont consignées selon l’heure de résolution de la publicité et non selon la séquence.
* La prise en charge de HEVC présente les restrictions suivantes dans cette version
   * DRM non pris en charge
   * Le soutien du CC (CEA 608/708) n&#39;est pas disponible car il n&#39;est pas pris en charge dans le CMAF.
   * La prise en charge de 4K n&#39;est pas encore présente.
   * Les balises ID3 ne sont pas prises en charge car elles ne le sont pas dans CMAF.
   * Flux HEVC dynamiques non muxés non vérifiés.
   * La prise en charge des publicités HEVC n&#39;a pas été vérifiée.
* Si JIT est activé et que la tolérance est définie sur 10 secondes, aucun appel VAST n’est visible pour la première coupure publicitaire intermédiaire en cas de publicités de redirection VMAP->VAST.
* Pour que le délai d’expiration de la résolution de la publicité fonctionne correctement, chaque fois que la liste de lecture est mise à jour pendant la lecture en flux continu, le lecteur s’attend à ce qu’une liste de lecture assemblée soit établie dans un délai de 20 secondes. S’il ne reçoit pas de liste de lecture cousue dans ledit intervalle, une erreur interne est générée et le lecteur s’arrête.

## Ressources utiles {#helpful-resources}

* [Guide du programmeur TVSDK 3.4 pour iOS](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-for-ios/introduction/ios-3x-overview.html)
* [Référence de l’API TVSDK iOS 3.4](https://help.adobe.com/en_US/primetime/api/psdk/appledoc_v34/index.html)
* Consultez la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.
