---
title: Notes de mise à jour de TVSDK 1.4 pour Desktop HLS
description: Les notes de mise à jour TVSDK pour Desktop HLS décrivent les nouveautés ou les modifications, les problèmes résolus et connus dans TVSDK DHLS.
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
exl-id: 5e227c99-acf6-4b16-a35a-68e2928fdbfd
source-git-commit: 1bc2f6c230c262babf2958c32fee31afcad04c2f
workflow-type: tm+mt
source-wordcount: '5194'
ht-degree: 0%

---

# Notes de mise à jour de TVSDK 1.4 pour Desktop HLS {#tvsdk-for-desktop-hls-release-notes}

Les notes de mise à jour TVSDK for Desktop HLS décrivent les nouveautés ou les modifications, les problèmes résolus et les problèmes connus de TVSDK DHLS.

## Nouvelles fonctionnalités {#new-features}

**1.4.31**

* **Prise en charge multi-CDN pour les annonces CRS**

   * Par défaut, toutes les ressources transcodées seront hébergées sur le réseau de diffusion de contenu détenu par l’Adobe sur Akamai. Avec la dernière version, Adobe Creative Repackaging Service (CRS) permet de charger les créatifs transcodés sur plusieurs CDN, comme spécifié par le client.
   * De nouvelles API sont ajoutées à TVSDK pour activer la spécification de l’URL créative CRS finale lorsque l’URL par défaut n’est pas utilisée. Reportez-vous à la documentation pour savoir comment utiliser ces nouvelles API.

### Nouvelles fonctionnalités des versions précédentes {#new-features-previous}

**1.4.30**

* **Mesures de facturation**

Pour tenir compte des clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte les mesures d’utilisation et les utilise pour déterminer le montant de facturation des clients.

**1.4.24**

* **Connexion réseau persistante**

Important : Vous devez avoir installé au moins Adobe Flash Player version 22 ou ultérieure.
Les connexions réseau persistantes créent et stockent une liste interne de connexions réseau qui peuvent être réutilisées pour plusieurs requêtes, au lieu d’ouvrir une nouvelle connexion pour chaque requête réseau. Les connexions réseau persistantes doivent augmenter l’efficacité et réduire la latence de votre code réseau.

Dans cette version, cette fonctionnalité n’est pas prise en charge dans Apple Safari et Mozilla Firefox sur Mac.

**1.4.19**

* Prise en charge de l’intégrité des diffusions pour les publicités VPAID.
* Activation de l’option de tabulation silencieuse dans le lecteur Flash FP 20.0.0.267 pour Firefox 42 et versions ultérieures en corrigeant le problème de blocage.

**1.4.18**

* Primetime Desktop HLS TVSDK prend désormais en charge les créations de SWF linéaires VPAID 2.0 pour permettre une expérience de publicité interactive riche en flux continu.

**1.4.10**

