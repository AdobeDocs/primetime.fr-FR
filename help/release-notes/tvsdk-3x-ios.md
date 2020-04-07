---
title: Notes de mise à jour de TVSDK 3.11 pour iOS
description: Les Notes de mise à jour de TVSDK 3.11 pour iOS décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus et les problèmes de périphérique dans TVSDK iOS 3.11.
translation-type: tm+mt
source-git-commit: ac75f63f98060e1937570476362bb5d4458d1f85

---


# Notes de mise à jour de TVSDK 3.11 pour iOS {#tvsdk-for-ios-release-notes}

Les Notes de mise à jour de TVSDK 3.11 pour iOS décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus et les problèmes de périphérique dans TVSDK iOS 3.11.

## Configuration système et logiciel requise {#system-software-requirements}

Avant de télécharger iOS 3.11, assurez-vous que les versions de votre matériel, de votre système d’exploitation et de vos applications répondent aux exigences suivantes :

Système d’exploitation : iOS 8.0 ou version ultérieure.

## iOS TVSDK 3.11

Correctifs pour les problèmes client qui provoquent le blocage de l’application `isFallbackOnInvalidCreativeEnabled` et `customParams` provoquent le blocage de la méthode et de l’application.

Pour les correctifs de la version actuelle, reportez-vous à la section Problèmes [client résolus](#resolved-issues) et pour les limitations, reportez-vous à la section Problèmes [connus et limites](#known-issues-and-limitations) .

### Nouvelles fonctionnalités et correctifs des versions précédentes {#whats-new-previous}

**iOS TVSDK 3.10**

* Correction d’un problème en raison duquel le lecteur TVSDK ne déclenchait pas `PTMediaPlayerStatusError` de notification lorsque le réseau n’était pas disponible.

**iOS TVSDK 3.9**

* Correction d’un problème en raison duquel la lecture des sous-titres VTT échouait et provoquait le blocage de l’application.

* iOS TVSDK 3.9 incluait le certificat de transport d’individualisation mis à jour.

**Correctif iOS TVSDK 3.8.0.83**

Le correctif contenait le certificat de transport d&#39;individualisation mis à jour.

**iOS TVSDK 3.8**

Conformité iOS 13 et prise en charge de la désapprobation de l’API UIWebView iOS 13.

**iOS TVSDK 3.7**

Correctif d’un scénario dans lequel la lecture s’arrêtait lorsqu’un grand nombre de demandes de résolution d’annonce étaient effectuées simultanément.

**iOS TVSDK 3.6**

**Correctifs dans la propriété vasteXML de la classe`PTNetworkAdInfo`**

La propriété vasteXML n’était pas correctement définie et renvoyait une valeur nulle.

**iOS TVSDK 3.5**

**Activation de l’audio en arrière-plan**

*Configurez votre application pour qu’elle continue la lecture audio lorsqu’elle passe en arrière-plan.*

Pour activer cette fonctionnalité, nous devons définir la nouvelle API `audioPlaybackInBackground` ajoutée à la classe PTMediaPlayer. Lorsque cette API est activée, votre application est prête à lire le son en arrière-plan.

**iOS TVSDK 3.4.0.19 (Correctif)**

Cette version comprend un correctif pour les blocages d’application survenant dans un scénario de basculement publicitaire.

**iOS TVSDK 3.4**

**Délai de résolution de la publicité**

* Avec TVSDK 3.4, les utilisateurs peuvent désormais définir la valeur du délai d’expiration pour la résolution globale de la publicité et les téléchargements de manifeste. Si, dans un délai d’attente donné, certaines publicités ne sont pas résolues, TVSDK lit les publicités restantes.

* PTAdMetadata : L’API adRequestTimeout est obsolète et sera supprimée. La valeur par défaut a été définie sur 35 secondes.

* Deux nouvelles API alternatives ont été introduites dans PTAdMetadataClass : adResolutionTimeout - délai d’expiration pour les appels de résolution d’annonce globale adManifestTimeout - délai d’expiration pour les téléchargements de manifeste d’annonce.

**Optimisation des recettes**

Activation du SDK TVSDK pour identifier les zones problématiques liées au d’insertion d’annonces publicitaires  à signaler à un point de terminaison de choix d’analyse.

**Version 3.3**

TVSDK 3.3 est désormais compatible avec le SDK iOS 11. Toutes les API obsolètes ont été remplacées par des alternatives appropriées.

**Version 3.2**

**Prise en charge supplémentaire de la journalisation (Phase 2)**

Ajout de la prise en charge des notifications d’erreur en cas de :

* La version HLS de la publicité utilise un niveau supérieur au contenu.

* La variante audio uniquement est exclue.

* Échec de la demande VAST/VMAP.

**Version 3.1**

* **Prise en charge** supplémentaire de la journalisation Ajout de la prise en charge des notifications descriptives en cas d’échec de la lecture d’une publicité.

* **Ajout de la prise en charge** des flux CMAF chiffrés Fairplay Les flux CMAF chiffrés Fairplay avec lecture du codec AVC sont désormais pris en charge.

**Version 3.0.1**

Aucune nouvelle fonctionnalité ou amélioration dans cette version.

**Version 3.0**

* TVSDK 3.0 prend en charge les flux HEVC.

* Juste à temps : résolution des publicités plus proches des marqueurs publicitaires.

Ajout `enableDelayAdLoading` d’une propriété de type booléen dans l’interface au niveau de l’application pour activer JIT. Si `enableDelayAdLoading` la valeur NO est affectée, elle `setadMetadata.delayAdLoading`est affectée de la valeur True (propriété de l’interface PTAdMetadata).

Lorsque cette propriété est activée, TVSDK résout chaque coupure publicitaire avant sa position en fonction de la valeur de tolérance définie. Par défaut, `delayAdTolerance` est défini sur 5 secondes.

**Version 1.4.45**

Pour se conformer à Xcode10, TVSDK est passé de &quot;`libstdc++`&quot; à &quot;`libc++`&quot;. Par conséquent, la version minimale prise en charge est iOS 7. Auparavant, il s’agissait d’iOS 6.

**Version 1.4.44**

Aucune nouvelle fonctionnalité ou amélioration dans cette version.

**Version 1.4.43**

* Expérience de type TV de la possibilité de rejoindre au milieu d’une publicité sans déclencher le suivi partiel d’une publicité.\
   Exemple : L’utilisateur se joint au milieu (à 40 secondes) d’une coupure publicitaire de 90 secondes composée de trois publicités de 30 secondes. Il s&#39;agit de 10 secondes dans la seconde publicité pendant la coupure.

   * La seconde publicité est lue pour la durée restante (20 s), suivie de la troisième publicité.
   * Les suivis publicitaires pour la publicité partielle lue (seconde publicité) ne sont pas déclenchés. Les suivis pour la troisième publicité uniquement sont déclenchés.

* Ajout de la propriété enableVodPreroll de type booléen dans l’interface PTAdMetadata. La propriété peut être utilisée pour activer le preroll sur un flux VoD. Si enableVodPreroll a la valeur NO, PSDK ne lit pas le fichier preroll. Cela n&#39;a cependant aucun impact sur les péages. La valeur par défaut de enableVodPreroll est YES.
* L’API closeCaptionDisplayEnabled de l’interface PTMediaPlayer est marquée comme obsolète à partir de la version 1.4.43 d’iOS. Pour déterminer si des sous-titres sont disponibles pour un objet PTMediaPlayerItem donné, examinez la propriété subtitlesOptions de PTMediaPlayerMediaItem.

**Version 1.4.42**

Aucune nouvelle fonctionnalité n’est ajoutée dans cette version. Pour un  de problèmes résolus, reportez-vous à la section Problèmes [](#resolved-issues)résolus.

**Version 1.4.41**

Modifications de l’API :

* **isSecure**: Une nouvelle API est introduite dans isSecure pour empêcher le lecteur d’enregistrer et de lancer une erreur. La valeur par défaut est true.

* **allowExternalRecording**: Une nouvelle API est introduite pour permettre la mise en miroir des jeux d’air pour un contenu sécurisé. La mise en miroir de l’espace aérien est traitée comme un enregistrement. Par conséquent, `allowExternalRecording` la valeur doit être définie sur `True`, pour permettre la mise en miroir de l’espace ou `False` pour arrêter la mise en miroir de l’espace pour un contenu sécurisé. Par défaut, `value` est true.

**Version 1.4.40**

Aucune nouvelle fonctionnalité.

**Version 1.4.39**

* iOS TVSDK est certifié avec VHL 2.0.1 et avec VHL 2.0.1 avec Nielsen.

* Le SDK iOS TVSDK est mis à jour afin d’effectuer des requêtes CRS à partir du nouvel hôte Akamai `primetime-a.akamaihd.net`.

* La nouvelle configuration du nom d’hôte fournit des  de ressources CRS via HTTP et HTTPS (SSL) à plus grande échelle.

**Version 1.4.36**

Intégrer et certifier VHL 2.0 dans le SDK iOS TVSDK : Réduisez l’obstacle de l’ `VideoHeartbeatsLibrary` implémentation en réduisant la complexité des API.

**Version 1.4.34**

**Informations sur les publicités réseau**

Les API TVSDK fournissent désormais des informations supplémentaires sur les réponses VAST tierces. L’ID de publicité, le système d’annonce et les extensions d’annonce VAST sont fournis dans la `PTNetworkAdInfo` classe accessible par le biais `networkAdInfo` d’une propriété sur un fichier d’annonce. Ces informations peuvent être utilisées pour l’intégration à d’autres plateformes d’analyses publicitaires, telles que **Moat Analytics**.

**Version 1.4.31**

* **Mesures** de facturation Pour répondre aux besoins des clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’à un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.

   Chaque fois que TVSDK génère un de flux  , le lecteur  envoyer des messages HTTP régulièrement au système de facturation d’Adobe. La période, connue sous le nom de durée facturable, peut être différente pour le contenu VOD standard, le contenu pro VOD (publicités milieu de gamme activées) et le contenu en direct. La durée par défaut de chaque type de contenu est de 30 minutes, mais votre contrat avec Adobe détermine les valeurs réelles.

* **Prise en charge multi-CDN pour CRS Ads** TVSDK prend désormais en charge le multi-CDN pour les annonces CRS. En fournissant des détails FTP pour les annonces CRS, vous pouvez spécifier des emplacements CDN autres que le CDN par défaut détenu par Adobe, tel qu’Akamai.

**Version 1.4.29**

Dans la `PTSDKConfig` classe, l’API forceHTTPS a été ajoutée.

La `PTSDKConfig` classe fournit des méthodes pour appliquer SSL sur les requêtes effectuées sur les serveurs Adobe Primetime et de prise de décision publicitaire, DRM et Video Analytics. Pour plus d’informations, voir les méthodes `forceHTTPS` et `isForcingHTTPS` les méthodes de cette classe. Si un manifeste est chargé via HTTPS, TVSDK conserve l’utilisation du contenu HTTPS et respecte cette utilisation lors du chargement d’URL relatives à partir de ce manifeste.

>[!NOTE] Les requêtes envoyées aux domaines tiers, tels que les pixels du suivi des publicités, les URL de contenu et d’annonce et les requêtes similaires, ne sont pas modifiées. Il incombe aux fournisseurs de contenu et aux serveurs d’annonces de fournir les URL prises en charge par le biais du protocole HTTPS.

**Version 1.4.18**

Primetime iOS TVSDK prend désormais en charge les éléments créatifs JavaScript VPAID 2.0 pour permettre une expérience publicitaire interactive riche en flux continu. Pour plus d’informations sur VPAID 2.0, voir Prise en charge des publicités VPAID.

**Version 1.4.17**

* tvOS

   Le SDK TVSDK prend en charge les applications natives tvOS.
* Les types de contenu suivants peuvent être lus :

   * VOD
   * Live
   * AES-128
   * Autre audio et sous-titres
   * FER

* Les types de publicités suivants peuvent être affichés :

   * Élémentaire
   * VAST2
   * VAST3
   * VMA

* Les fonctionnalités suivantes ne sont actuellement pas prises en charge :

   * Gestion des droits numériques (DRM)
   * Bannières publicitaires
   * TVML (TV Markup Language)

**Version 1.4.13**

>[!NOTE] Le module Nielsen a été supprimé de la version TVSDK, le module TVSDK sera mis à jour prochainement avec un nouveau module d’intégration Nielsen.

**Abandon de publicité, chaînement de la marguerite dans la logique de sélection de publicité (Zendesk n° 3103)**

Pour les publicités VAST (créatives) avec la règle de secours activée, le kit TVSDK traite une publicité avec un type MIME non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours. Pour plus d’informations, reportez-vous à la section Reprise publicitaire pour les annonces VAST et VMAP.

**Version 1.4.9**

**Signalisation par coupure de courant avec remplacement de contenu alternatif**

Dans le cadre de la mise à jour de TVSDK 1.4, nous soutenons désormais le recours aux coupures régionales et le retour de celles-ci contre le contenu linéaire. Le TVSDK peut maintenant traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d&#39;arrêt même lorsque la programmation alternative est présentée à la place de la programmation originale.

**Version 1.4.8**

**Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.5**

* Possibilité d’envoyer des métadonnées avec des  vidéo et/ou des vidéo/publicitaire/de chapitre en tant que données contextuelles.

* Moins de trafic réseau : les pulsations sont moins nombreuses en moyenne et de taille plus petite.

**Version 1.4.7**

* **Prise en charge de l’individualisation sur site**

Prise en charge des installations sur site d’Adobe Individualization Server pour personnaliser la demande d’individualisation du client afin d’accéder à un autre point de terminaison.

* **Protection de sortie basée sur la résolution**

Les stratégies DRM peuvent désormais spécifier la résolution maximale autorisée, en fonction des fonctionnalités de protection de sortie du périphérique. Par exemple, &quot;Si HDCP est disponible, autorisez la lecture du contenu jusqu’à une résolution de 1080p, et si HDCP n’est pas disponible, autorisez la lecture du contenu jusqu’à une résolution de 480p&quot;.

**Version 1.4.4**

* **Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.4.1.1**

   * Ajout de la possibilité de regrouper différents cas d’utilisation d’analyses, provenant d’autres kits SDK ou lecteurs, avec Adobe Analytics Video Essentials.
   * Le suivi des publicités a été optimisé en supprimant les `trackAdBreakStart` méthodes et les `trackAdBreakComplete` . La coupure publicitaire est déduite des appels de la `trackAdStart` méthode et `trackAdComplete` de la méthode.
   * La `playhead` propriété n’est plus nécessaire lors du suivi des publicités.
   * Ajout de la prise en charge de l’ID de Marketing Cloud.

* **Intégration du SDK Nielsen**

Le SDK TVSDK prend désormais en charge l’envoi de balises mTVR et MDPR ID3 au SDK Nielsen sans intégration personnalisée. Pour commencer, téléchargez le SDK d’application iOS 3.1.2.19 Nielsen et suivez les instructions du Guide des programmeurs iOS.

**Version 1.4.0**

* **Signalisation par coupure de courant avec remplacement de contenu alternatif**

Dans le cadre de la mise à jour de TVSDK 1.4, TVSDK prend également en charge l’entrée et le retour des coupures régionales contre le contenu linéaire. Le TVSDK peut maintenant traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d&#39;arrêt même lorsque la programmation alternative est présentée à la place de la programmation originale.

* **Supprimer/Remplacer les publicités C3**

Désormais, aucun travail de préparation supplémentaire n’est nécessaire pour insérer dynamiquement de nouvelles publicités dans les ressources vidéo à la demande (VOD) qui sortent de la fenêtre C3. Le SDK TVSDK fournit désormais une API pour supprimer des plages de contenu personnalisées et insérer dynamiquement de nouvelles publicités. Cette nouvelle fonctionnalité puissante est également utile dans les cas où le contenu en direct/linéaire est diffusé pendant la diffusion et est immédiatement retiré pour être utilisé comme contenu à la demande sans le temps approprié pour &quot;nettoyer&quot; le fichier.

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

* (ZD#41289) - `NSInvalidArgumentException` est observé avec la méthode `customParams` conduisant au blocage de l’application.

### Problèmes résolus dans les versions précédentes {#resolved-issues-previous}

**iOS TVSDK 3.10**

(ZD#40943) - Le lecteur TVSDK ne déclenche pas la notification PTMediaPlayerStatusError lorsque le réseau n’est pas disponible.

**iOS TVSDK 3.9**

(ZD#40272) - Le SDK iOS TVSDK ne parvient pas à lire les sous-titres VTT avec l’erreur 101001 et entraîne le blocage de l’application.

**iOS TVSDK 3.8**

* (ZD#40087) - iOS se bloque avec une erreur du lecteur pour le contenu VOD expiré.

* (ZD#40083) - Les publicités preroll ne sont pas lues pour le flux continu avec `OpportunityGenerator` et le lecteur affiche une erreur.

* (ZD#39828) - `CurrentItem` l’annotation de nullability est manquante dans la propriété, ce qui provoque le plantage du lecteur lorsque l’état du lecteur contenu dans la notification est `PTMediaPlayerStatusStopped`.

**iOS TVSDK 3.7**

(ZD#38961) - La lecture du contenu échoue dans la fenêtre Image dans l’image (PiP) une fois qu’un contenu a terminé sa lecture, lorsque plusieurs contenus sont configurés pour être lus dans le PiP.

**iOS TVSDK 3.6**

Aucun nouveau problème dans cette version.

**iOS TVSDK 3.5**

Aucun nouveau problème dans cette version.

**Version 3.3**

(ZD#37820) - Ajout d’une liste blanche pour l’en-tête personnalisé HS-Id, HS-SSAI-TAG.

**Version 3.2**

* **Billet #36588** - Le blocage du lecteur est observé lorsque la méthode STOP de MediaPlayer est appelée.
Correction d’un blocage intermittent observé lorsque la méthode STOP est appelée pour quelques flux avec sous-titres.

* **Ticket#37080** - Demandes de  affichées pour les appels Manifest.
Correction des demandes de  de effectuées pour les URL de manifeste pendant la lecture. TVSDK effectue désormais un appel par manifeste.

* **Ticket#37** - Échec de la règle de normalisation CRS avec le type de correspondance équipCorrection d’un cas où le lecteur se bloquait lorsqu’il était rencontré avec la dernière règle de normalisation définie pour les noms d’hôtes avec un type de correspondance équipÉe.

**Version 3.1**

**Billet #36313** - Résultats intermittents imprévisibles pendant les pauses publicitaires linéairesCorrection de la lecture intermittente pendant les pauses publicitaires linéaires dans le flux continu en direct.

**Version 3.0.1**

**Billet36948** - CRS - Ordre de sélection des ressources incohérent sur iOS 12 La ressource sélectionnée pour CRS n’est pas toujours la variante de qualité la plus élevée renvoyée dans une réponse VAST ou VMAP.

**Version 3.0**

* **Ticket35311** - L&#39;état du lecteur n&#39;est pas ENDOMMAGÉ lors d&#39;une interruption d&#39;appel téléphoniqueAjout d&#39;un gestionnaire d&#39;interruption pour empêcher l&#39;interruption du lecteur. En cas d’interruption, l’état du lecteur devient PAUSED, puis la lecture reprend en cliquant sur le bouton de lecture.

* **Ticket36685** - Ressources en direct - Incohérence temporelle avec la progression du temps du lecteur et temps du marqueur SCTELe temps correct est calculé pour les marqueurs SCTE qui sont en avance sur le point réel.

* **Ticket36492** - `currentTime` et `localTime` ne sont pas mis à jour lors de la recherche d&#39;une nouvelle position pendant l&#39;heure de mise en pause, le lecteur peut désormais être défini sur zéro au cas où l&#39;état du lecteur serait en pause ; plus tôt, l’heure actuelle était définie sur zéro uniquement à l’état actif.

**Version 1.4.45**

* **Ticket36294** - Le TVSDK iOS ne fonctionne pas avec Xcode 10. Correction des problèmes de compilation avec TVSDK sur XCode 10. En raison de la configuration requise pour XCode 10, les applications créées à partir de TVSDK pour iOS 1.4.45 nécessitent un de déploiement minimum  sous iOS 7.0

* **Ticket36321** - Écart observé dans la plage recherchable entre `PTMediaPlayer` et `AVPlayer` l’instance dans l’état &quot;Lecture&quot;.

* **Ticket36493** - `libstdc++` Prise en charge sur iOS 12 Correction des problèmes de compilation avec TVSDK sur iOS 12. Les applications créées à partir de TVSDK pour iOS 1.4.45 nécessitent un de déploiement minimum sous iOS 7.0

**Version 1.4.44**

* **Ticket34683** - Le Temps De Progression De La Lecture De La Publicité Est Négatif

D’autres vérifications sont effectuées pour gérer le cas en cas de discordance entre la durée rapportée par le serveur d’annonces et le contenu de la publicité réel.

* **Ticket34801** - currentTime et localTime n’étaient pas mis à jour lorsque la recherche d’une nouvelle position pendant l’heure en pause statusPlayer peut désormais être réglée sur zéro au cas où le lecteur serait en pause ; plus tôt, l’heure actuelle était définie sur zéro uniquement à l’état actif.

* **Ticket35037** - Les étals de lecture avec une URL incorrecte lors du retour d’une insertion d’annonce basée sur un signal.
Correctif fourni pour le numéro fermé 34385 dans la version 1.4.42. Ajout du code de contrôle et de gestion des exceptions estAnnulé pour rendre la file d’attente des opérations plus robuste.

**Version 1.4.43**

* (ZD#32990) - iOS : Contenu lu au lieu de publicités sur certains indices. `selectedMediaOptionInMediaSelectionGroup` L’API qui faisait partie de l’interface AVPlayerItem a maintenant été déplacée sous AVMediaSelection dans iOS 11. Le problème a été résolu à l’aide de cette nouvelle API.

* (ZD#33683) Le SDK TVSDK a été supprimé du suffixe == des chaînes de métadonnées. Le problème est corrigé dans la logique d’analyse.

* (ZD#33905) - Le kit TVSDK iOS appelle les fichiers de manifeste avec deux agents utilisateur. Le problème de l’agent utilisateur a été résolu dans le premier appel m3u8 (cas d’installation Fresh). Les M3u8 ont les mêmes agents utilisateur pour tous les appels maintenant.

* (ZD#34293) - Les pré-rouleaux insérés dans les flux LINEAR ne sont pas lus correctement sous iOS11. Le problème est corrigé pour les publicités preroll.

* (ZD#34684) - Lorsque la stratégie de saut d’annonce est appliquée, les trames publicitaires preroll s’affichent pendant quelques secondes. Une nouvelle API, enableVodPreroll, a été introduite pour désactiver la lecture preroll dans la lecture de vod. La valeur par défaut de cette API est &quot;Yes&quot;. L’API permet d’ignorer le raccordement du contenu publicitaire dans le contenu principal.

* (ZD#34765) - Après avoir appelé stop(), peu de segments de flux de transport sont toujours téléchargés. Amélioration de l’API Stop() afin d’éviter le téléchargement des segments supplémentaires.

* (ZD#34865) - Les publicités preroll pour le flux continu sont tronquées sur iOS. En rapport avec iOS11 et l’ajout d’une vérification supplémentaire pour vérifier si le flux est pré-roll ou de contenu principal, résout ce problème.

* (ZD#35093) - Correction d’un scénario de basculement dans lequel, si la variante principale du flux échoue au démarrage (renvoie 404), la lecture ne passe pas au flux de sauvegarde.

**1.4.42 (1.4.42.118)**

* (ZD#34385) - La lecture bloque les URL incorrectes lors du retour d’une insertion d’annonce basée sur un signal.

   Augmentez le nombre maximal de répétitions pour `CustomAVAssetLoaderOperations`que les lectures du manifeste puissent continuer à s&#39;exécuter.

* (ZD#34373) - Les utilisateurs finaux ne peuvent pas diffuser sur des périphériques connectés au HDMI, lorsque l’enregistrement du flux est interdit.

* (ZD#32678) - TVSDK ne collecte pas les ID publicitaires corrects sur iOS.

   L’identifiant de publicité du créatif publicitaire final est maintenant sélectionné dans les pings VHL en cas de redirections VAST/VMAP.

* (ZD#33904) - Le SDK TVSDK n’est pas enregistré pour les notifications AVFoundation `AVAudioSessionMediaServicesWereLostNotification` et `AVAudioSessionMediaServicesWereResetNotification`.

   `PTMediaServicesWereLostNotification` et `PTMediaServicesWereResetNotification` peuvent désormais être enregistrés dans l’application du lecteur pour obtenir les notifications lorsque les services de médias sont réinitialisés ou perdus.

* (ZD#33815) - Les clients ne sont pas en mesure de mettre à jour leurs règles CRS de hiérarchisation et de normalisation sans avoir besoin d’une mise à jour de l’application.

   Ajout des `getCRSRulesJsonURL` et `setCRSRulesJsonURL` des API au SDK iOS TVSDK .

**Version 1.4.41 (1.4.41.76)**

* (ZD #34464) - Création de problèmes avec une application de référence avec TVSDK version 1.4.41

   Depuis cette version, Xcode 9 est requis pour la compilation de TVSDK pour iOS.
* (ZD n° 29456) - de l’espace dans l’état en pause

   Correction du problème de mise en pause qui se produisait lorsque la vidéo s’interrompait lors de la saisie de la lecture.
* (ZD #30371) - La durée du AdBreak change lorsque nous insérons plus de 2 publicités dans un flux linéaire.

   Correction de l’erreur lors de la tentative de lecture du contenu sur Apple TV, qui empêchait la lecture complète
* (ZD #32146)- Non `PTMediaPlayerStatusError` reçu pour le contenu HLS Live lors du blocage de la version bêta d’iOS 11

   Non `PTMediaPlayerStatusError` reçu pour le contenu HLS Live et VOD sur le blocage à l’aide de Charles (Abandonner la connexion et 403)
* (ZD n° 29242) - Echec de la lecture vidéo en cours de lecture avec activation des publicités

   Lorsque les publicités sont activées et que la fonction AirPlay est activée pour le démarrage de la lecture d’une vidéo, la lecture de la vidéo n’est jamais  et aucune erreur n’est affichée.
* (ZD#33341) - `DRMInterface.h` déclenche des avertissements de création dans Xcode 9

   Correction de deux prototypes de blocs dans `DRMInterface.h` lesquels le mot &quot;void&quot; manquait dans leur de paramètres 
* (ZD#31979) - N’est pas compilé/exécuté lorsqu’il s’agit d’iOS 10 ou d’une version ultérieure pour iPhone 7/iPhone7+.

   Correction de la compilation des  IB pour les versions antérieures à iOS 7 qui n’est plus prise en charge
* (ZD#32920) - écran blanc dans une coupure publicitaire et aucune coupure publicitaire n’est terminée

   Lorsqu’une coupure publicitaire présente des instances de publicité et qu’une fois une instance de publicité terminée, un écran blanc s’affiche.
* (ZD#32509) - Désactivation de l’enregistrement d’écran sous iOS 11 Désactivation de l’enregistrement d’écran sous iOS 11

* (ZD#33179) - Echec de  intermittent sur iOS11

   Correction de l’échec  du sur iOS 11

**Version 1.4.40** (1.4.40.72)

* (ZD #32465) - Le lecteur ne peut pas gérer les listes de lecture fusionnées.

   Appel `finishLoadingWithError`(avec : Erreur) pour la fondation AV afin d’essayer d’autres flux/déclencher le basculement.

* (ZD #31951) - Erreur TVSDK lors des rotations de licence.

   Correction du problème de rotation des licences.
* (ZD #31951) - Ecran blanc dans une coupure publicitaire et aucune coupure publicitaire n’est terminée.

   Correction d’un problème en raison duquel les publicités Facebook VPAID renvoyaient souvent plusieurs blocs CDATA dans un noeud VAST unique `<AdParameters>` .
* (ZD #33336) - iOS TVSDK - Les capsules publicitaires ne sont pas remplies, même si suffisamment de publicités sont renvoyées par Freeroue.

   Création d’une relation parent-enfant entre la publicité de séquence et la publicité de secours et tri basé sur la séquence et l’index parents.

**Version 1.4.39** (1.4.39.43)

* (ZD #32178) - La version du SDK iOS TVSDK est incorrecte.

   La sortie de la version TVSDK dans les fichiers journaux était 1.0.211. Correction pour générer la version correcte.

* (ZD #32199) - Chargement de publicités irrégulières - La vidéo n’est pas affichée pour le contenu.

   La chronologie locale d’Adbreak qui n’était pas initialisée auparavant est maintenant actualisée avant l’utilisation.

* (ZD #27528) - Les vidéos, les fichiers audio ou les deux se bloquent entre 1 et 45 secondes après la lecture d’un de fichiers, si le son secondaire n’est pas défini sur non-default sur iOS 1.2.

   Préparez et informez les pistes audio à l’état Prêt.

* (ZD #30411) - Vous pouvez obtenir des résultats inattendus, comme l’absence d’audio ou d’audio incorrect, si vous choisissez une langue Sap secondaire.

   Préparez et informez les pistes audio à l’état Prêt.

* (ZD #32199) - Chargement de publicités irrégulières - La vidéo n’est pas affichée pour le contenu.

   La chronologie locale d’Adbreak qui n’était pas initialisée auparavant est maintenant actualisée avant l’utilisation.

* (ZD #27528) - Les vidéos, les fichiers audio ou les deux se bloquent entre 1 et 45 secondes après la lecture d’un de fichiers, si le son secondaire n’est pas défini sur non-default sur iOS 1.2.

   Préparez et informez les pistes audio à l’état Prêt.

* (ZD #30411) - Vous pouvez obtenir des résultats inattendus, comme l’absence d’audio ou d’audio incorrect, si vous choisissez une langue Sap secondaire.

   Préparez et informez les pistes audio à l’état Prêt.

**Version 1.4.38** (1.4.38.860)

* (ZD n° 29281) - iOS : Ajouter d’AdSystem et d’ID de création aux demandes CRS

Utilisation de l’ID de création et d’AdSystem dans la requête CRS en fonction des règles de normalisation CRS

* (ZD #29176) - Blocage `PTAdPolicyDeligate``satAdBreakAsWatched:position`

Le blocage dû à AdBreak vide est maintenant géré.

* (ZD #30125) - Les publicités par programmation ne fonctionnent pas sur la plate-forme iOS

Ajout de la prise en charge des publicités programmatiques dans iOS.

* (ZD #30782) - #EXT-X--Notification-DATE-HEURE

Le de métadonnées minutées n’est pas déclenché pour la balise # EXT-X---DATE-TIME avec les flux DRM EN DIRECT.

**Version 1.4.37 (1.4.37.842)**

* (ZD #28950) - Problème de lecture VOD

Problème de lecture lorsque la balise # EXT-X-PLAYLIST-TYPE du flux est définie sur  plutôt que VOD

* (ZD n° 29281) - iOS : Ajouter d’AdSystem et d’ID de création aux demandes CRS

Utilisation de Creative Id et d’AdSystem dans les demandes CRS en fonction des règles de normalisation CRS.

* [ ZD #29462] - TremorHub et VOD A&amp;E provoquant un blocage dans les applications iOS

**Version 1.4.36 (1.4.36.835)**

* (ZD n° 29418) - Les cônes de durée 0 (#EXT-X-CUE-OUT:0.000) provoquent l’arrêt ou le blocage de la lecture du TVSDK iOS.

Le problème est résolu et le de lecture  correctement.

* (ZD #29462) - Publicité dans VOD provoquant un blocage sur le TVSDK iOS.

Le problème est résolu. Le SDK TVSDK iOS génère un fichier `exception(AUDNetworkAdInfo::initWithAdId)` et ne le gère pas. L&#39;exception est due à un identifiant de publicité vide.

* (ZD #29281) - Ajouter les demandes AdSystem et Creative ID aux demandes CRS.

Incluez AdSystem et CreativeId comme nouveaux paramètres dans les requêtes 1401 et 1403 (tous les autres paramètres restent les mêmes).

**Version 1.4.35** (1.4.35.830)

* (ZD #27830) - Nécessité de déterminer par programmation la différence entre les sous-titres et les sous-titres dans iOS.

TVSDK expose maintenant les deux types qui peuvent être utilisés pour filtrer le type de légende requis.

* (ZD #29160) - Les signaux publicitaires EXT-X-CUE-OUT ne sont pas correctement épinglés sur TVSDK iOS.

Avec la publicité intermédiaire EXT-X-CUE-OUT est en cours de lecture.

* (ZD #29100) - L’application se bloque lorsque l’utilisateur fait défiler une séquence vidéo vers la fin d’une séquence.

Correction de plusieurs blocages liés à la synchronisation.

* (ZD n° 28785), (ZD n° 27712) et (ZD n° 25076) - L’application iOS se bloque pendant la grande  en direct.

Correction de plusieurs blocages liés à la synchronisation.

**Version 1.4.34** (1.4.34.815 pour iOS 6.0+)

* (ZD n° 28481) - Pannes d’électricité gratuites dues à l’ajout d’une clé incorrecte à la fin d’une coupure publicitaire pour ces flux FER

Pour un flux FER, la clé avant la coupure publicitaire est insérée après la fin de la coupure publicitaire. Ce problème a été résolu en annexant la *dernière clé* affichée à la fin de la coupure publicitaire.

**Version 1.4.33** (1.4.33.803 pour iOS 6.0+)

* (ZD# 21701) Activer CRS pour les sous-comptes

Activé en envoyant l’URL de création d’origine pour la demande CRS 1401 au lieu de l’URL normalisée, conformément aux exigences du serveur CRS principal.

* (ZD# 26218) - Problème de chargement PSDKResources.bundle

Ce problème a été résolu en mettant à jour le chargement des ressources pour rechercher tous les lots disponibles.

* (ZD# 27460) Premier appel publicitaire - POST au `cdn.auditude.com` retour 403.

Le nouveau compte CDN ne peut pas traiter une demande de CDN POST. Ce problème a été résolu en mettant à jour le code afin que la demande `cdn.auditude.com` publicitaire soit GET au lieu de POST.

**Version 1.4.32** (1.4.32.792 pour iOS 6.0+)

* (ZD# 27132) Prise en charge des valeurs décimales pour les pauses publicitaires VMAP.

Lorsque le contenu n’était pas segmenté le long des coupures publicitaires définies, les entiers provoquaient des emplacements publicitaires inattendus. Le problème a été résolu en ne convertissant pas les valeurs décimales en entiers.

* (ZD# 27189) Le contenu AES avec la balise EXT-X-DISCONTINUITY-SEQUENCE ne s’exécute pas correctement.

Le problème a été résolu en plaçant la balise au début de la liste de lecture.

**Version 1.4.31** (1.4.31.785 pour iOS 6.0+)

* (ZD# 24528) Mise en oeuvre des mesures d’utilisation du SDK TVSDK pour la facturation

Pour plus d’informations, voir Mesures [de facturation].

* (ZD# 24642) Prise en charge de l’image pour TVSDK

La fonction d&#39;image dans l&#39;image, qui ne fonctionnait pas correctement dans certains cas, a été corrigée.

* (ZD# 25246) Signaux de coupures publicitaires incorrects

Ce problème a été résolu en alignant les balises de discontinuité entre les manifestes variantes.

* (ZD# 26218) Le processus de création d’applications se complique lorsque vous tentez d’inclure PSDKLibrary.framework dans la structure d’applications du client.

Ce problème a été résolu en regroupant le fichier PSDKLibrary.framework comme demandé.

* (ZD# 26364) Prise en charge multi-CDN pour les publicités CRS

Pour plus d’informations, voir Prise en charge de plusieurs CDN pour les  publicitaires CRS.

* (ZD# 27028) Délai de lecture de certains flux dans iOS 10.

Ce problème a été résolu en fournissant une solution pour les flux qui n’ont pas d’extension M3U8.

**Version 1.4.30** (1.4.30.754 pour iOS 6.0+)

Les problèmes suivants ont été résolus pour TVSDK dans cette version :

* (ZD# 24180) Ajouter d’un en-tête personnalisé en blanc

Un nouvel en-tête personnalisé a été ajouté au  blanc de TVSDK.

* (ZD# 25016) Le flux de basculement est sélectionné de manière aléatoire lorsque les paramètres de contrôle ABR sont définis

Ce problème a été résolu en maintenant les flux ABR dans l’ordre lorsque les paramètres ABR sont fournis avec le paramètre initialBitrate sur un flux qui inclut des URL de basculement. Cela évitera de lire les flux de basculement au lieu des flux principaux.

* (ZD# 25076) Blocage sur PTAuditudeAdResolver loadComplete

Le problème qui se produisait lors de l’/l’arrêt rapide de plusieurs instances PTMediaPlayer avec publicités a été résolu.

* (ZD# 25960) Aucune balise d’abonnement supplémentaire n’a déclenché des diffusions de notification de modification des métadonnées.

Le problème qui se produit lorsqu’une balise abonnée n’est pas avertie lorsqu’elle apparaît avant le premier segment du manifeste a été résolu.

* (ZD# 26084) PSDK lance un 106000.101000.Erreur de décodeur -11833 introuvable lors de la transition entre la dernière coupure publicitaire et le contenu de divertissement

Lorsque le dernier de coupure publicitaire  l’heure du VMAP est antérieure à la fin de la durée totale, dans certaines conditions, la clé n’est insérée qu’après la fin de la dernière coupure publicitaire. Ce problème a été résolu.

* La bibliothèque Video Heartbeat (VHL) a été mise à jour vers la version 1.5.9 afin de résoudre les problèmes suivants :

* (ZD #22351) VHL - Analyses : Durée de la ressource vidéo en direct

Ce problème a été résolu en ajoutant l’API assetDuration à PTVideoAnalyticsTrackingMetadata afin de mettre à jour la durée des ressources pour les flux en direct/linéaires et de fournir une logique de vérification du flux en direct.

* (ZD# 22675) VHL - Analyses : Mise à jour de la durée des fichiers vidéo en direct

Ce problème est le même que ZD #22351.

* (ZD #25908) VHL - Analyses : Adobe Heartbeat  plantage

Ce problème a été résolu en mettant à jour l’implémentation afin d’utiliser la dernière version de VHL pour iOS version 1.5.9 pour améliorer la stabilité et les performances.

* (ZD #25956) VHL - Analyses : Blocage lors de la lecture répétée de vidéos

Ce problème est le même que ZD #25908.

**Version 1.4.29** (1.4.29.743)

* (ZD# 23901) Les publicités tierces ne sont pas lues

Ce problème a été résolu en passant à la structure URL CRS v3 pour inclure l’ID de zone dans l’URL reconditionnée.

* (ZD #25183) Problèmes de lecture DRM sur tvOS et iOS

Ce problème a été résolu en prenant en charge plusieurs balises clés nécessaires à la prise en charge de DRM multiple.

* (ZD# 25334) Le kit TVSDK ne parvient pas à lire un contenu partagé cDVR

Ce problème a été résolu en empêchant TVSDK de convertir des chaînes vides en URL absolues.

* (ZD# 25347) Définition de l’en-tête HTTP personnalisé sur AVURLAsset

La prise en charge des en-têtes personnalisés sur ses demandes de segment par le biais de la classe PTNetworkConfiguration a été ajoutée.

**Version 1.4.28** (1.4.28.722)

* (ZD n° 24549) Plusieurs appels de suivi d’annonce

Ce problème a été résolu en mettant à jour le gestionnaire de chronologie afin d’écouter les notifications sur un objet spécifique lors de la création de plusieurs lecteurs.

* (ZD #24758) PTManifestLogger ne prend pas en charge iOS 8

Ce problème a été résolu en mettant à jour la bibliothèque de l’utilitaire de journalisation vers le de déploiement version 7.0.

* (ZD #24775) Flux différé en raison de publicités

Ce problème a été résolu en calculant correctement la dérive de la durée sur les listes de  de lecture des.

* (ZD #24799) Certains épisodes ne sont pas lus sur l’application iOS

Ce problème a été résolu en utilisant le serveur Web local pour les sous-titres lorsque les fichiers WebVTT sont géolimités.

**Version 1.4.27** (1.4.27.711) pour iOS 6.0+

* (ZD #24089) - Optimisations pour la résolution des publicités sur les flux DVR longs

Ce problème a été résolu en ajoutant plusieurs optimisations afin de réduire le temps nécessaire au traitement de la fenêtre DVR dans les flux en direct/linéaire.

* (ZD #21554) - Balises d’erreur TVSDK non déclenchées pour le type d’application = video/mp4

Ce problème a été résolu en permettant au lecteur d’effectuer un test ping sur les URL de suivi des erreurs correctes sur les formats de fichier non valides.

* (ZD #24424) - Le plantage de type EXC_BAD_ACCESS KERN_INVALID_ADDRESS provient de PSDKLib pour iOS sur des périphériques plus récents.

Le blocage survenant en raison d’une instance délocalisée du lecteur multimédia, lorsque la lecture est basculée rapidement entre les différents flux, a été résolu.

* (ZD #24575) - Blocage dans TVSDK sur les périphériques 32 bits lorsque enableDebugLog=true

Le problème du format de journal qui provoquait le blocage sur les périphériques 32 bits lorsque la journalisation était activée a été résolu.

**Version 1.4.26** (1.4.26.702) pour iOS 6.0+

* (ZD# 20213) - Le kit TVSDK FW doit être dynamique/modulaire pour XCode7

Corrigé en mettant à jour les bibliothèques avec la prise en charge des modules

**Version 1.4.25** (1.4.25.684) pour iOS 6.0+

* (ZD #19629) - La vidéo en direct s’interrompt lorsque vous entrez dans Airplay au format ATV 4

Ce problème a été résolu en ajoutant une période d’attente après la suppression des anciens éléments, mais avant l’ajout de nouveaux éléments à AVQueuePlayer. Sans délai d’attente, les notifications sont envoyées à l’élément incorrect.

* (ZD #19856) - Aucun sous-titre ne s’affiche lorsqu’il est activé par défaut.

Les problèmes de la liste de lecture Web, qui entraînaient l’affichage incorrect des sous-titres, ont été résolus.

* (ZD #21590) - Performances vidéo et suivi dans les derniers   de

Le problème concernant la longueur de vidéo manquante dans VideoAnalytics a été résolu.

* (ZD #20202) - La définition d’un style de sous-titres personnalisés bloque l’application iOS.

Ce problème a été résolu en ajoutant d’autres vérifications d’objets nuls lors de la définition des styles de sous-titre.

* (ZD #20709) - la durée de la vidéo est signalée comme 0 dans le suivi des  vidéo

Ce problème est identique à (ZD #21590).

* (ZD #22280) - La durée de la vidéo Analytics est définie sur 0.

Ce problème est identique à (ZD #21590).

* (ZD n° 22592) - Problèmes liés à l’espace dans Primetime

Ce problème est le même que (ZD #19629).

* (ZD#22922) - Commutation manuelle du débit pour iOS

Ce problème a été résolu en proposant une option permettant de spécifier le débit maximal.

* (ZD n° 23084) - Conformité Apple pour les réseaux IPv6 uniquement

Les symboles qui n’étaient pas recommandés par Apple pour la compatibilité IPv6 ont été supprimés.

**Version 1.4.24** (1.4.24.661) pour iOS 6.0+

* ZD #2548) - Prise en charge Primetime de la publicité interactive sur mobile - VPAID 2.0

Ce problème a été résolu en mettant à jour la logique afin d’afficher le du lecteur en cas d’échec de lecture d’une publicité VPAID.

* (ZD #20101) - L’implémentation de chapitre personnalisé déclenche le  de chapitre  pendant la lecture de la publicité.

Ce problème a été résolu en mettant à jour VideoAnalyticsTracker afin de détecter correctement les /terminées de chapitre lors de la transition entre les limites de chapitre et non-chapitre.

* (ZD n° 20784) - Analytics : Déclenchement du contenu terminé pour les vidéo en direct 

Ce problème a été résolu en ajoutant une logique permettant de déclencher manuellement la fin du contenu au cours d’une session de suivi vidéo.

Les bibliothèques suivantes ont été mises à jour :

* Bibliothèque AdobeMobile vers la version 4.10.0
* Bibliothèque VHL vers 1.5.6
* Bibliothèque VHL-Nielsen à 1.6.7
* (ZD #21855) - Les sous-titres ne sont pas lus après le milieu du rouleau

Dans ce problème, les balises de discontinuité  l’empêchaient l’affichage des sous-titres après le déroulement intermédiaire. Ce problème a été résolu en supprimant les balises de discontinuité les unes à côté des autres.

* (ZD n° 21994) - Chaîne hors limites dans PTHLSUtils

La cause la plus probable du blocage est lorsqu’une EXT-X-KEY a une URL entourée de guillemets.

* ZD #22074) - Un blocage AUDVAST se produit une fois par minute sur iOS

Dans la version 1.4.23, le blocage provoqué par la présence de caractères non sûrs dans une URL de redirection VAST a été corrigé. Toutefois, TVSDK continuait à ignorer ces publicités.

Ce problème a été résolu en gérant les caractères dangereux et en autorisant la lecture des publicités.

* (ZD #22694) - PTMediaPlayer.   masqué par le lecteur

Ce problème a été résolu en mettant à jour la logique afin d’afficher le du lecteur en cas d’échec de lecture d’une publicité VPAID.

**Version 1.4.23** (1.4.23.641) pour iOS 6.0+

* (ZD #18016) - Aucune réponse du SDK Primetime avec une mauvaise condition réseau

Ce problème a été résolu en améliorant la notification d’erreur lorsqu’une erreur irrécupérable d’AVFoundation se produit et pour permettre à l’application de gérer le redémarrage après l’erreur.

* (ZD #20580) - Blocage dans PTSplicerManager

Ce problème a été résolu en fournissant une protection supplémentaire contre les problèmes d’accès simultané qui provoquent le blocage.

* (ZD #21782) - Code d’erreur iOS 10100

Le problème en raison duquel TVSDK renvoyait une erreur 101000 lors du démarrage de la lecture sur les flux DRM d’Adobe Access a été résolu.

* (ZD #21889) - Echec de la lecture des publicités en ligne et du contenu hors ligne

Le problème d’échec de la lecture après la résolution d’une publicité sur un contenu hors ligne chiffré AES.

* (ZD #22074) - Un blocage AUDVAST se produit une fois par minute sur iOS

Ce problème a été résolu en améliorant la gestion des balises publicitaires VAST tierces qui contiennent des caractères non valides dans l’URL.

* (ZD #22257) - Le kit TVSDK ne parvient pas à lire le flux DRM

Le problème en raison duquel TVSDK renvoyait une erreur 101000 lors du démarrage de la lecture sur les flux DRM d’Adobe Access a été résolu.

**Version 1.4.22** (1.4.22.627) pour iOS 6.0+

* (ZD n° 18709) - Blocage du SDK TVSDK pour iOS

Le problème d’un blocage survenant sur certains flux protégés DRM d’Adobe Access a été résolu.

* (ZD #18850) - Mise à jour de la logique de sélection créative en fonction des règles CRS

Ce problème a été résolu en ajoutant un fichier de configuration .json pour spécifier la priorité de sélection créative.

* (ZD #19770) - Le flux vidéo AES protégé ne se lit plus

Le problème où certains flux 302 redirigés échouaient à jouer a été résolu.

* (ZD #19629) - La vidéo en direct s’interrompt lorsque vous entrez dans Airplay au format ATV 4

Ce problème a été résolu en ajoutant une solution pour la mise en pause de la vidéo en direct lorsque la lecture de l’écran est activée pour les périphériques Apple TV 4. Le problème semble être une publication d’AppleTV 4.

* (ZD #21119) - Le SDK TVSDK est bloqué après la lecture de la publicité.

La prise en charge des flux chiffrés AES a été ajoutée avec une séquence IV lors de l’utilisation de l’insertion d’annonces.

* (ZD #21125) - Retour d’une coupure publicitaire linéaire/en direct tôt

La prise en charge du retour d’une coupure publicitaire tôt avant que la coupure publicitaire ne soit lue jusqu’à l’achèvement a été ajoutée. Un retour anticipé est indiqué par le biais d’une balise de manifeste personnalisée.

* (ZD #21224) - Prise en charge des jeux d’air pour les flux jetés d’Akamai

Des API ont été ajoutées à la classe PTNetworkConfiguration pour ajouter des cookies en tant que paramètres d’URL sur les segments pour certains flux jetés Akamai.

* (ZD #21287) - Journal externe

Un problème avec certaines instructions de journal affichées par défaut dans la console xcode même lorsque la journalisation est désactivée a été résolu.

* (ZD #21446) - Le de coupures publicitaires n’est parfois pas déclenché par le kit TVSDK

Dans les flux , les coupures publicitaires ne sont pas déclenchées correctement dans la version précédente. Cette version résout ce problème.

**Version 1.4.21** (1.4.21.605) pour iOS 6.0+

* (ZD #20749) - Le rapport de secours ignore les réponses VAST non vides ; Flux d’URL de suivi des publicités supplémentaires

Un problème lié aux pings de  sur les publicités de secours a été résolu.

**Version 1.4.20** (1.4.20.590) pour iOS 6.0+

* (ZD n° 18639) - Le SDK TVSDK utilise une quantité excessive de ressources/CPU sur un fichier d’enregistrement à chaud de longue durée.

L&#39;utilisation excessive du processeur/des ressources a été corrigée dans les deux niveaux. Tout d&#39;abord en laissant la fonction de mise à jour temporelle s&#39;exécuter sur une file d&#39;attente globale, au lieu du thread principal, et en optimisant l&#39;utilisation de l&#39;UC pour analyser le manifeste avec le m3u8 précédemment traité et mis en cache.

* (ZD #19349) - Les publicités preroll sont ignorées lors du ralentissement de la connexion réseau.

Ce problème a été résolu en fournissant un de temporisation (requestTimeout) à l’application et aux métadonnées adMetadata.  API adRequestTimeout pour remplacer le délai d’expiration par défaut de 10 secondes.

* (ZD #19446) - Notification manquante sur les flux en direct

Ce problème a été résolu en permettant à l&#39;application de s&#39;abonner à EXT-X--DATE-TIME sur les flux en direct.

* (ZD #19459) - Blocage lors de la préparation d’un fichier audio alternatif avec PTMediaPlayerItem prepareAudioOptionsWithAVMediaSelectionOptions
* (ZD #19460) - Blocage - `[PTMediaPlayerItem prepareSubtitlesOptionsWithAVMediaSelectionOptions:nonForcedOptions:]`

Ce problème est le même que Zendesk #19459.

* (ZD #19574) - Le SDK TVSDK ne renvoie pas les données de réponse M3U8 pour le contenu DRM ou non DRM.

Lors du chargement initial du fichier manifeste dans PTMediaPlayerItem.prepareToPlay, en cas d’échec du chargement du manifeste, TVSDK ne signale pas le corps de la réponse d’échec à l’application.

Ce problème a été résolu en permettant à TVSDK de signaler la réponse à l’échec comme une erreur à l’application.

* (ZD n° 19615) - La logique de secours ne fonctionne pas

Dans l’implémentation actuelle, les publicités de secours ont été ignorées et n’ont pas été reconditionnées, sauf si elles sont au format m3u8. Ce problème a été résolu en ajoutant également la prise en charge du reconditionnement des annonces de secours.

* (ZD #19770) - Le kit TVSDK ne parvient pas à lire un contenu AES protégé avec une redirection 302.

Le problème de redirection a été résolu, car l’URL de redirection était effacée par cleanConnectionData avant de pouvoir être utilisée pour analyser le manifeste.

* (ZD #19856) - Les sous-titres ne s’affichent pas pour certains débits lorsqu’ils sont activés par défaut.

Ce problème a été résolu en gérant l’erreur provenant d’iOS pour les segments des flux dans lesquels les sous-titres ne s’affichent pas.

* (ZD #19868) - Le SDK TVSDK se bloque lorsqu’un élément créatif non valide est victime de trafic.

Le blocage dans TVSDK qui délocalisait incorrectement une instance de l’analyseur a été corrigé.

* (ZD #20180) - Les publicités VPAID sont parfois ignorées.

Le type MIME JavaScript n’était pas toujours inclus ou considéré comme un type MIME valide. Ce problème a été résolu en incluant JavaScript comme type MIME valide.

* (ZD #20749) - Le rapport de secours ignore les réponses VAST non vides ; Flux d’URL de suivi des publicités supplémentaires

Le problème qui empêchait certains créatifs d’être reconditionnés a été résolu.

**Version 1.4.19** (1.4.19.563) pour iOS 6.0+

* ZD #18639) - Le SDK TVSDK utilise une quantité excessive d’UC/de ressources sur un fichier d’enregistrement à chaud de longue durée.

Ce problème a été résolu en optimisant la réécriture de la liste de lecture DRM m3u8 vers les bits de mise en cache de la liste de lecture précédemment réécrits. Ceci est particulièrement pertinent lorsque vous lisez des flux m3u8 en direct pour lesquels m3u8 est téléchargé après chaque téléchargement de segment.

* (ZD#18956) - player.drmManager est nul lorsque le point d’arrêt est défini dans le lecteur de démonstration iOS

Ce problème a été résolu en mettant à jour l’implémentation de l’API PTMediaPlayer.drmManager pour récupérer DRMManager à partir de la structure DRM.

**Version 1.4.18** (1.4.18.557) pour iOS 6.0+

* (ZD #18844) Suivi du curseur de lecture pour le contenu en direct dans le lecteur iOS.

Ce problème a été résolu en permettant aux applications de définir leur propre valeur de curseur de lecture.

* (Zendesk n° 18518) - Si le nom de la vidéo n’est pas spécifié, le nom de TVSDK est défini par défaut sur * Lecteur basé sur PSDK.*

Ce problème a été résolu en supprimant la valeur par défaut du nom du lecteur.

**Version 1.4.17** (1.4.17.545) pour iOS 6.0+

* (Zendesk #2228) - Améliorer le kit TVSDK pour renvoyer la réponse JSON de la récupération d’un manifeste

Au lieu d’envoyer une erreur lorsque le contenu n’est pas M3U8, la structure DRM renvoie une valeur de données DRMetadata nulle. Le problème a été résolu en ajoutant des métadonnées pour exposer le contenu lorsque la notification M3U8_PARSER_ERROR se produit.

* (Zendesk #2231) - Erreur renvoyée en raison de la récupération du manifeste non disponible dans MediaPlayerNotification.

Même résolution que Zendesk #2228

* (Zendesk #3304) - macro VAST 3.0 `[ERRORCODE]` non renseignée

Le problème en raison duquel le SDK Auditude n’envoie pas de ping lorsque l’URL de suivi comporte des espaces au début a été résolu.

* (Zendesk #17294) - Crash SecKeyRawSign

Un blocage possible lorsque le code du client utilise la chaîne de clé a été résolu.

* (Zendesk n° 18008) - Prise en charge des cookies pour iOS8+ pour la prise en charge des flux jetés

Les flux jetés d’Akamai nécessitent l’envoi de cookies sur les demandes de segments, ce qui n’était pas possible sous iOS 7 et versions antérieures. Depuis iOS 8, Apple a ajouté une API qui permet de transmettre des cookies pour les demandes de segments. Ce support est maintenant disponible dans TVSDK . La prise en charge de l’envoi d’un agent-utilisateur a également été ajoutée, le cas échéant.

* (Zendesk #18166) - TVSDK 1.4.15 émet des centaines d’avertissements lors de la compilation avec DWARF avec les options de fichier dSYM

Tous les avertissements ont été résolus.

**Remarque**: Les bibliothèques compatibles tvOS ont été ajoutées pour TVSDK .

**Version 1.4.16** (1.4.16.1454)

* Zendesk #3875 - L’onglet S se bloque pendant la lecture

Rétablissement de la dépendance d’OKHTTP sur l’auditude pour CRS parce que TVSDK utilise maintenant directement httpurlconnection au lieu de curl. Le problème a été résolu en effaçant les exceptions avant d’effectuer un autre appel JNI.

* (Zendesk #4487) - Suivi des  linéaires de contenu

Le problème a été résolu en réinitialisant le suivi de pulsation vidéo pendant une session de lecture de flux linéaire.

* (Zendesk #17919) - Android - la recherche de contenu provoque une erreur de pulsation

Le problème était de résoudre la pulsation dans un état d’erreur en cas de recherche dans un chapitre.

* (Zendesk n° 18053) - Application utilisant le kit TVSDK se bloque sur Marshmallow

Le SDK TVSDK se bloquait sur Android M OS lorsque la bibliothèque TVSDK utilisait du code néon qui convertissait les couleurs YUV `->` RVB. Ce problème a été résolu en mettant à jour les fonctions à l’origine de ce problème à l’aide d’une version non néon de `code`.

* (Zendesk #18072) - Android M - Blocage d’application

Ce blocage survient lors de l’appel des API MediaCodecList et MediaCodecInfo lors de la vérification de la prise en charge du  et du niveau. Adobe recherche la prise en charge de Google pour obtenir des informations supplémentaires. Ce problème a été résolu en fournissant une solution temporaire en chargeant toutes les informations de codec à l’avance afin d’éviter d’appeler ces API uniquement lorsque des informations de codec sont nécessaires.

* (Zendesk #18074) - Les sous-titres arabes ne fonctionnent pas sur Nexus avec Android 6.0

Ce problème a été résolu en prenant en charge le mappage des polices CTS Android.

**Version 1.4.15** (1.4.15.512) pour iOS 6.0+

**Remarque**: Le module Nielsen a été supprimé de la version TVSDK, mais le module TVSDK sera mis à jour prochainement avec un nouveau module d’intégration Nielsen.

* (ZD #2228) - Erreur renvoyée après la récupération du manifeste non disponible dans MediaPlayerNotification.

Ajout de métadonnées pour exposer le contenu lorsque la notification M3U8_PARSER_ERROR se produit.

* (ZD #4437) - Blocages dans le SDK Adobe Primetime

Correction d’un blocage signalé lors de la préparation des sous-titres/des fichiers audio de remplacement.

* (ZD n° 4487) - Suivi du linéaire de contenu

Possibilité de réinitialiser le suivi de la pulsation vidéo pendant une session de lecture de flux linéaire.

**Version 1.4.14** (1.4.14.498) pour iOS 6.0+

* (ZD n° 17260) - Blocage sur playlistManagerForURL

Correction d’un blocage intermittent en raison de problèmes d’accès simultané.

**Version 1.4.13** (iOS 6.0+)

* (ZD #3304) - `[ERRORCODE]` Macro VAST 3.0 non renseignée

   * Le code d’erreur 400 sera affiché si la publicité intégrée comporte un élément créatif incorrect.
   * `[ERRORCODE]` sera codée en URL.

* (ZD #3865) Intégration de Heartbeat avec les annonces IMA

Correction d’un bogue en raison duquel la longueur de la vidéo était reportée incorrectement.

* Lecteur de démonstration TVSDK mis à jour pour prendre en charge iOS 9

Pour prendre correctement en charge iOS 9, vous devez configurer les exceptions de la sécurité du transport des applications. Aux fins de la démo, l&#39;ATS est complètement désactivé.

**Version 1.4.12** (1.4.12.464) pour iOS 6.0+

* (ZD #4521) CRS Test côté client et SSAI

Correction d’un MD5 inversé dans l’URL 3P.

**Version 1.4.12** (1.4.12.463) pour iOS 6.0+

* (ZD n° 2751) IFC et CS Ex / Amélioration : Gérez les éléments dynamiques dans certaines URL de fichier multimédia.

Mise à jour de Creative Repackaging Service afin de gérer correctement les publicités avec des URL de création dynamiques.

* (ZD #3654) Fuite de mémoire dans la version PSDK après la version 1.3.4.166

Correction d’une fuite de mémoire dans drmFramework avec lecture régulière sur les périphériques iOS 8.2.

* (ZD #3988) Le paramètre Preroll est ignoré lors de la recherche d’un élément de retour après la première lecture.

Correction d’un bogue afin que les stratégies publicitaires puissent être correctement désactivées.

* (ZD n° 4017) Demande à l’API iOS de forcer la lecture de la publicité à l’envers

Correctif pour ZD #4279 résolu

* (ZD #4279) Problème de redirection du kit TVSDK HLS sur iOS et le bureau

Correction d’un bogue lorsqu’un fichier d’annonce utilisait une URL de redirection relative.

**Version 1.4.9** (1.4.9.427) pour iOS 6.0+

* (ZD #3075) Problème de disponibilité Internet - iOS

Ajout d’une notification pour détecter le blocage de la lecture.

* (ZD #3193) Demande d’API de modification de  dans TVSDK

Mise à jour de PTPlaybackInformation afin d’exposer la valeur mise à jour de l’élément indiquéBitrate. Mise à jour de la notification BITRATE_CHANGE pour qu’elle soit plus fiable et plus précise en temps pour les débits signalés par le M3U8.

* (ZD #3324) Les publicités Primetime  problème lorsqu’aucun média publicitaire n’est présent dans VMAP

Prise en charge de la sonnerie des URL de suivi des coupures publicitaires vides, TVSDK vérifie désormais les  de coupures publicitaires et termine les pings pour les coupures publicitaires vides.

**Version 1.4.8** (1.4.8.402)

* (ZD n° 3158) IOS 7 se bloque lors de la réexécution complète des 

**Version 1.4.7** (1.4.7.382)

* (ZD n° 2197) Suivi des erreurs publicitaires. Échec du chargement du manifeste de la notification pour le fichier ajoutée.
* (ZD #2894) Le lecteur effectue 4 demandes de manifeste de niveau supérieur pendant la lecture.
* (ZD #2992) L&#39;Auditude  des durées et des identifiants bizarres.

**Version 1.4.6**(1.4.6.325)

* (ZD n° 2197) Suivi des erreurs publicitaires. Échec du chargement du manifeste de la notification ajoutée pour le fichier

**Version 1.4.5** (1.4.5.283)

* (ZD n° 2141) Mise en oeuvre d’Analytics pour l’application TreeHouse, ajout d’une `AdobeAnalyticsPlugin.a` bibliothèque pour créer un package.
* Mise à jour de la bibliothèque Video Heartbeats vers la version 1.4.1.2
* [PTPALY-4226] [lié au ZD n° 2423) L’exécution de la réinitialisation DRM peut entraîner la suppression des données  du d’applications.

**Version 1.4.4** (1.4.4.242)

* Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.4.1.

* (ZD #2435) La documentation du SDK TV sur les analyses nécessite des mises à jour

**Version 1.4.2** (1.4.2.210) : iOS 6.0+)

* (ZD #1129) `_player.currentItem.audioOptions` Retour vide
* (ZD #2109) Le PSDK Primetime 1.4.1.125 ne fonctionne pas avec Xcode 5.1.1
* (ZD #2137) Blocage dans le fichier PSDK sur iOS lorsque les métadonnées DRM ne peuvent pas être chargées

**Version 1.4.1**(1.4.1.125)

* (ZD #1107) CocoaLumberjack symboles 
* (ZD #1644) Modifier l’agent utilisateur iOS pour le ciblage et les 
* (ZD n° 1850) Fichiers de prise en charge de cacao inclus dans le SDK iOS
* (ZD#1908) Les balises personnalisées sont ignorées par le PSDK s’il existe plus de 1

**Version 1.4.0** (1.4.0.32)

* Zendesk #1024 - Fonction permettant de supprimer une publicité du flux via le manifeste

## Certification et prise en charge des périphériques {#device-certification-and-support}

>[!NOTE]
>
>Les fonctionnalités suivantes **ne sont pas** prises en charge dans TVSDK :
>
>* Mouvement lent, sur n’importe quelle plateforme ou version.
>* Jeu de l&#39;astuce en direct.


**Version 1.4.43**

* TVSDK 1.4.43 est certifié pour iOS 11.

**Version 1.4.29**

* TVSDK 1.4.29 a été certifié pour iOS 10.

**Version 1.4.28**

* TVSDK 1.4.28 a été certifié pour la version bêta 7 d’iOS 10.
* Prise en charge de DRM pour forcer HTTPS par l’ajout `forceHTTPS` et `isForcingHTTPS` des API.
* Mise à jour des bibliothèques VHL vers 1.5.8, des bibliothèques Adobe Mobile vers 4.8.4 et de la bibliothèque de l’utilitaire de journalisation vers le de déploiement version 7.0.

**Version 1.4.19**

Cette version de TVSDK a été certifiée avec le support FairPlay pour iOS et tvOS.

**Version 1.4.17**

* tvOS

   Cette version de TVSDK inclut la prise en charge de tvOS et a été certifiée pour les flux HLS non chiffrés.

   **Remarque**: Tenez compte des recommandations de compilation suivantes :

   * La prise en charge de TVSDK tvOs est limitée aux flux chiffrés DRM non-Adobe. Vous devez supprimer la référence à drmNativeInterface.framework dans vos paramètres de génération tvOS. Les flux chiffrés AES sont toujours pris en charge.
   * Apple exige que toutes les applications Apple TV soient activées pour le code bitmap. Vous devez donc activer cet indicateur dans les paramètres de votre projet.

## Problèmes et limites connus {#known-issues-and-limitations}

* En raison de l’obsolescence de la classe iOS UIWebView, dans iOS TVSDK 3.6 et versions ultérieures :
   * Les publicités VPAID ne seront pas lues comme prévu sur iPad 13.
   * Les publicités complémentaires ne seront pas lues comme prévu.

* Dans iOS TVSDK, toutes les publicités sont collées dans le manifeste de contenu. Les comportements publicitaires sont implémentés en effectuant des recherches en fonction de la durée du contenu et des segments de publicité. Ainsi, si les durées des segments ne sont pas précises, la recherche peut ne pas toujours se terminer à l’image exacte du début ou de la fin de la coupure publicitaire. Même si les durées correspondent au cadre, il existe une tolérance que la plate-forme elle-même impose à la recherche et il peut y avoir quelques cadres ou publicités ou du contenu affichés. Il s’agit d’une limitation de la plate-forme et de la façon dont l’insertion d’annonces fonctionne avec TVSDK sur iOS.
* La décision d’ignorer se produit sur le  de recherche dans ce cas. Cependant, puisque les durées des segments publicitaires dans le manifeste ne représentent pas exactement la durée réelle de la publicité, la recherche n’est pas précise dans le cadre. Vous voyez donc quelques cadres publicitaires lorsque les stratégies publicitaires sont appliquées.
* Il se peut que la vidéo de rotation de la licence ne soit pas lue sur iOS 11 et qu’elle soit lue correctement sur iOS 9.x et iOS 10.x.
* Dans la prise en charge de VPAID 2.0, si la lecture est active sur AirPlay, les publicités VPAID sont ignorées.
* Le fichier drmNativeInterface.framework ne se lie pas correctement lorsque la  minimale du est définie sur iOS7 (ou version ultérieure).
Solution : Spécifiez explicitement la bibliothèque libstdc++.6.dylib comme suit : Accédez à ->Build Phases->Link Binary With Libraries (Créer des phases->Lier le fichier binaire aux bibliothèques) et ajoutez libstdc++.6.dylib.
* La publicité post-roulée n&#39;est pas insérée pour l&#39;API de remplacement.
* La recherche d’une coupure publicitaire (sans en sortir) génère une  et une  de et une notification de coupure publicitaire
* La définition de currentTimeUpdateInterval n’a aucun effet.
Remarque : Dans certaines versions d’iOS, le système d’exploitation ne charge pas automatiquement les ressources dans PSDKLibrary.framework. Il est important de copier manuellement le fichier PSDKResources.bundle dans les ressources d’assemblage de l’application : Accédez à &quot;Build Phases&quot; (Créer des phases) et copiez des ressources d’assemblage.
* L’application de référence ne peut pas être créée à l’aide de Xcode 8 ou de versions inférieures. iOS TVSDK version 1.4.41 et ultérieures, utilisez Xcode 9 pour la compilation.
* Les publicités VPAID ne respectent pas la valeur delayAdLoadingTolérance.
* 24077- Pour certains contenus HLS avec sous-titres, le lecteur se bloque lors de la méthode Stop ou Reset.
* Les notifications d’erreur détaillées ne sont pas disponibles au cas où la résolution de publicités juste à temps est activée.
* Les notifications d’erreur sont enregistrées selon l’heure de résolution de l’annonce et non selon la séquence d’annonce.
* La prise en charge de HEVC présente les restrictions suivantes dans cette version
   * DRM non pris en charge
   * Prise en charge CC (CEA 608/708) non disponible, car elle n’est pas prise en charge dans le CMAF.
   * La prise en charge de 4K n’est pas encore présente.
   * Les balises ID3 ne sont pas prises en charge, car elles ne le sont pas dans CMAF.
   * Flux HEVC dynamiques non muxés non vérifiés.
   * Prise en charge des publicités HEVC non vérifiée.
* Si JIT est activé et que la tolérance est définie sur 10 secondes, aucun appel VAST n’est vu pour la première coupure publicitaire intermédiaire dans le cas des publicités de redirection VMAP->VAST.
* Pour que le délai d’expiration de la résolution de la publicité fonctionne correctement, chaque fois que la liste de lecture est mise à jour pendant la lecture en flux continu en direct, le lecteur attend une liste de lecture raccordée dans les 20 secondes. S’il ne reçoit pas de liste de lecture cousue dans ledit intervalle, une erreur interne est générée et le lecteur s’arrête.

## Ressources utiles {#helpful-resources}

* [Guide du programmeur TVSDK 3.4 pour iOS](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-for-ios/introduction/ios-3x-overview.html)
* [Référence de l’API TVSDK iOS 3.4](https://help.adobe.com/en_US/primetime/api/psdk/appledoc_v34/index.html)
* Reportez-vous à la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.