* **Secours de la publicité, enchaînement des publicités dans la logique de sélection des publicités (Zendesk #3103)** Pour les publicités VAST (créatives) avec la règle de secours activée, TVSDK traite une publicité avec un type MIME non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.

Pour plus d’informations, voir [Reprise de publicité pour les publicités VAST et VMAP](../programming/tvsdk-1.4-for-android/ad-insertion/ad-fallback/android-1.4-ad-fallback.md).

**1.4.8**

* **Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.5**

   * Possibilité d’envoyer des métadonnées avec le démarrage de la vidéo et/ou vidéo/ad/chapitre en tant que données contextuelles
   * Moins de trafic réseau : les pulsations sont moins nombreuses en moyenne et de taille inférieure.

**1.4.7**

* **Prise en charge de l’individualisation sur site**

Prise en charge des installations on-premise du serveur d’individualisation Adobe pour personnaliser la demande d’individualisation du client afin d’accéder à un autre point de terminaison.

**1.4.6**

* **Exemple de chiffrement AES (nécessite la version 17.0.0.134 du Flash Player)**

Le chiffrement AES basé sur des exemples est désormais pris en charge.

**1.4.2**

* **Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.4.0.1**

   * Ajout de la possibilité de regrouper différents cas d’utilisation d’analyse, à partir d’autres SDK ou lecteurs, avec les composants vidéo essentiels d’Adobe Analytics.
   * Le suivi des publicités a été optimisé en supprimant les méthodes trackAdBreakStart et trackAdBreakComplete . La coupure publicitaire est déduite des appels des méthodes trackAdStart et trackAdComplete .
   * La propriété playhead n’est plus nécessaire lors du suivi des publicités.

**1.4.0**

* **Signalisation par blackout avec remplacement de contenu alternatif** Dans le cadre de la mise à jour de la version 1.4 de TVSDK, TVSDK prend également en charge l’entrée et le retour de pannes régionales de contenu linéaire. TVSDK peut désormais traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d’interruption même lorsque des programmes alternatifs sont affichés à la place de la programmation d’origine.

* **Supprimer/Remplacer des publicités C3** Désormais, aucun travail de préparation supplémentaire n’est nécessaire pour insérer dynamiquement de nouvelles publicités dans les ressources vidéo à la demande (VOD) qui sortent de la fenêtre C3. TVSDK fournit désormais une API pour supprimer des plages de contenu personnalisées et insérer dynamiquement de nouvelles publicités. Cette nouvelle fonctionnalité puissante est également utile dans les cas où le contenu en direct/linéaire est diffusé pendant la diffusion et est immédiatement retiré pour être utilisé comme contenu à la demande sans temps approprié pour &quot;nettoyer&quot; la ressource.

## Problèmes résolus {#resolved-issues}

>[!NOTE]
>
>Tous les clients TVSDK qui utilisent CRS sont fortement encouragés à effectuer la mise à niveau vers au moins TVSDK 1.4.32 sur iOS, Android et Desktop HLS. Cette mise à niveau remplacera la mise en oeuvre de l’application existante. Après la mise à niveau, recherchez les demandes d’URL de création CRS dans un outil de proxy (Charles, par exemple) pour vérifier que la version du chemin d’accès reflète la version 3.1. Par exemple,
>
>`https://adunit.cdn.auditude.com/assets/3p/v3.1/218747/94b/c1b/94bc1b964cc67e115a5a6781c7329b90_ee92607938ffff46b083121f044c2746.m3u8`

**Version 1.4.41**

* Zendesk #33777 - SWF de jeton Localhost pour le build de distribution DHLS expiré.

  Mise à jour du jeton localhost pour la démonstration PMP sur DHLS.

### Problèmes résolus dans les versions précédentes {#resolved-issues-previous}

**Version 1.4.38** (891)

* Zendesk #30731 - TVSDK ne lit pas plusieurs publicités VPAID dans un AdBreak.

  Correction de la lecture de plusieurs publicités VPAID dans un AdBreak.

* Zendesk #29968 - Double Panneau.

  Le lecteur vidéo peut répéter le dernier segment d’une période au cours de laquelle un commutateur ABR se produit. En raison de cela, parfois, le dernier segment de pré-lecture a été répété. Ce problème a été corrigé.

**Version 1.4.35** (879)

* Zendesk #26058 - Prend en charge les événements VPAID natifs

**Version 1.4.3** (873)

* Zendesk #21701 - Envoyez l’URL de création d’origine pour la demande CRS 1401 au lieu de l’URL normalisée.

  Le problème en raison duquel les URL déjà reconditionnées sont demandées pour le transcodage a été corrigé, conformément aux exigences du serveur principal CRS.
* Zendesk #26197 - Compression anamorphique non lue dans la résolution d’affichage souhaitée.

  **Remarque**: Ce problème nécessite le lecteur Flash 24.0.0.194 ou version ultérieure.

  Correction du problème en raison duquel les entrées manquantes dans les tableaux de proportions étaient utilisées pour calculer la largeur de sortie.

* Zendesk #26840 - Échec de la détection HDCP sur IE11 + Windows7 après la deuxième tentative.

  **Remarque**: Ce problème nécessite le lecteur Flash 24.0.0.218 ou version ultérieure.

  Ce problème a été résolu en modifiant le traitement de la file d’attente des messages principale d’AdobeCP pour itérer dans toute la file d’attente, au lieu de simplement bloquer le tout premier message.

* Zendesk #27460 - Le nouveau compte Akamai ne peut pas gérer une requête CDN de POST.

  Le nouveau compte CDN ne peut pas gérer une requête CDN de POST. Ce problème a été résolu en mettant à jour le code afin que la demande d’annonce cdn.auditude.com soit GET au lieu de POST.
* Zendesk #27619 - Flash crash sous Windows 10

  **Remarque**: Ce problème nécessite le lecteur Flash 24.0.0.218 ou version ultérieure.

  Ce problème a été résolu en empêchant un problème en raison de longues URL.

* Zendesk #28218 - L’événement de suivi ne se déclenche pas lorsque l’enregistrement se fait à partir du point de reprise

  Ce problème est le même que dans Zendesk #26592. Correction du problème en raison duquel les opérations de recherche étaient autorisées lorsque le lecteur multimédia était à l’état PRÉPARÉ pour les diffusions VOD.

**Version 1.4.32** (867)

* Zendesk #26592 L’événement de suivi ne se déclenche pas lorsque la lecture commence à partir du point de reprise

Le code ne mettait pas à jour l’élément de coupure publicitaire preroll lorsque le point de reprise n’était pas nul. Ce problème a été résolu en ajoutant une logique pour actualiser le code lorsque les heures de début de la plage ne correspondent pas.

* Zendesk #27022 Les publicités ne sont pas lues la deuxième fois qu’une ressource est lue

Les exceptions avec les méthodes de tableau ont été corrigées.

**Version 1.4.30** (855)

Les problèmes suivants ont été résolus pour TVSDK dans cette version :

* Zendesk #22898 - Les sous-titres manquants ne doivent pas entraîner l’échec de la lecture.

**Remarque**: Ce problème nécessite le lecteur Flash 23.0.0.185 ou version ultérieure.

Ce problème a été résolu en permettant à TVSDK de continuer la lecture, même si le manifeste ne contient pas le WebVTT M3U8, et en enregistrant simplement un avertissement.

* Zendesk #23454 - Les annonces tierces (VPAID) ne sont pas correctement gérées

Ce problème a été résolu en gérant correctement les publicités VPAID en fonction des identifiants de contenu plutôt que des périodes.

* Zendesk #24528 - Mesures d’utilisation de TVSDK pour la facturation.

Important : Ce problème nécessite le lecteur Flash 23.0.0.185 ou version ultérieure.

* Problème Zendesk # 25432 Closed Caption (Sous-titrage codé) lors du redimensionnement du lecteur.

Important : Ce problème nécessite le lecteur Flash 23.0.0.185 ou version ultérieure.

Le code de la carte de texture de l’affichage de la légende a été corrigé afin de gérer correctement les coordonnées lors du redimensionnement du lecteur.

La bibliothèque Video Heartbeat (VHL) a été mise à jour vers la version 1.5.9 afin de résoudre les problèmes suivants :

* Zendesk #23730 - Les mesures de débit sont vides

Ce problème a été résolu en suivant les changements de débit dans VideoAnalyticsTracker.

* Ajout d’une nouvelle API, assetDuration, à PTVideoAnalyticsTrackingMetadata afin de mettre à jour la durée des ressources pour les flux en direct/linéaire.

**Version 1.4.28** (848)

* Zendesk #25027 - Auditude ne fonctionne pas dans la version de bureau 1.4.27

Ce problème a été résolu en ajoutant le code pour vérifier l’AUDITUDE_METADATA_KEY et en rendant les variables AUDITUDE_METADATA_KEY et ADVERTISING_METADATA_KEY interchangeables.

* Zendesk #24428 - Problème de mise en mémoire tampon fréquent lors de l’utilisation de TVSDK pour lire un DRM HLS

Ce problème a été résolu en tenant compte du fait que lorsqu’il n’y a aucune configuration de publicité, TVSDK peut accélérer le traitement en éliminant la rétention de publicité preroll et la rétention de réservation en direct sur la chronologie conçue pour synchroniser l’insertion de publicités.

* Zendesk #24344 - Désactivez les fichiers WebVTT pour améliorer les temps de démarrage.

**Remarque**: Ce problème nécessite le lecteur Flash 23 ou une version ultérieure.

Ce problème a été résolu en chargeant les fichiers WebVTT uniquement lorsque des sous-titres doivent être affichés.

* Zendesk #24994 - Le sous-titrage codé est retiré du lecteur lors du retour d’une coupure commerciale.

**Remarque**: Ce problème nécessite le lecteur Flash 23 ou une version ultérieure.

Le mauvais code EOC a fait disparaître l’affichage de la légende. Ce problème a été résolu en forçant les codes de sous-titres 608 RU2, RU3 et RU4 à fournir la bonne visibilité dans la principale fenêtre actuelle.

**Version 1.4.27** (844)

* Zendesk #21554 - Balises d’erreur TVSDK non déclenchées pour application-type = video/mp4

Ce problème a été résolu en permettant à TVSDK d’envoyer un ping aux URL de suivi des erreurs correctes sur les formats de ressources non valides.

* Zendesk #23402 - Lecture de publicité incomplète

**Remarque**: Ce problème nécessite le lecteur Flash 23 ou une version ultérieure.

Une erreur 404 peut se produire après l’obtention de certaines requêtes. Ce problème a été résolu en s’assurant que la connexion ne s’arrête pas pendant la gestion de la réponse. La résolution garantit que les fichiers de publicité VPAID ne sont pas comptabilisés incorrectement. Ils ne sont donc pas publiés lorsqu’ils sont en cours de téléchargement.

* Zendesk #23621 - La reprise échoue sur les versions 400 et 404

**Remarque**: Ce problème nécessite le lecteur Flash 23 ou une version ultérieure.

Correction d’un problème qui entraînait une corruption des métadonnées DRM lors du basculement entre différents profils.

* Zendesk #23705 - Blocage des publicités vidéo pendant les coupures AdStitched

**Remarque**: Ce problème nécessite le lecteur Flash 23 ou une version ultérieure.

Ce problème est le même que dans Zendesk #23621.

* Zendesk #23905 - Certaines coupures publicitaires ignorent les coupures publicitaires

**Remarque**: Ce problème nécessite le lecteur Flash 23 ou une version ultérieure.

Le code réseau natif Windows a été corrigé afin de s’assurer que les connexions ne ferment pas les poignées utilisées actuellement par d’autres connexions.

* Ticket #24029 - HLS Les flux de FER ne lisent pas toutes les publicités mid-roll dans le fichier mid-roll .json.

Ce problème a été résolu en permettant aux clients de définir des paramètres personnalisés séparément sur l’instance Opportunity afin que les clients n’aient pas à remplacer OpportunityGenerator.

**Version 1.4.26** (839)

* Zendesk #18854 - Mettre à jour la logique de sélection créative en fonction des règles CRS
   * Prise en charge de la mise à jour de la logique de sélection créative en fonction des règles CRS.

* Zendesk #22725 - mise en oeuvre de playbackManager.beginPlayback() dans l’exemple d’application pour bureau

   * Corrigé en supprimant cet appel redondant à la fin de startPlaybackFromFlashVars lorsque la méthode est appelée à partir de setupVideo()

* Zendesk #22807 - Exception de référence nulle SearchManager

   * Corrigé en fournissant la protection de pointeur NULL nécessaire à l’intérieur de SeekManager relative à _dispatcher

* Zendesk #22822 : mise en mémoire tampon fréquente lors de l’utilisation de TVSDK pour lire un HLS clair

   * Corrigé en supprimant l’opportunité initiale générée par adSignalingModeOpportunityGenerator en l’absence de publicité

* Zendesk #23378 - L’intégrité du flux bloque le fichier rules.xml

   * Corrigé en chargeant le fichier rules.xml par le biais du workflow d’intégrité du flux.

**Version 1.4.24** (817)

* Zendesk #19851 - Lorsque le lecteur s’adapte à un débit différent, il retourne quelques images dans le temps sur le nouveau débit, ce qui rend l’expérience maladroite.

**Remarque**: Ce problème nécessite le lecteur Flash 22.0.0.175 ou version ultérieure.

Le problème en raison duquel l’adaptateur DRM est réinitialisé après le téléchargement d’une petite partie d’un segment n’est pas restauré correctement a été résolu.

* Zendesk #20784 - Analytics : Déclenchement du contenu terminé pour les transitions vidéo en direct

Ce problème a été résolu en ajoutant une API (trackVideoComplete) pour déclencher manuellement la fin du contenu au cours d’une session de suivi vidéo LINEAR/LIVE.

Les bibliothèques suivantes ont été mises à jour :

* Zendesk #21643 - Les publicités VPAID ne sont pas lues en intégralité

   * Bibliothèque AdobeMobile vers 4.10.0
   * Bibliothèque VHL vers 1.5.6
   * Bibliothèque VHL-Nielsen vers la version 1.6.7

Ce problème a été résolu en utilisant une fenêtre d’affichage à zéro hauteur pour remplir l’étape lors de la lecture d’une publicité VPAID.

* Zendesk #22110 - Analytics : Ajouter un h:sc:champ ssl aux appels de suivi de pulsation

Les problèmes liés au protocole SSL ont été résolus et la bibliothèque VHL utilisée dans TVSDK a été mise à jour vers la dernière version.

* Zendesk #22608 - La vidéo affiche un écran noir par intermittence (nécessite le Flash Player 22.0.0.175 ou une version ultérieure)

Lors d’un débit adaptatif, avec la limite de débit maximal, le rechargement de la vidéo affiche par intermittence un écran noir, même si le client voit des mises à jour de la position, et que le client se comporte comme s’il lisait du contenu.

**Version 1.4.23** (809)

* Zendesk #2887 - Problème de saut de publicité post-roll lorsque la logique de règle de publicité est appliquée à TVSDK

**Remarque**: Ce problème nécessite le lecteur Flash 21.0.0.240 ou version ultérieure.

Correction du problème en raison duquel les publicités post-roll étaient ignorées lorsque la logique de règle publicitaire était appliquée à TVSDK.

* Zendesk #19863 - Annonce avec fichier multimédia VPAID ignoré

Si une vaste publicité intégrée comporte plusieurs fichiers multimédias avec une publicité VPAID comme première publicité, la publicité intégrée n’est pas lue pour les diffusions en direct. Ce problème a été résolu en sélectionnant un autre fichier multimédia à la place.

* Zendesk #21021 : liaison tardive de l’audio entraînant la répétition de segments audio

**Remarque**: Ce problème nécessite le lecteur Flash 21.0.0.240 ou version ultérieure.

Le problème de répétition audio a été corrigé.

* Zendesk #21125 - Retour d’une coupure publicitaire linéaire/en direct

**Remarque**: Ce problème nécessite le lecteur Flash 21.0.0.240 ou version ultérieure.

Cette version prend en charge le retour d’une coupure publicitaire tôt avant la fin de la coupure publicitaire. Un retour anticipé est indiqué par le biais d’une balise de manifeste personnalisée.

* Zendesk # 21369 La liaison tardive du son provoque une incohérence

**Remarque**: Ce problème nécessite le lecteur Flash 21.0.0.240 ou version ultérieure.

Le problème de répétition audio qui a été corrigé a également corrigé ce problème.

* Zendesk #21760, 20921 - Audio Video Desync on Seek.

**Remarque**: Ce problème nécessite le lecteur Flash 21.0.0.240 ou version ultérieure.

Le problème de répétition audio a été corrigé.

* Zendesk #22024 - Erreur lors de l’exécution de TVSDK

Correction du problème en raison duquel le lecteur de référence ne lisait aucun flux et renvoyait une exception au démarrage.

**Version 1.4.22** (791)

* Zendesk #17580 - Erreur d’exécution Primetime avec le code 3357

**Remarque**: Ce problème nécessite le lecteur Flash 21.0.0.197 ou version ultérieure.

Les erreurs 3357 aléatoires qui se sont produites lors de l’initialisation correcte de deviceID lors de l’appel de storeVoucher() ont été corrigées.

* Zendesk #21334 - valeur du délai d’expiration de la demande de publicité TVSDK pour les requêtes de publicité tierces

Dans cette version, le délai d’attente global des demandes d’annonces a été ajouté.

**Version 1.4.21** (782)

* Zendesk #19580 TVSDK attend la fin du résolveur de contenu avant d’envoyer `PTTimedMetadataChangedNotification` notifications

**Remarque**: Ce problème nécessite le lecteur Flash 21.0.0.182 ou version ultérieure.

Ce problème a été résolu dans le lecteur de référence du bureau en permettant de définir des balises d’annonce et en ajoutant un générateur d’opportunités personnalisé qui indique comment s’abonner à des repères personnalisés et comment traiter ces signaux dans un fichier VOD.

* Zendesk #20806 Les futures publicités mid-roll dans la fenêtre de réalité numérique ne se déclencheront pas après la permutation de caméras

**Remarque**: Ce problème nécessite le lecteur Flash 21.0.0.182 ou version ultérieure.

Ce problème a été résolu en mettant à jour l’application pour définir _resource.metadata.setValue(DefaultMetadataKeys.ENABLE_LIVE_PREROLL, &quot;false&quot;) pour désactiver l’insertion de publicités preroll dans un échange PIP et, par conséquent, aucune opportunité de preroll n’est générée.

Une fonctionnalité de tri a été introduite pour corriger le placement d’annonce hors séquence qui a entraîné une durée de contenu principal négative.

* Zendesk #20522 : Impossible d’ignorer les publicités VPAID 2.0

**Remarque**: Ce problème nécessite le lecteur Flash 21.0.0.182 ou version ultérieure.

* Ce problème a été résolu en ignorant les publicités VPAID lors de l’annulation de la publicité.
* Lorsque la stratégie de coupure publicitaire est définie sur saut, les événements de coupure publicitaire et de coupure publicitaire sont toujours distribués. L’état du lecteur est incohérent.

Ce problème a été résolu afin de se comporter correctement et de ne pas distribuer d’événements lorsque la coupure publicitaire est ignorée.

* Zendesk #20955 Définir des paires clé-valeur dans la propriété customParameters via le générateur d’opportunités

**Remarque**: Ce problème nécessite le lecteur Flash 21.0.0.182 ou version ultérieure.

La requête Auditude analyse les paramètres Auditude pour les paramètres personnalisés lors de la création d’une unité publicitaire pour les requêtes publicitaires.

Ce comportement a été modifié afin d’inclure des paramètres personnalisés de l’objet Opportunity dans la requête. En outre, plusieurs opportunités avec différents paramètres personnalisés ne peuvent pas être incluses dans une requête Auditude.

* Zendesk #21227 - m3u8 ne joue pas de manière cohérente

**Remarque**: Ce problème nécessite le lecteur Flash 21.0.0.211 ou version ultérieure.

Ce problème a été résolu en permettant à TVSDK d’ignorer le manifeste (sous-profils HLS) contenant le codec AC3 que le TVSDK ne prend pas en charge (entouré).

**Version 1.4.20** (762)

* Zendesk #19181 - Les trompes jouent vite en avant pour verrouiller le flux en direct.

**Remarque**: Ce problème nécessite le lecteur Flash 20.0.0.306 ou version ultérieure.

* Zendesk #19286 - Un crash du Flash Player s&#39;est produit lors de la recherche en avant et en arrière dans un flux FER.

**Remarque**: Ce problème nécessite le lecteur Flash 20.0.0.306 ou version ultérieure.

Les blocages occasionnels qui se produisaient lors de la recherche dans Google Chrome ont été résolus en arrêtant les requêtes, si les requêtes prennent trop de temps pour obtenir une réponse ou si le socket est en cours d’arrêt.

* Zendesk #19305 - Lecture agitée rencontrée lors de la lecture d’un flux avec des discontinuités A/V.

**Remarque**: Ce problème nécessite le lecteur Flash 20.0.0.306 ou version ultérieure.

Ce problème a été résolu en signalant un avertissement.

* Zendesk # 19359 - Le Flash Player s&#39;est écrasé à cause de la position de #EXT-X-FAXS-CM : dans le manifeste de niveau défini.

Ce problème a été résolu lorsque la balise #EXT-X-FAXS-CM apparaît dans la liste de lecture supérieure avant un débit ou des segments individuels dans la liste de lecture.

* Zendesk #19489 - Module externe Quick Forward to Live Point Stalls (flux en direct)

Ce problème est le même que Zendesk #19181.

* Zendesk #19699 - TVSDK ne parvient pas à passer d’une piste de sous-titre WebVTT à l’autre.

Ce problème a été résolu en faisant le vidage du lecteur et en rechargeant le manifeste lorsqu’un suivi change et en corrigeant le problème de conversion de chaîne UTF8 qui affectait les noms de suivi des sous-titres WebVTT sur deux octets.

**Version 1.4.19** (1.4.19.738)

* Zendesk #18234 - Flash Player bloque la lecture des diffusions avec des chaînes Unicode en CC

Ce problème nécessite le Flash Player FP 20.0.0.267 ou version ultérieure et a été résolu en gérant correctement la chaîne Unicode.

* Zendesk #18304 - Prise en charge de l’intégrité des diffusions pour les publicités VPAID

Cette fonctionnalité nécessite le Flash Player FP 20.0.0.267 ou version ultérieure et a été introduite dans la version 1.4.19.

* Zendesk #18766 - Le lecteur de référence ne peut pas afficher les caractères unicode non latins dans les noms de suivi CC

Cette fonctionnalité nécessite le Flash Player FP 20.0.0.267 ou version ultérieure et a été corrigée en gérant correctement la chaîne Unicode.

* Zendesk #18804 - Panne de lecteur dans Firefox 42

Ce problème nécessite le Flash Player FP 20.0.0.235 ou une version ultérieure et est le même que Zendesk #18723.

* Zendesk #18864 - Flash Player du blocage complet des modules externes

Ce problème nécessite le Flash Player FP 20.0.0.235 ou version ultérieure et est identique à Zendesk #18723.

* Zendesk #18998 - Si les horodatages audio et vidéo ne correspondent pas, un téléchargement sans fin de segments en cas de discontinuité s’est produit.

Ce problème a été résolu en ignorant l’écart entre les horodatages et en lisant simplement le contenu téléchargé.

* Zendesk #19093 - Les publicités mid-roll ne peuvent être visionnées qu’une seule fois avec du contenu de relecture en direct et en événement complet (FER), mais ces publicités n’ont pas pu être visionnées à nouveau lors du transfert rapide ou de la recherche au-delà des publicités.

Dans le sélecteur de stratégie publicitaire par défaut de Primetime, si une publicité mid-roll est visionnée, la coupure publicitaire n’est pas déplacée à la position recherchée lorsque vous effectuez une recherche. Pour lire à nouveau la publicité, après la recherche, l’application doit remplacer la fonction selectAdBreaksToPlay() .

* Zendesk #19101 - Le retour dans les publicités mid-roll non résolues supprime l’emplacement de la publicité.

Ce problème a été résolu en permettant au lecteur de mettre à jour l’heure playbackMetrics, la valeur minimumOpportunityTime et la chronologie.

* Zendesk #19102 - Problèmes avec le mode FER et astuce

Ce problème nécessite le Flash Player FP 20.0.0.267 ou version ultérieure et a été résolu en définissant correctement advertisingMetadata.adSignalingMode.

* Zendesk #19175 - Parfois, les publicités preroll ne s’affichent pas la première fois que le flux est lu.

Ce problème a été résolu en ajoutant une nouvelle API, adRequestTimeout, aux paramètres AuditudeSettings pour un délai d’attente de requête de publicité. Les utilisateurs peuvent désormais remplacer le délai d’expiration de la requête de publicité des 10 s par défaut.

**Version 1.4.18** (1.4.18.722)

* Zendesk #3324 - La création de rapports de publicités Primetime ne permet pas de suivre les coupures publicitaires lorsqu’il n’y a aucun média publicitaire dans un VMAP.

Lorsqu’une coupure publicitaire est vide, les événements de début et de fin de coupure publicitaire n’étaient pas en cours de ping. Ce problème a été résolu en envoyant des pings de démarrage de coupure publicitaire pour les coupures publicitaires vides, comme VMAP AdBreak, avec un noeud AdSource valide.

**Version 1.4.17** (1.4.17.702)

* Zendesk #17168 - Les sous-titres n&#39;apparaissent pas pendant environ 10 secondes après avoir basculé de la visibilité

Ce problème a été résolu en fournissant la prise en charge de la balise EXT-X-MEDIA-TIME pour les fichiers de sous-titres vtt.

* Zendesk #17983 - Le fait de ne pas télécharger de clés pour un manifeste entraîne l’échec de la lecture du manifeste.

**Remarque**: Vous devez avoir au moins Flash Player FP 19.0.0.245 ou version ultérieure.

Lors de la lecture de contenu en direct, il se peut que le manifeste contienne des clés non valides (par exemple, pour les périodes de blackout), mais d’autres périodes peuvent avoir des clés valides et seront toujours lues. Auparavant, lorsqu’une clé répertoriée dans un manifeste ne pouvait pas être téléchargée, l’intégralité du manifeste échouait. Désormais, le manifeste échoue uniquement lorsque toutes les clés répertoriées ne peuvent pas être téléchargées. Si certaines clés sont valides, mais que certaines de ces clés n’ont pas pu être téléchargées, le contenu est lu. Nous échouerons toujours si nous tentons de jouer un segment qui nécessite une clé que nous n’avons pas.

* Zendesk #18554 - Réglage de l’intégrité des diffusions pour réduire les cookies dans certains cas

**Remarque**: Vous devez avoir au moins Flash Player FP 19.0.0.245 ou version ultérieure.

Correction d’un bogue dans le code de manipulation de cookies qui tronquait les valeurs des cookies.

**Version 1.4.16** (1.4.16.684)

* Zendesk #3732 - Ajout de la prise en charge des proxys dans Chrome pour l’intégrité des flux (nécessite Flash Player FP 19.0.0.207 ou version ultérieure)

Il s’agit d’une amélioration.

* Zendesk #4244 - Problèmes de diffusion au survol PTS

Ce problème a été résolu en détectant le survol et en gérant la discontinuité par type de charge utile et non de manière générique.

* Zendesk #4487 - Tracking du canal linéaire de contenu

Ce problème a été résolu en réinitialisant le suivi de pulsation vidéo au cours d’une session de lecture de flux linéaire.

* Zendesk #17427 - Adobe de l’intégrité des flux ne fonctionne pas par le biais d’un proxy sur Chrome (Win7) ()

**Remarque**: La résolution nécessite le Flash Player FP 19.0.0.207 ou version ultérieure.

Ce problème est le même que Zendesk #3732.

* Zendesk #17907 - Poignée sur Live Stream pHLS avec Flash Player 19

**Remarque**: La résolution nécessite le Flash Player FP 19.0.0.207 ou version ultérieure.

Ce problème a été résolu en gérant les flux en direct où les domaines des fichiers TS changent lors du rechargement du manifeste en direct, et les fichiers ont été téléchargés deux fois.

* Zendesk #17931 - La lecture du contenu HLS avec ardoise au début échoue

**Remarque**: La résolution nécessite le Flash Player FP 19.0.0.207 ou version ultérieure.

Le problème a été résolu en gérant les diffusions sans audio dans les 2 premières secondes du premier fichier TS.

* Zendesk #17934 - Échec de la diffusion en continu en direct avec Flash 19.0.0.185

**Remarque**: La résolution nécessite le Flash Player FP 19.0.0.207 ou version ultérieure.

Le problème a été résolu en gérant les diffusions en direct avec le temps qui s’écoule entre les images audio et vidéo sur les limites des segments.

* Zendesk #17973 - Dernier Flash Player 19.0.0.185 se bloque pendant le mid-roll

**Remarque**: La résolution nécessite le Flash Player FP 19.0.0.207 ou version ultérieure.

Le problème a été résolu en gérant le contenu audio non muet avec l’insertion de publicités mid-roll. (Le changement d’analyseur se produit, et à tout moment de la lecture, le contenu passe à la publicité mid-roll, au milieu de la lecture de la publicité, etc.)

* Zendesk #18049 - crash du Flash 19 avec Firefox 42 bêta

Ce problème est le même que Zendesk #17973.

**Version 1.4.15** (1.4.15.678)

* Zendesk #4377 : Déclenchez l’événement AD_BREAK_SKIPPED lorsque vous ignorez une coupure publicitaire en raison de la stratégie publicitaire.

Le correctif consistait à ajouter AD_BREAK_SKIPPED si une publicité est ignorée.

* Zendesk #4496 - Stream Integrate : Erreur 102100 avec redirections vers les diffusions segmentées en unités.

Le correctif consistait à ajouter la prise en charge de la définition de la propriété AVNetworkConfiguration useCookieHeaderForAllRequests via TVSDK.

* Zendesk #17179 - Le lecteur Flash se bloque sur plusieurs modifications SAP pour le contenu chiffré.

Correction d’un blocage lors de la lecture de certains contenus chiffrés.

**Remarque**: Le correctif nécessite le Flash Player 19.0.0.200 ou version ultérieure.

* Zendesk #17499 - Comment ne pas supprimer les midrolls après la montre mais supprimer la pré-lecture du contenu férié

Ajout d’un type à AdBreakTimelineItem (AdBreakTimelineItem.placementType) afin qu’AdPolicySelector puisse renvoyer une stratégie différente pour le contenu preroll, mid-roll et post-roll.

* Zendesk #17665 - Limitation de la bande passante

Le correctif consistait à supprimer la logique pour modifier la taille de la mémoire tampon cible en taille de mémoire tampon initiale au début de la mise en mémoire tampon.

**Version 1.14.14** (1.4.14.771)

* Zendesk #17363 - Fix README documentation pour le lecteur de référence

   * Clarifiez les instructions de téléchargement et d’installation de playerglobal.swc.
   * Ajoutez des instructions pour la mise à jour de la configuration du projet avec une version spécifique du lecteur Flash.
   * Mettez à jour la configuration du projet AdvertisingOverlay pour utiliser la version minimale du lecteur.
   * Mettez à jour la configuration du projet ReferenceCore pour utiliser la version 11.9 du lecteur spécifique.

* Zendesk #17471 - Le libre du lecteur

Correction partielle d’un problème en raison duquel une publicité n’est pas lue depuis le début après la recherche.

* Zendesk #17496 - Podbuster n’est pas résolu lors d’une recherche en amont dans la fenêtre de l’enregistreur numérique.

Spécifiez des paramètres personnalisés pour chaque coupure publicitaire.

**Version 1.4.13** (1.4.13.660)

* Zendesk #4037 - Aucune erreur de profil utile (nécessite le Flash Player 18.0.0.232 ou une version ultérieure)

correction du problème d’analyse de l’url lorsque le paramètre de requête contient &quot;http&quot;

* Zendesk #4260 - Flash Player 18 se bloque dans IE11 (nécessite Flash Player 18.0.0.232 ou supérieur)

Correction d’un blocage lors de la lecture d’une vidéo en mode plein écran avec IE11.

* Zendesk #4262 - Le lecteur Adobe Primetime se bloque sous Windows 10 (nécessite le Flash Player 18.0.0.232 ou version ultérieure)

Correction d’un blocage lors de la lecture d’une vidéo en mode plein écran avec FireFox sous Windows.

* Zendesk #4279 - insertion de publicités HLS TVSDK -302 problème de redirection sur iOS et Desktop

Correction d’un problème en raison duquel une URL n’était pas correctement reconnue car son type n’avait pas d’extension.

* Zendesk #4306 : blocage du Flash Player lors du passage en plein écran sous Windows uniquement (nécessite le Flash Player 18.0.0.232 ou supérieur)

Correction d’un blocage lors de la lecture d’une vidéo en mode plein écran sous Windows.

* Zendesk #4480 - Événements de balise ID3 manquants (nécessite Flash Player 18.0.0.232 ou supérieur)

**1.4.12 **(1.4.12.656)

* Zendesk #2751 - CSAI et CRS | Amélioration : Gérez les éléments dynamiques dans certaines URL de fichier multimédia.

Mise à jour de Creative Repackaging Service pour gérer correctement les annonces avec des URL de création dynamiques.

* PTPLAY - 2114 - Prise en charge de la lecture MP4.

La lecture de base du contenu MP4 est désormais prise en charge, y compris la lecture, la mise en pause et la recherche.

Les Flashs Player suivants requièrent la version 18.0.0.225 ou supérieure de :

* Zendesk #3992 - Vitesses TrickPlay supplémentaires.

TrickPlay accepte désormais des taux supérieurs à 16x : +/- 32, +/-64 et +/-128.

* Zendesk #3113 - Flash Player du blocage des modules externes

Correction d’un blocage lors de la tentative de lecture d’une publicité de redirection sur Mac Firefox.

* Zendesk #4037 - Aucune erreur de profil utile
* Zendesk #4262 - Le lecteur Adobe Primetime se bloque sous Windows 10

Correction d’un blocage dans Windows Firefox lors de la lecture en mode plein écran.

**Version 1.4.11** (1.4.11.648)

* Zendesk #1869 - Problème lors de la modification de la taille de police (nécessite le Flash Player 18.0.0.200)

Autoriser l’utilisation des tailles de légende dans le code de légende WebVTT.

* Zendesk #3113 - Flash Player du blocage des modules externes (nécessite Flash Player 18.0.0.200)
* Zendesk #3268 - Desktop : Le lecteur vidéo commence à scintiller après +- 40/50 secondes et commence à devenir noir après +- 90 secondes (Flash Player 18.0.0.200 requis).

Correction d’un bogue vidéo d’étape.

* Zendesk #3670 - Erreur INVALID_PARAMETER dans VOD lors de la recherche dans le lecteur de référence (nécessite le Flash Player 18.0.0.200)

InvalidateProfiles dans ThreadSeek lorsqu’une nouvelle période est détectée.

* Zendesk #3896 - Blocage de Flash Player avec l’intégrité de diffusion définie sur ON sur Chrome (nécessite le Flash Player 18.0.0.200)

Correction d’un blocage en mode de mise en réseau natif dans pepper.

* Zendesk #3905 - Le lecteur TVSDK ne se charge pas lorsqu’il est hébergé sur CDN

Correction de problèmes liés à la recherche d’un jeton de caractère générique lorsque pageDomain est différent du domaine swf.

**Version 1.4.10** (1.4.10.642)

* Zendesk #3249 - Le lecteur web TVSDK bloque le Flash sur Firefox

Correction d’un blocage de Flash Player occasionnel avec Firefox sur Mac lorsqu’un flux, lu sur un moniteur externe, basculait vers un flux à débit supérieur.(nécessite le Flash Player 18.0.0.160)

* Zendesk #3268 - Desktop : Le lecteur vidéo commence à scintiller après `+-` 40/50 secondes et commence à devenir noir après `+-` 90 secondes

Correction d’un problème dans Mac Chrome en raison duquel la diffusion commençait à scintiller et finissait par devenir noire. (nécessite le Flash Player 18.0.0.161)

* Zendesk #3304 - VAST 3.0 `[ERRORCODE]` macro non renseignée

   * le code d’erreur 400 sera révélé si la publicité intégrée comporte un contenu créatif incorrect.
   * `[ERRORCODE]` La macro sera encodée en URL

* Zendesk #3601 - Demande d’amélioration : Gestion des compagnons d’emballage

   * TVSDK affiche le compagnon des wrappers qui contient des ressources (html, iframe ou statique ) proches de la version intégrée. (si la ligne d’entrée ne contient pas une pour cette taille)
   * Les compagnons d’encapsulage avec une ressource, sauf si elle est utilisée pour l’affichage, seront ignorés. (non utilisé pour le suivi )
   * Seuls les compagnons d’encapsulation sans ressource seront utilisés à des fins de suivi. ( compagnon wrapper ne contenant que le suivi )

**Version 1.4.9**

* Zendesk #2615 - problème lors de la suppression de la vue HLS de l’affichage de bureau

Ajout de la méthode clearVideo() à MediaPlayer. Efface le cadre vidéo affiché en effaçant AVStream de l’objet StageVideo. Doit être appelé uniquement si la vidéo est mise en pause et replaceCurrentResource ou replaceCurrentItem doit être appelé avant que play() puisse être de nouveau appelé.

* Zendesk #3169 - Mise à jour du lecteur de référence avec l’intégration d’Adobe Analytics

Mise à jour du lecteur de référence avec l’intégration d’Adobe Analytics

* Zendesk #3296 - Desktop HLS TVSDK - Publicités tierces VAST non lues

Les types MIME pour le format HLS étaient sensibles à la casse. Ils étaient incorrects et ont été modifiés afin qu’ils ne soient plus sensibles à la casse.

**Version 1.4.8**

* Zendesk #2737 - Desktop Player - Error 106000 (nécessite le Flash Player 17.0.0.184)
* Zendesk #3007 - Les publicités preroll n’apparaissent pas après la mise à jour vers le Flash Player 17 (nécessite le Flash Player 17.0.0.184)
* Zendesk #3085 - Desktop HLS Player renvoie une erreur 106000 après 60 secondes (nécessite le Flash Player 17.0.0.184)

**Version 1.4.7**

* Zendesk #2760 - Balise DISCONTINUITY ignorée pendant le mode TrickPlay (nécessite la version 17.0.0.158 du Flash Player)
* Zendesk #2760 - Balise DISCONTINUITY ignorée pendant le mode TrickPlay (nécessite la version 17.0.0.158 du Flash Player)

**Version 1.4.6**

* Zendesk #2652 - Documentation Auditude pour les fichiers HLS de bureau, Clarification des media_id Auditude pour la documentation HLS de bureau

**Version 1.4.5**

* Zendesk #2256 - Accès à la liste de lecture des Principal, mise à jour du PSDK pour distribuer des événements timedMetadata pour les balises inscrites sur la liste de lecture principale. (nécessite la version 17.0.0.134 du Flash Player)
* Zendesk #2417 - Lecteur tentant de télécharger des sous-titres avant le début de la lecture, WebVTT utilisait une variable de numéro de segment incorrecte pour la correspondance de numéro de segment. Le bogue s’affichait uniquement pour les médias dont les index de segment commençaient à zéro. (nécessite la version 17.0.0.134 du Flash Player)
* Zendesk #2537 - Le lecteur de Flash se bloque lors de l’utilisation du module externe pepper avec Chrome (nécessite la version 17.0.0.134 de Flash Player)
* Zendesk #2547 - Sous-titres en arabe : Le texte doit être aligné à droite (nécessite la version 17.0.0.134 du Flash Player).

**Version 1.4.4**

* Zendesk #1561 - Re : `[Adobe Primetime]` Mise à jour : Prise en charge du basculement basé sur le client HLS pour PROGRAM-DATE-TIME dans le PSDK de bureau (nécessite la version 16.0.0.305 ou ultérieure du Flash Player)
* Zendesk #2197 - `[Ads]` Tracking des erreurs publicitaires
* Zendesk #2286 - Feature Request : Fournir des informations sur l’état de chargement des publicités (VPAID)
* Zendesk #2285 - Feature Request : Ignorer la publicité après une durée spécifiée
* Bogue #3921755 - Mise à jour de la bibliothèque OpenSSL vers la version 1.0.1L en Flash Player (nécessite la version 16.0.0.305 de Flash Player ou ultérieure)

**Version 1.4.2**

* Zendesk #1303 - Décalage vertical pour le sous-titrage codé (nécessite la version 16.0.0.235 ou ultérieure du Flash Player, date de publication prévue : Décembre 2014)
* Zendesk #1870 - Closed Caption Activation et désactivation (nécessite la version 16.0.0.235 ou ultérieure du Flash Player, date de publication prévue) : Décembre 2014)
* Zendesk #2110 - La lecture est bloquée après avoir tenté d’entrer en mode plein écran pendant une publicité VPAID (nécessite la version 16.0.0.235 ou une version ultérieure du Flash Player), date de publication prévue : Décembre 2014)
* Zendesk #2199 - `[VPAID]` Le lecteur ne répond pas lors de la recherche d’une coupure publicitaire passée
* Zendesk #2358 - Re : `[Analytics]` Données de chapitre incorrectes

**Version 1.4.1**

* Mise à jour de l’API Blackouts pour qu’elle soit cohérente avec la mise en oeuvre d’Android et d’iOS.

**Version 1.4.0**

* Zendesk #1024 - Fonctionnalité de suppression de la publicité du flux via le manifeste
* Zendesk #1423 - L’échec de lecture HLS bloque le Flash Player (sans erreur signalée).
* Zendesk #1674 - ClosedCaption Non affiché, la légende 708 correcte s’affiche lorsque les codes ETX 0x03 sont manquants.

## Problèmes connus {#known-issues}

* Le sous-titrage codé ne fonctionne pas avec le contenu audio uniquement, car le système de sous-titrage a besoin d’une vidéo pour fonctionner.
Sans vidéo, il n’y a pas de dimension de fenêtre d’affichage et sans dimension de fenêtre d’affichage, vous ne pouvez pas afficher de graphiques pour les sous-titres.
* L’intégrité des diffusions est légèrement plus lente dans Google Chrome en raison des restrictions de l’environnement de test Chrome.
* Dans TVSDK 1.4, si vous désactivez la lecture automatique, une erreur DRM peut se produire lorsque le lecteur reste inactif pendant au moins une minute. Pour contourner ce problème, lorsque vous désactivez la lecture automatique mais que vous préchargez des ressources, modifiez `ReferenceCore.as` en modifiant le contenu de `onPlaybackManagerPrepared`:

```
if (_playbackManager.autoPlay) {
_playbackManager.play();
} else {
_playbackManager.play();
_playbackManager.pause();
}
```

* **Version 1.4.13** PTPLAY-8501 - Lorsque VMAP renvoie deux publicités MP4 non transcodées directes, la même publicité rétroactive est lue deux fois.

* **Version 1.4.2** Dans la version 16 du Flash Player, un problème a été identifié avec la logique de &quot;basculement&quot; de l’ABR, une fois que le lecteur est entré dans un événement de mise en mémoire tampon vide. Le problème empêche le débit binaire de basculer dans les environnements à bande passante incorrecte une fois que le lecteur passe en état de mise en mémoire tampon. Pour contourner le problème, demandez à votre application de définir la variable `BufferControlParameters.initialBufferTime` pour être identique à `BufferControlParameters.playbackBufferTime` temporairement pendant l’état de mise en mémoire tampon (c’est-à-dire, sur un `BufferEvent.BUFFERING_BEGIN` ), puis réinitialisez-la aux valeurs définies sur . `BufferEvent.BUFFERING_END` . Le correctif pour ce problème sera disponible dans la prochaine version de correctif de Flash Player version 16.

* **Version 1.4.0**

   * PTPLAY-1634 - La même balise Abonnée comporte différents horodatages dans différentes fenêtres actives. Lorsque des fenêtres actives se déplacent, la même balise dans chacune d’elles doit avoir les mêmes horodatages. Cependant, il arrive parfois que les mêmes balises aient des horodatages différents.
   * PTPLAY-28 - La chronologie MediaPlayer n’inclut pas les pauses vides.
   * Un fichier de stratégie interdomaines (crossdomain.xml) est requis pour obtenir l’autorisation de diffuser du contenu depuis un autre domaine. [Définition d’un fichier crossdomain.xml pour la diffusion en continu HTTP](https://helpx.adobe.com/adobe-media-server/dev/configure-dynamic-streaming-live-streaming.html).
   * Bogue #3694203 - Dans un flux de données virtuelle, la recherche depuis un mid-roll dans un autre signal publicitaire mid-roll peut entraîner un gel du navigateur.
   * Bogue #3753725 - selectPolicyForSeekIntoAd ne prend pas en compte si la coupure publicitaire a été visionnée
   * Bogue #3754529 - Les publicités preroll ne sont pas supprimées de la diffusion lors de la recherche en amont dans une diffusion DVR en direct.
   * Bogue #3761896 - Si la recherche est autorisée pendant la lecture de la publicité, les marqueurs de publicité seront réajustés après la recherche. La solution consiste à ne pas utiliser le rappel Item_UPDATED lors de la recherche.
   * Bogue #3779889 - L’appel complet n’est pas effectué lorsque vous atteignez la fin de la lecture de l’astuce dans Video Analytics.
   * Bogue #VA-779 - La pulsation de l’événement de changement de débit n’est pas envoyée pour l’analyse vidéo améliorée avec la mise en oeuvre de la référence de prise en charge de la pulsation - La lecture de la marque n’est pas mise en oeuvre dans l’exemple d’application.

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://helpx.adobe.com/support/primetime.html) page.
