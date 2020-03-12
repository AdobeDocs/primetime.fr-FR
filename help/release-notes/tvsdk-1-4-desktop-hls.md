---
title: Notes de mise à jour de TVSDK 1.4 pour Desktop HLS
seo-title: Notes de mise à jour de TVSDK 1.4 pour Desktop HLS
description: Les notes de mise à jour TVSDK for Desktop HLS décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus dans TVSDK DHLS.
seo-description: Les notes de mise à jour TVSDK for Desktop HLS décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus dans TVSDK DHLS.
uuid: 84da27b7-299b-478d-88f5-ef943f0a8321
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: e4437a26-9454-4da1-ae87-0fce664aac3d
translation-type: tm+mt
source-git-commit: a94150abc2afff4af24ee83573e73124f8b3260a

---


# Notes de mise à jour de TVSDK 1.4 pour Desktop HLS {#tvsdk-for-desktop-hls-release-notes}

Les notes de mise à jour TVSDK for Desktop HLS décrivent les nouveautés ou les modifications, les problèmes résolus et connus dans TVSDK DHLS.

## Nouvelles fonctionnalités {#new-features}

**1.4.31**

* **Prise en charge multi-CDN pour les publicités CRS**

   * Par défaut, tous les fichiers transcodés seront hébergés sur le CDN d’Adobe sur Akamai. Avec la dernière version, Adobe Creative Repackaging Service (CRS) permet de télécharger les éléments créatifs transcodés sur plusieurs réseaux de diffusion de contenu selon les besoins du client.
   * De nouvelles API sont ajoutées à TVSDK pour permettre de spécifier l’URL créative CRS finale lorsque l’URL par défaut n’est pas utilisée. Reportez-vous à la documentation pour savoir comment utiliser ces nouvelles API.

### Nouvelles fonctionnalités des versions précédentes {#new-features-previous}

**1.4.30**

* **Mesures de facturation**

Afin d’accommoder les clients qui souhaitent payer uniquement ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.

**1.4.24**

* **Connexion réseau persistante**

Important : Vous devez avoir installé au moins Adobe Flash Player version 22 ou ultérieure.
Les connexions réseau persistantes créent et stockent un interne de connexions réseau qui peuvent être réutilisées pour plusieurs requêtes, au lieu d&#39;ouvrir une nouvelle connexion pour chaque requête réseau. Les connexions réseau persistantes doivent augmenter l&#39;efficacité et réduire la latence de votre code réseau.

Dans cette version, cette fonctionnalité n’est pas prise en charge dans Apple Safari et Mozilla Firefox sur Mac.

**1.4.19**

* Prise en charge de l’intégrité du flux pour les annonces VPAID.
* Activation de l’option d’onglet silencieux dans le lecteur Flash FP 20.0.0.267 pour Firefox 42 et versions ultérieures en corrigeant le problème de blocage.

**1.4.18**

* Primetime Desktop HLS TVSDK prend désormais en charge les éléments créatifs SWF linéaires VPAID 2.0 pour permettre une expérience publicitaire interactive riche en flux continu.

**1.4.10**

* **Abandon de publicité, chaînement de publicités dans la logique de sélection de publicités (Zendesk #3103)** Pour les publicités VAST (créatifs) avec la règle de secours activée, le kit TVSDK traite une publicité avec un type MIME non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.

Pour plus d’informations, voir Reprise [publicitaire pour les annonces VAST et VMAP](../programming/tvsdk-1.4-for-android/ad-insertion/ad-fallback/android-1.4-ad-fallback.md).

**1.4.8**

* **Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.5**

   * Possibilité d’envoyer des métadonnées avec des  vidéo et/ou des vidéo/publicitaire/de chapitre en tant que données contextuelles
   * Moins de trafic réseau : les pulsations sont moins nombreuses en moyenne et de taille plus petite.

**1.4.7**

* **Prise en charge de l’individualisation sur site**

Prise en charge des installations sur site d’Adobe Individualization Server pour personnaliser la demande d’individualisation du client afin d’accéder à un autre point de terminaison.

**1.4.6**

* **Exemple de chiffrement AES (nécessite Flash Player version 17.0.0.134)**

Le chiffrement AES basé sur des exemples est désormais pris en charge.

**1.4.2**

* **Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.4.0.1**

   * Ajout de la possibilité de regrouper différents cas d’utilisation d’analyses, provenant d’autres kits SDK ou lecteurs, avec Adobe Analytics Video Essentials.
   * Le suivi des publicités a été optimisé en supprimant les méthodes trackAdBreakStart et trackAdBreakComplete. La coupure publicitaire est déduite des appels des méthodes trackAdStart et trackAdComplete.
   * La propriété playhead n’est plus nécessaire lors du suivi des publicités.

**1.4.0**

* **Signalisation par coupure de courant avec remplacement** de contenu alternatif Dans le cadre de la mise à jour de TVSDK 1.4, TVSDK prend également en charge l’entrée et le retour des coupures de courant régionales par rapport au contenu linéaire. Le TVSDK peut maintenant traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d&#39;arrêt même lorsque la programmation alternative est présentée à la place de la programmation originale.

* **Supprimez/Remplacez les publicités** C3 Maintenant, aucun travail de préparation supplémentaire n’est nécessaire pour insérer dynamiquement de nouvelles publicités dans les ressources vidéo à la demande (VOD) qui sortent de la fenêtre C3. Le SDK TVSDK fournit désormais une API pour supprimer des plages de contenu personnalisées et insérer dynamiquement de nouvelles publicités. Cette nouvelle fonctionnalité puissante est également utile dans les cas où le contenu en direct/linéaire est diffusé pendant la diffusion et est immédiatement retiré pour être utilisé comme contenu à la demande sans le temps approprié pour &quot;nettoyer&quot; le fichier.

## Problèmes résolus {#resolved-issues}

>[!NOTE]
>
>Tous les clients TVSDK qui utilisent CRS sont vivement encouragés à effectuer la mise à niveau vers au moins TVSDK 1.4.32 sur iOS, Android et HLS pour ordinateur. Cette mise à niveau remplacera la mise en oeuvre de l’application existante. Après la mise à niveau, recherchez les demandes d’URL de création CRS dans un outil proxy (Charles, par exemple) pour vérifier que la version du chemin d’accès reflète la version 3.1. Par exemple,
>
>`https://adunit.cdn.auditude.com/assets/3p/v3.1/218747/94b/c1b/94bc1b964cc67e115a5a6781c7329b90_ee92607938ffff46b083121f044c2746.m3u8`

**Version 1.4.41**

* Zendesk #33777 - Le fichier SWF du jeton Localhost pour la version de distribution DHLS a expiré.

   Mise à jour du jeton localhost pour la démonstration PMP sur DHLS.

### Problèmes résolus dans les versions précédentes {#resolved-issues-previous}

**Version 1.4.38** (891)

* Zendesk #30731 - TVSDK ne lit pas plusieurs publicités VPAID dans une AdBreak.

   Correction de la lecture de plusieurs publicités VPAID dans un AdBreak.

* Zendesk #29968 - Panneau de .

   Le lecteur vidéo peut répéter le dernier segment d’une période au cours de laquelle un commutateur ABR se produit. En raison de cela, il arrive que le dernier segment de préroll se répète. Ce problème a été résolu.

**Version 1.4.35** (879)

* Zendesk #26058 - Prend en charge les natifs VPAID

**Version 1.4.33** (873)

* Zendesk #21701 - Envoyez l’URL originale de création pour la demande CRS 1401 au lieu de l’URL normalisée.

   Le problème de demande d’URL déjà reconditionnées pour le transcodage a été résolu, conformément aux exigences du serveur principal CRS.
* Zendesk #26197 - Compression anamorphique non rejouée dans la résolution d’affichage souhaitée.

   **Remarque**: Ce problème nécessite Flash Player 24.0.0.194 ou version ultérieure.

   Le problème d’utilisation d’entrées manquantes dans les tableaux des proportions pour calculer la largeur de sortie a été corrigé.

* Zendesk #26840 - Échec de la détection HDCP sur IE11 + Windows7 après une deuxième tentative.

   **Remarque**: Ce problème nécessite Flash Player 24.0.0.218 ou version ultérieure.

   Ce problème a été résolu en modifiant le traitement principal de la file d’attente des messages d’AdobeCP afin qu’il effectue une itération dans toute la file d’attente, au lieu de se limiter au blocage du tout premier message.

* Zendesk #27460 - Le nouveau compte Akamai ne peut pas gérer une requête POST CDN.

   Le nouveau compte CDN ne peut pas traiter une demande de CDN POST. Ce problème a été résolu en mettant à jour le code afin que la demande d’annonce cdn.auditude.com soit GET au lieu de POST.
* Zendesk #27619 - Un blocage de Flash sous Windows 10

   **Remarque**: Ce problème nécessite Flash Player 24.0.0.218 ou version ultérieure.

   Ce problème a été résolu en empêchant une erreur en raison de longues URL.

* Zendesk #28218 - Le de suivi ne se déclenche pas pendant que le référentiel du point de reprise

   Ce problème est le même que dans Zendesk #26592. Le problème en raison duquel les opérations de recherche étaient autorisées lorsque le lecteur multimédia était à l’état PRÉPARÉ pour les flux VOD a été résolu.

**Version 1.4.32** (867)

*  de suivi Zendesk #26592 ne se déclenche pas lorsque le de lecture  à partir du point de reprise

Le code ne mettait pas à jour l’élément de coupure publicitaire preroll lorsque le point de reprise n’était pas zéro. Ce problème a été résolu en ajoutant une logique permettant d’actualiser le code lorsque la plage  fois ne correspond pas.

* Zendesk #27022 Les publicités ne sont pas lues la deuxième fois qu’une ressource est lue

Les exceptions aux méthodes de tableau ont été corrigées.

**Version 1.4.30** (855)

Les problèmes suivants ont été résolus pour TVSDK dans cette version :

* Zendesk #22898 - Les sous-titres manquants ne doivent pas entraîner l’échec de la lecture.

**Remarque**: Ce problème nécessite Flash Player 23.0.0.185 ou une version ultérieure.

Ce problème a été résolu en permettant à TVSDK de poursuivre la lecture, même si le manifeste ne contient pas le WebVTT M3U8, et il suffit d’enregistrer un avertissement.

* Zendesk #23454 - Les publicités tierces (VPAID) ne sont pas gérées correctement

Ce problème a été résolu en gérant correctement les publicités VPAID en fonction des ID de contenu plutôt que des plages de temps.

* Zendesk #24528 - Mesures d’utilisation du SDK pour la facturation.

Important : Ce problème nécessite Flash Player 23.0.0.185 ou une version ultérieure.

* Problème de sous-titrage de Zendesk # 25432 lors du redimensionnement du lecteur.

Important : Ce problème nécessite Flash Player 23.0.0.185 ou une version ultérieure.

Le code d’affichage de texture de la légende a été corrigé afin de gérer correctement les coordonnées lors du redimensionnement du lecteur.

La bibliothèque Video Heartbeat (VHL) a été mise à jour vers la version 1.5.9 afin de résoudre les problèmes suivants :

* Zendesk #23730 - Les mesures de débit sont vides

Ce problème a été résolu en suivant les changements de débit dans VideoAnalyticsTracker.

* Ajout d’une nouvelle API, assetDuration, à PTVideoAnalyticsTrackingMetadata pour mettre à jour la durée des ressources pour les flux en direct/linéaires.

**Version 1.4.28** (848)

* Zendesk #25027 - Auditude ne fonctionne pas dans la version de bureau 1.4.27

Ce problème a été résolu en ajoutant le code permettant de vérifier la clé AUDITUDE_METADATA_KEY et en rendant les clés AUDITUDE_METADATA_KEY et ADVERTISING_METADATA_KEY interchangeables.

* Zendesk #24428 - Problème de mise en mémoire tampon fréquente lors de l’utilisation de TVSDK pour lire un DRM HLS

Ce problème a été résolu en tenant compte du fait que, lorsqu’il n’y a aucune configuration de publicité, TVSDK peut accélérer le traitement en éliminant la suspension de la publicité preroll et de la réservation en direct sur la chronologie conçue pour synchroniser l’insertion de publicité.

* Zendesk #24344 - Désactivez les fichiers WebVTT pour améliorer les temps de .

**Remarque**: Ce problème nécessite Flash Player 23 ou version ultérieure.

Ce problème a été résolu en chargeant les fichiers WebVTT uniquement lorsque des légendes doivent être affichées.

* Zendesk #24994 - Le sous-titrage est retiré du lecteur lors du retour d’une pause commerciale.

**Remarque**: Ce problème nécessite Flash Player 23 ou version ultérieure.

Le code EOC fallacieux a fait disparaître l’affichage de la légende. Ce problème a été résolu en obligeant les codes de sous-titrage 608 RU2, RU3 et RU4 à fournir la visibilité correcte dans la fenêtre active actuelle.

**Version 1.4.27** (844)

* Zendesk #21554 - Balises d’erreur TVSDK non déclenchées pour le type d’application = video/mp4

Ce problème a été résolu en activant TVSDK pour effectuer un test ping sur les URL de suivi des erreurs correctes sur les formats de fichier non valides.

* Zendesk #23402 - Lecture publicitaire incomplète

**Remarque**: Ce problème nécessite Flash Player 23 ou version ultérieure.

Après avoir obtenu une erreur 404 sur certaines requêtes, un blocage peut se produire. Ce problème a été résolu en veillant à ce que la connexion ne s’arrête pas pendant que la réponse est traitée. La résolution garantit que les fichiers de publicité VPAID ne sont pas comptabilisés incorrectement. Ils ne sont donc pas publiés pendant le téléchargement.

* Zendesk #23621 - La nouvelle tentative échoue sur 400 et 404

**Remarque**: Ce problème nécessite Flash Player 23 ou version ultérieure.

Correction d’un problème en raison duquel les métadonnées DRM étaient endommagées lors du passage d’un  à un autre.

* Zendesk #23705 - Blocage des publicités vidéo pendant les pauses AdStitched

**Remarque**: Ce problème nécessite Flash Player 23 ou version ultérieure.

Ce problème est le même que dans Zendesk #23621.

* Zendesk #23905 - Certaines coupures publicitaires ne sont pas autorisées

**Remarque**: Ce problème nécessite Flash Player 23 ou version ultérieure.

Le code réseau natif Windows a été corrigé afin de s&#39;assurer que les connexions ne ferment pas les poignées actuellement utilisées par d&#39;autres connexions.

* Billet n° 24029 - Les flux RSS HLS ne lisent pas toutes les publicités mid-roll dans le fichier .json mid-roll.

Ce problème a été résolu en permettant aux clients de définir des paramètres personnalisés séparément sur l’instance Opportunity afin que les clients n’aient pas à remplacer OpportunityGenerator.

**Version 1.4.26** (839)

* Zendesk #18854 - Mise à jour de la logique de sélection créative basée sur les règles CRS
   * Prise en charge de la mise à jour de la logique de sélection créative en fonction des règles CRS

* Zendesk #22725 - mise en oeuvre de playbackManager.beginPlayback() dans l’exemple d’application pour bureau

   * Correction en supprimant cet appel redondant à la fin de startPlaybackFromFlashVars, car la méthode est appelée à partir de setupVideo()

* Zendesk #22807 - Exception de référence nulle SearchManager

   * Correction en fournissant la protection nécessaire du pointeur NULL à l’intérieur de SeekManager en rapport avec _dispatcher

* Zendesk #22822 - Mise en mémoire tampon fréquente lors de l’utilisation de TVSDK pour lire un fichier HLS clair

   * Correction en supprimant l’opportunité initiale générée par adSignalingModeOpportunityGenerator en l’absence de publicité

* Zendesk #23378 - L’intégrité du flux bloque le fichier rule.xml

   * Corrigé en chargeant le fichier rule.xml via le flux de travaux d’intégrité du flux

**Version 1.4.24** (817)

* Zendesk #19851 - Lorsque le lecteur s’adapte à un autre débit, il saute quelques images dans le temps sur le nouveau débit, ce qui rend l’expérience maladroite

**Remarque**: Ce problème nécessite Flash Player 22.0.0.175 ou une version ultérieure.

Le problème de réinitialisation de l’adaptateur DRM après le téléchargement d’une petite partie d’un segment qui n’est pas restauré correctement a été résolu.

* Zendesk #20784 - Analytics : Déclenchement du contenu terminé pour les vidéo en direct 

Ce problème a été résolu en ajoutant une API (trackVideoComplete) pour déclencher manuellement la fin du contenu lors d’une session de suivi vidéo LINEAR/LIVE.

Les bibliothèques suivantes ont été mises à jour :

* Zendesk #21643 - Les publicités VPAID ne sont pas lues en intégralité

   * Bibliothèque AdobeMobile vers la version 4.10.0
   * Bibliothèque VHL vers 1.5.6
   * Bibliothèque VHL-Nielsen à 1.6.7

Ce problème a été résolu par l’utilisation d’une fenêtre d’affichage à hauteur nulle pour remplir l’étape de lecture d’une publicité VPAID.

* Zendesk #22110 - Analytics : Ajouter un champ h:sc:ssl aux appels de suivi de pulsation

Les problèmes liés au protocole SSL ont été résolus et la bibliothèque VHL utilisée dans TVSDK a été mise à jour vers la dernière version.

* Zendesk #22608 - La vidéo montre un écran noir par intermittence (nécessite Flash Player 22.0.0.175 ou une version ultérieure)

Pendant le débit adaptatif, avec la limite de débit maximale, le rechargement de la vidéo affiche un écran noir par intermittence, même si le client voit les mises à jour de sa position et se comporte comme s’il lisait du contenu.

**Version 1.4.23** (809)

* Zendesk #2887 - Problème de saut de publicité après le roulage lorsque la logique de règle publicitaire s’appliquait à TVSDK

**Remarque**: Ce problème nécessite Flash Player 21.0.0.240 ou une version ultérieure.

Correction du problème de saut des publicités consécutives au cumul lorsque la logique de la règle publicitaire était appliquée à TVSDK.

* Zendesk #19863 - Annonce avec fichier média VPAID ignoré

Si une vaste publicité intégrée comporte plusieurs fichiers multimédia dont la première est une publicité VPAID, la publicité intégrée n’est pas lue pour les flux en direct. Ce problème a été résolu en sélectionnant un autre fichier multimédia à la place.

* Zendesk #21021 - Liaison tardive de l’audio qui entraîne des répétitions de segments audio

**Remarque**: Ce problème nécessite Flash Player 21.0.0.240 ou une version ultérieure.

Le problème de répétition audio a été résolu.

* Zendesk #21125 - Retour d’une coupure publicitaire linéaire/en direct tôt

**Remarque**: Ce problème nécessite Flash Player 21.0.0.240 ou une version ultérieure.

Cette version permet de revenir d’une coupure publicitaire tôt avant que la coupure publicitaire ne soit lue jusqu’à la fin. Un retour anticipé est indiqué par le biais d’une balise de manifeste personnalisée.

* Zendesk n° 21369 Le son de liaison tardive provoque une incohérence temporelle

**Remarque**: Ce problème nécessite Flash Player 21.0.0.240 ou une version ultérieure.

Le problème de répétition audio qui a été corrigé a également résolu ce problème.

* Zendesk n° 21760, 20921 - Audio Video Desync on Seek.

**Remarque**: Ce problème nécessite Flash Player 21.0.0.240 ou une version ultérieure.

Le problème de répétition audio a été résolu.

* Zendesk #22024 - Erreur lors de l’exécution de TVSDK

Le problème en raison duquel le lecteur de référence ne lisait aucun flux et renvoyait une exception au  a été résolu.

**Version 1.4.22** (791)

* Zendesk #17580 - Erreur d’exécution Primetime avec le code 3357

**Remarque**: Ce problème nécessite Flash Player 21.0.0.197 ou version ultérieure.

Les erreurs 3357 aléatoires survenues lors de l’initialisation correcte de deviceID lors de l’appel de storeVoucher() ont été corrigées.

* Zendesk #21334 - Valeur du délai d’expiration de la demande d’annonce TVSDK pour les demandes d’annonce tierces

Dans cette version, le délai d’expiration global de la demande d’annonce a été ajouté.

**Version 1.4.21** (782)

* Zendesk #19580 TVSDK attend la fin du programme de résolution de contenu avant d’envoyer `PTTimedMetadataChangedNotification` des notifications

**Remarque**: Ce problème nécessite Flash Player 21.0.0.182 ou version ultérieure.

Ce problème a été résolu dans le lecteur de référence pour ordinateur en permettant de définir des balises publicitaires et en ajoutant un générateur d’opportunités personnalisé qui montre comment s’abonner à des signaux personnalisés et comment traiter ces signaux dans un fichier VOD.

* Zendesk #20806 Les futures publicités mid-roll dans la fenêtre du DVR ne se déclenchent pas après le permutation de cames

**Remarque**: Ce problème nécessite Flash Player 21.0.0.182 ou version ultérieure.

Ce problème a été résolu en mettant à jour l’application pour définir _resource.metadata.setValue(DefaultMetadataKeys.ENABLE_LIVE_PREROLL, &quot;false&quot;) afin de désactiver l’insertion de publicités preroll dans un échange PIP et, par conséquent, aucune opportunité pre-roll n’est générée.

Une fonctionnalité de tri a été introduite pour corriger l’emplacement d’annonce hors séquence qui résultait en une durée de contenu principal négative.

* Zendesk #20522 : Impossible d&#39;ignorer les publicités VPAID 2.0

**Remarque**: Ce problème nécessite Flash Player 21.0.0.182 ou version ultérieure.

* Ce problème a été résolu en ignorant les publicités VPAID pendant l’annulation de la publicité.
* Lorsque la stratégie adbreak est définie sur saut, les  de coupure publicitaire et publicitaire sont toujours distribuées. L’état du lecteur est incohérent.

Ce problème a été résolu afin de se comporter correctement et de ne pas distribuer de  de lorsque la coupure publicitaire est ignorée.

* Zendesk #20955 Définition de paires clé-valeur dans la propriété customParameters via le générateur d’opportunités

**Remarque**: Ce problème nécessite Flash Player 21.0.0.182 ou version ultérieure.

La requête Auditude analyse les paramètres AuditudeSettings à la recherche de paramètres personnalisés lors de la création d’une unité publicitaire pour les requêtes publicitaires.

Ce comportement a été modifié afin d’inclure des paramètres personnalisés de l’objet Opportunity dans la requête. En outre, plusieurs opportunités avec différents paramètres personnalisés ne peuvent pas être regroupées dans une seule requête Auditude.

* Zendesk #21227 - m3u8 ne joue pas de manière cohérente

**Remarque**: Ce problème nécessite Flash Player 21.0.0.211 ou une version ultérieure.

Ce problème a été résolu en permettant à TVSDK d’ignorer le manifeste (sous-HLS) qui contient le codec AC3 que TVSDK ne prend pas en charge (surround).

**Version 1.4.20** (762)

* Zendesk #19181 - Les mecs jouent vite en avant pour qu&#39;ils se bloquent.

**Remarque**: Ce problème nécessite Flash Player 20.0.0.306 ou version ultérieure.

* Zendesk #19286 - Un blocage du lecteur Flash s’est produit lors de la recherche aller-retour dans un flux FER.

**Remarque**: Ce problème nécessite Flash Player 20.0.0.306 ou version ultérieure.

Les blocages occasionnels survenant lors de la recherche dans Google Chrome ont été résolus en arrêtant le  du, si le  du prend trop de temps pour obtenir une réponse ou si le socket est en cours d’arrêt.

* Zendesk #19305 - Lecture en saut rencontrée lors de la lecture d’un flux avec des discontinuités A/V.

**Remarque**: Ce problème nécessite Flash Player 20.0.0.306 ou version ultérieure.

Ce problème a été résolu par un  d’avertissement.

* Zendesk # 19359 - Flash Player s’est écrasé en raison de la position de #EXT-X-FAXS-CM : dans le manifeste de niveau set.

Ce problème a été résolu lorsque la balise #EXT-X-FAXS-CM apparaît dans la liste de lecture supérieure avant le débit individuel ou les segments dans la liste de lecture.

* Zendesk #19489 - Module externe d’installation Fast Forward to Live Point (flux en direct)

Ce problème est le même que Zendesk #19181.

* Zendesk #19699 - TVSDK ne parvient pas à basculer entre les pistes de sous-titres WebVTT

Ce problème a été résolu en faisant le vidage du lecteur et en rechargeant le manifeste lorsqu’un suivi change et en corrigeant le problème de conversion de chaîne UTF8 qui affectait les noms de suivi des sous-titres WebVTT sur -octets.

**Version 1.4.19** (1.4.19.738)

* Zendesk #18234 - Flash Player plante la lecture des flux avec des chaînes Unicode dans CC

Ce problème nécessite Flash Player FP 20.0.0.267 ou version ultérieure et a été résolu en gérant correctement la chaîne Unicode.

* Zendesk #18304 - Prise en charge de l’intégrité des flux pour les publicités VPAID

Cette fonctionnalité nécessite Flash Player FP 20.0.0.267 ou version ultérieure et a été introduite dans la version 1.4.19.

* Zendesk #18766 - Le lecteur de référence ne peut pas afficher les caractères unicode non latins dans les noms de pistes CC

Cette fonctionnalité nécessite Flash Player FP 20.0.0.267 ou une version ultérieure et a été corrigée en gérant correctement la chaîne Unicode.

* Zendesk #18804 - Le joueur plante dans Firefox 42

Ce problème nécessite Flash Player FP 20.0.0.235 ou une version ultérieure et il s’agit du même problème que Zendesk #18723.

* Zendesk #18864 - blocage du module externe Flash Player

Ce problème nécessite Flash Player FP 20.0.0.235 ou une version ultérieure et est identique à Zendesk #18723.

* Zendesk #18998 - Si les horodatages audio et vidéo ne correspondent pas, un téléchargement sans fin de segments en cas de discontinuité s’est produit.

Ce problème a été résolu en ignorant l’écart entre les horodatages et en lisant simplement le contenu téléchargé.

* Zendesk #19093 - Les publicités milieu de gamme ne peuvent être regardées qu’une seule fois avec du contenu en direct et en mode Plein (FER), mais ces publicités ne peuvent plus être regardées lors d’un transfert rapide ou d’une recherche au-delà des publicités.

Dans le sélecteur de stratégie publicitaire par défaut de Primetime, si une publicité preroll est visionnée, la coupure publicitaire n’est pas déplacée à la position recherchée lorsque vous terminez une recherche. Pour lire à nouveau la publicité, après la recherche, l’application doit remplacer la fonction selectAdBreaksToPlay().

* Zendesk #19101 - Le redécoupage en publicités Midroll non résolues supprime le placement de la publicité.

Ce problème a été résolu en permettant au lecteur de mettre à jour l’heure de playbackMetrics, l’heure d’opportunité minimale et le journal.

* Zendesk #19102 - Problèmes avec le mode FER et astuce

Ce problème nécessite Flash Player FP 20.0.0.267 ou version ultérieure et a été résolu en définissant correctement le paramètre adsMetadata.adSignalingMode.

* Zendesk #19175 - Parfois, les publicités preroll ne s’affichent pas la première fois que le flux est lu.

Ce problème a été résolu en ajoutant une nouvelle API, adRequestTimeout, aux paramètres AuditudeSettings pour un délai d’expiration de demande d’annonce. Les utilisateurs peuvent désormais remplacer le délai d’expiration des demandes publicitaires des 10 s par défaut.

**Version 1.4.18** (1.4.18.722)

* Zendesk #3324 - Le des publicités Primetime n’effectue pas de suivi des coupures publicitaires lorsqu’il n’existe aucun média publicitaire dans un VMAP.

Lorsqu’une coupure publicitaire est vide, le de coupure publicitaire et le de suivi complet n’étaient pas en cours d’épinglage. Ce problème a été résolu en envoyant des pings de de coupures publicitaires sur des coupures publicitaires vides, telles que VMAP AdBreak, avec un noeud AdSource valide.

**Version 1.4.17** (1.4.17.702)

* Zendesk #17168 - Les légendes n’apparaissent pas pendant environ 10 secondes après avoir basculé en visibilité.

Ce problème a été résolu en prenant en charge la balise EXT-X-MEDIA-TIME pour les fichiers de sous-titrage vtt.

* Zendesk #17983 - Le fait de ne pas télécharger de clés pour un manifeste provoque l’échec de la lecture complète du manifeste

**Remarque**: Vous devez avoir au moins Flash Player FP 19.0.0.245 ou version ultérieure.

Lorsque vous lisez parfois du contenu en direct, il se peut que le manifeste comporte des clés non valides (par exemple, pendant les périodes d’interruption), mais d’autres plages de temps peuvent avoir des clés valides et continueront à être lues. Auparavant, lorsqu’une clé répertoriée dans un manifeste ne pouvait pas être téléchargée, le manifeste entier échouait. Désormais, le manifeste échoue uniquement lorsque toutes les clés répertoriées ne peuvent pas être téléchargées. Si certaines clés sont valides, mais que certaines d’entre elles n’ont pas pu être téléchargées, le contenu est lu. Nous échouerons encore si nous essayons de jouer un segment qui nécessite une clé que nous n&#39;avons pas.

* Zendesk #18554 - Intégrité du flux qui réduit les cookies dans certains cas

**Remarque**: Vous devez avoir au moins Flash Player FP 19.0.0.245 ou version ultérieure.

Correction d’un bogue dans le code de manipulation de cookies qui pouvait tronquer les valeurs de cookie.

**Version 1.4.16** (1.4.16.684)

* Zendesk #3732 - Ajouter prise en charge des proxies dans Chrome pour l’intégrité du flux (nécessite Flash Player FP 19.0.0.207 ou version ultérieure)

C&#39;est une amélioration.

* Zendesk #4244 - Problèmes de diffusion en continu lors du survol PTS

Ce problème a été résolu en détectant le survol et en gérant la discontinuité par type de charge utile et non de manière générique.

* Zendesk #4487 - Suivi des  linéaires de contenu

Ce problème a été résolu en réinitialisant le suivi de pulsation vidéo pendant une session de lecture de flux linéaire.

* Zendesk #17427 - L’intégrité du flux Adobe ne fonctionne pas par le biais d’un proxy sur Chrome (Win7) ()

**Remarque**: La résolution nécessite Flash Player FP 19.0.0.207 ou version ultérieure.

Ce problème est le même que Zendesk #3732.

* Zendesk #17907 - Pointage sur pHLS Live Stream avec Flash Player 19

**Remarque**: La résolution nécessite Flash Player FP 19.0.0.207 ou version ultérieure.

Ce problème a été résolu en gérant les flux en direct dans lesquels les domaines des fichiers TS changent lors du rechargement du manifeste en direct et les fichiers ont été téléchargés deux fois.

* Zendesk #17931 - La lecture du contenu HLS avec ardoise au début échoue

**Remarque**: La résolution nécessite Flash Player FP 19.0.0.207 ou version ultérieure.

Le problème a été résolu en gérant les flux sans audio dans les 2 premières secondes du premier fichier TS.

* Zendesk #17934 - Echec de diffusion en direct avec Flash 19.0.0.185

**Remarque**: La résolution nécessite Flash Player FP 19.0.0.207 ou version ultérieure.

Le problème a été résolu en gérant les flux en direct avec le décalage temporel entre les images audio et vidéo sur les limites des segments.

* Zendesk #17973 - Dernière version de Flash Player 19.0.0.185 se bloque pendant le processus mid-roll

**Remarque**: La résolution nécessite Flash Player FP 19.0.0.207 ou version ultérieure.

Le problème a été résolu en gérant des fichiers audio non muxés avec insertion de publicités mid-roll. (Le commutateur d’analyseur se produit, et à tout moment de la lecture, le contenu  à la publicité intermédiaire, ou au milieu de la lecture de la publicité, etc.)

* Zendesk #18049 - Crash Flash 19 avec la version bêta de Firefox 42

Ce problème est le même que Zendesk #17973.

**Version 1.4.15** (1.4.15.678)

* Zendesk #4377 : Désactivez le AD_BREAK_SKIPPED lorsque vous ignorez une coupure publicitaire en raison de la stratégie publicitaire.

Le correctif était d’ajouter AD_BREAK_SKIPPED si une publicité est ignorée.

* Zendesk #4496 - Intégrité du flux : Erreur 102100 avec redirections vers des flux jetés.

Le correctif était d’ajouter la prise en charge de la définition de la propriété AVNetworkConfiguration useCookieHeaderForAllRequests via le kit TVSDK.

* Zendesk #17179 - Le lecteur Flash plante sur plusieurs modifications SAP pour le contenu chiffré.

Un blocage au cours de la lecture de certains contenus chiffrés a été corrigé.

**Remarque**: Le correctif requiert Flash Player 19.0.0.200 ou version ultérieure.

* Zendesk #17499 - Comment ne pas supprimer les midrolls après la surveillance mais supprimer la pré-lecture du contenu frelaté

Ajout d’un type à AdBreakTimelineItem (AdBreakTimelineItem.placementType) afin qu’AdPolicySelector puisse renvoyer une stratégie différente pour le contenu preroll, mid-roll et post-roll.

* Zendesk #17665 - Ralentissement de la bande passante

Le correctif était de supprimer la logique de modification de la taille de la mémoire tampon  du à la taille de la mémoire tampon initiale au début de la mise en mémoire tampon.

**Version 1.14.14** (1.4.14.771)

* Zendesk #17363 - Correction de la documentation README pour le lecteur de référence

   * Clarifier les instructions de téléchargement et d’installation de playerglobal.swc.
   * Ajouter des instructions pour mettre à jour la configuration du projet avec une version spécifique du lecteur Flash.
   * Mettez à jour la configuration du projet AdvertisingOverlay pour utiliser la version minimale du lecteur.
   * Mettre à jour la configuration du projet de base Reference pour utiliser une version spécifique du lecteur 11.9

* Zendesk #17471 - Le Joueur gèle

Correction partielle d’un problème en raison duquel une publicité n’est pas lue depuis le début après la recherche.

* Zendesk #17496 - Le postbuster n’est pas résolu lors de la recherche en retour dans la fenêtre du RVV.

Spécifiez des paramètres personnalisés pour chaque coupure publicitaire.

**Version 1.4.13** (1.4.13.660)

* Zendesk #4037 - Aucune erreur de utilisable (nécessite Flash Player 18.0.0.232 ou version ultérieure)

correction d’un problème d’analyse d’URL lorsque le paramètre  de l’contient &quot;http&quot;

* Zendesk #4260 - Flash Player 18 se bloque dans IE11 (nécessite Flash Player 18.0.0.232 ou version ultérieure)

Correction d’un blocage lors de la lecture d’une vidéo en mode plein écran avec IE11.

* Zendesk #4262 - Le lecteur Adobe Primetime se bloque sur Windows 10 (nécessite Flash Player 18.0.0.232 ou version ultérieure)

Correction d’un blocage lors de la lecture d’une vidéo en mode plein écran avec FireFox sous Windows.

* Zendesk n° 4279 - Insertion d’une publicité TVSDK HLS -302 - Problème de redirection sur iOS et bureau

Correction d’un problème en raison duquel une URL ne recevait pas correctement son type reconnu parce qu’elle n’avait pas d’extension.

* Zendesk #4306 - Le lecteur Flash se bloque lors du passage en plein écran sous Windows uniquement (nécessite Flash Player 18.0.0.232 ou version ultérieure)

Correction d’un blocage lors de la lecture d’une vidéo en mode plein écran sous Windows.

* Zendesk #4480 -  de balises ID3 manquant (nécessite Flash Player 18.0.0.232 ou version ultérieure)

**1.4.12 **(1.4.12.656)

* Zendesk #2751 - CSAI et CRS| Améliorer : Gérez les éléments dynamiques dans certaines URL de fichier multimédia.

Mise à jour de Creative Repackaging Service afin de gérer correctement les publicités avec des URL de création dynamiques.

* PTPLAY - 2114 - Prise en charge de la lecture MP4.

La lecture de base du contenu MP4 est désormais prise en charge, y compris la lecture, la mise en pause et la recherche.

Les éléments suivants nécessitent Flash Player 18.0.0.225 ou version ultérieure :

* Zendesk #3992 - Vitesses TrickPlay supplémentaires.

TrickPlay accepte désormais des taux supérieurs à 16x : +/- 32, +/-64 et +/-128.

* Zendesk #3113 - Arrêt du module externe Flash Player

Correction d’un blocage lors de la tentative de lecture d’une publicité de redirection sur Mac Firefox.

* Zendesk #4037 - Aucune erreur de utilisable
* Zendesk #4262 - Le lecteur Adobe Primetime se bloque sur Windows 10

Correction d’un blocage dans Windows Firefox lors de la lecture en mode plein écran.

**Version 1.4.11** (1.4.11.648)

* Zendesk #1869 - Problème de modification de la taille de la police (nécessite Flash Player 18.0.0.200)

Autorisez l’utilisation des tailles de légende dans le code de légende WebVTT.

* Zendesk #3113 - Arrêt du module externe Flash Player (nécessite Flash Player 18.0.0.200)
* Zendesk #3268 - Bureau : Le lecteur vidéo  scintiller après +- 40/50 secondes et le devenir noir après +- 90 secondes (nécessite Flash Player 18.0.0.200)

Correction d’un bogue de vidéo d’étape.

* Zendesk #3670 - Erreur INVALID_PARAMETER dans VOD lors de la recherche dans le lecteur de référence (nécessite Flash Player 18.0.0.200)

InvalidateProfiles dans ThreadSeek lorsqu’une nouvelle période est détectée.

* Zendesk #3896 - Flash Player plante lorsque l’intégrité du flux est activée sur Chrome (nécessite Flash Player 18.0.0.200)

Correction d’un blocage en mode de mise en réseau natif dans pepper. 

* Zendesk #3905 - Le lecteur TVSDK ne se charge pas lorsqu’il est hébergé sur CDN

Correction de problèmes de recherche du jeton de caractères génériques lorsque pageDomain est différent du domaine swf.

**Version 1.4.10** (1.4.10.642)

* Zendesk #3249 - Le lecteur web TVSDK bloque Flash sur Firefox

Correction d’un blocage occasionnel du lecteur Flash avec Firefox sur Mac lorsqu’un flux, en cours de lecture sur un moniteur externe, basculait vers un flux à débit plus élevé.(nécessite Flash Player 18.0.0.160)

* Zendesk #3268 - Bureau : du lecteur vidéo  scintillement après `+-` 40/50 secondes et noir après `+-` 90 secondes

Correction d’un problème sur Mac Chrome, en raison duquel le flux à scintiller et finit par devenir noir. (nécessite Flash Player 18.0.0.161)

* Zendesk #3304 - Macro VAST 3.0 `[ERRORCODE]` non renseignée

   * le code d’erreur 400 sera affiché si la publicité intégrée comporte un élément créatif incorrect.
   * `[ERRORCODE]` sera codée dans l’URL

* Zendesk #3601 - Demande d’amélioration : Gestion des compagnons d&#39;enveloppe

   * TVSDK affichera le compagnon des wrappers qui contient des ressources (html, iframe ou static ) se rapproche de la ligne d’entrée. (si la ligne d’entrée ne contient pas une pour cette taille)
   * Les compagnons d’enveloppes avec ressource, à moins qu’ils ne soient utilisés pour l’affichage, seront ignorés. (non utilisé pour le suivi)
   * Seuls les compagnons d’enveloppe sans ressource seront utilisés à des fins de suivi. ( compagnon wrapper ne contenant que le suivi )

**Version 1.4.9**

* Zendesk #2615 - problème lors de la suppression du HLS de l’écran de bureau

Ajout de la méthode clearVideo() à MediaPlayer. Efface le cadre vidéo affiché en effaçant AVStream de l’objet StageVideo. Doit être appelée uniquement si la vidéo est en pause et que replaceCurrentResource ou replaceCurrentItem doit être appelé avant que play() puisse être appelé à nouveau. 

* Zendesk #3169 - Mise à jour du lecteur de référence avec l’intégration d’Adobe Analytics

Le lecteur de référence a été mis à jour avec l’intégration d’Adobe Analytics.

* Zendesk #3296 - Desktop HLS TVSDK - Publicités tierces VAST non lues

les types MIME pour le format HLS étaient sensibles à la casse, incorrects et modifiés afin qu’ils ne soient plus sensibles à la casse

**Version 1.4.8**

* Zendesk #2737 - Lecteur de bureau - Erreur 106000 (nécessite Flash Player 17.0.0.184)
* Zendesk #3007 - Publicités preroll n’apparaissant pas après la mise à jour vers Flash Player 17 (nécessite Flash Player 17.0.0.184)
* Zendesk #3085 - Desktop HLS Player lance une erreur 106000 après 60 secondes (nécessite Flash Player 17.0.0.184)

**Version 1.4.7**

* Zendesk #2760 - Balise DISCONTINUITY ignorée en mode TrickPlay (nécessite Flash Player version 17.0.0.158)
* Zendesk #2760 - Balise DISCONTINUITY ignorée en mode TrickPlay (nécessite Flash Player version 17.0.0.158)

**Version 1.4.6**

* Zendesk #2652 - Documentation Auditude pour HLS de bureau, Media_id Clarified Auditude pour la documentation HLS de bureau

**Version 1.4.5**

* Zendesk #2256 - Accès à la liste de lecture principale, mise à jour du fichier PSDK pour distribuer des  de métadonnées minutées pour les balises abonnées sur la liste de lecture principale. (Flash Player version 17.0.0.134 requise)
* Zendesk #2417 - Lecteur essayant de télécharger des sous-titres avant le  de lecture, WebVTT utilisait la variable de numéro de segment incorrecte pour la correspondance des numéros de segment. Le bogue ne s’affichait que pour les médias dont les indices de segmentation commençaient à zéro. (Flash Player version 17.0.0.134 requise)
* Zendesk #2537 - Le lecteur Flash se bloque lors de l’utilisation du module externe pepper avec Chrome (nécessite Flash Player version 17.0.0.134)
* Zendesk #2547 - Sous-titres en arabe : Le texte doit être aligné à droite (nécessite Flash Player version 17.0.0.134).

**Version 1.4.4**

* Zendesk #1561 - Objet: `[Adobe Primetime]` Mise à jour : Prise en charge du basculement sur incident basé sur le client HLS pour le-DATE-TIME dans le PSDK de bureau (nécessite Flash Player version 16.0.0.305 ou ultérieure)
* Zendesk #2197 - `[Ads]` Suivi des erreurs et des erreurs
* Zendesk #2286 - Demande de fonctionnalités : Fournir des informations sur l&#39;état du chargement des publicités (VPAID)
* Zendesk #2285 - Demande de fonctionnalités : Ignorer la publicité après une durée de temporisation spécifiée
* Bogue #3921755 - Mise à jour de la bibliothèque OpenSSL vers la version 1.0.1L dans Flash Player (nécessite Flash Player version 16.0.0.305 ou ultérieure)

**Version 1.4.2**

* Zendesk #1303 - Décalage vertical pour les sous-titres codés (nécessite Flash Player version 16.0.0.235 ou supérieure, date de publication prévue : Décembre 2014)
* Zendesk #1870 - Sous-titrage fermé activé et désactivé (nécessite Flash Player version 16.0.0.235 ou supérieure, date de publication prévue : Décembre 2014)
* Zendesk #2110 - La lecture reste bloquée après avoir essayé d’entrer en mode plein écran pendant une publicité VPAID (nécessite Flash Player version 16.0.0.235 ou supérieure, date de publication prévue : Décembre 2014)
* Zendesk #2199 - `[VPAID]` Le lecteur ne répond pas lors de la recherche d’une coupure publicitaire passée.
* Zendesk #2358 - Objet: Données `[Analytics]` de chapitre incorrectes

**Version 1.4.1**

* Mise à jour de l’API Blackouts pour qu’elle soit compatible avec la mise en oeuvre d’Android et d’iOS.

**Version 1.4.0**

* Zendesk #1024 - Fonction permettant de supprimer une publicité du flux via le manifeste
* Zendesk #1423 - L’échec de la lecture HLS verrouille Flash Player (aucune erreur n’est signalée)
* Zendesk #1674 - ClosedCaption Ne s’affiche pas, la légende 708 s’affiche correctement lorsque les codes ETX 0x03 sont manquants.

</p>
</details>

## Problèmes connus {#known-issues}

* Le sous-titrage codé ne fonctionne pas avec le contenu audio uniquement, car le système de sous-titrage a besoin de vidéo pour fonctionner.
Sans vidéo, il n’y a pas de dimension de fenêtre d’affichage et sans dimension de fenêtre d’affichage, vous ne pouvez pas afficher de graphiques pour les légendes.
* L’intégrité du flux est légèrement plus lente dans Google Chrome en raison des restrictions du sandbox Chrome.
* Dans TVSDK 1.4, si vous désactivez autoPlay, une erreur DRM peut se produire lorsque le lecteur reste inactif pendant au moins une minute. Pour contourner ce problème, lorsque vous désactivez autoPlay mais que vous préchargez des fichiers, modifiez `ReferenceCore.as` le contenu de `onPlaybackManagerPrepared`:

>if (_playbackManager.autoPlay) {
>_playbackManager.play();
>} else {
>_playbackManager.play();
>_playbackManager.pause();
>}

* **Version 1.4.13** PTPLAY-8501 - Lorsque VMAP renvoie deux publicités MP4 directes non transcodées, la même publicité de automne est lue deux fois.

* **Version 1.4.2** Dans la version 16 de Flash Player, un problème a été identifié avec la logique de &quot;basculement&quot; ABR, une fois que le lecteur est entré dans un de mise en mémoire tampon vide. Le problème empêche le débit de s’arrêter dans une bande passante incorrecte  le  une fois que le lecteur est en état de mise en mémoire tampon. Pour résoudre ce problème, demandez à votre application de définir le paramètre `BufferControlParameters.initialBufferTime` de manière à ce qu’il soit le même que `BufferControlParameters.playbackBufferTime` temporairement pendant l’état de mise en mémoire tampon (c’est-à-dire sur un `BufferEvent.BUFFERING_BEGIN` ), puis de le réinitialiser sur les valeurs définies sur `BufferEvent.BUFFERING_END` le . Le correctif de ce problème sera disponible dans la prochaine version du correctif de Flash Player version 16.

* **Version 1.4.0**

   * PTPLAY-1634 - La même balise Abonné a des horodatages différents dans différentes fenêtres dynamiques. Lorsque les fenêtres dynamiques se déplacent, la même balise dans chacune d’elles doit avoir les mêmes horodatages. Cependant, il arrive que les mêmes balises aient des horodatages différents.
   * PTPLAY-28 - La chronologie de MediaPlayer n’inclut pas les pauses vides.
   * Un fichier de stratégie interdomaines (crossdomain.xml) est requis pour l’autorisation de diffusion en continu de contenu à partir d’un autre domaine. [Définition d’un fichier crossdomain.xml pour la diffusion en flux continu](https://www.adobe.com/devnet/adobe-media-server/articles/cross-domain-xml-for-streaming.html)HTTP.
   * Bogue n° 3694203 - Dans un flux DVR, la recherche depuis un flux mid-roll en cours de lecture vers un autre signal publicitaire mid-roll peut entraîner un blocage du navigateur.
   * Bogue #3753725 - selectPolicyForSeekIntoAd ne prend pas en compte si la coupure publicitaire a été visionnée
   * Bogue #3754529 - Les publicités preroll ne sont pas supprimées du flux lors de la recherche dans un flux DVR en direct.
   * Bogue #3761896 - Si la recherche est autorisée pendant la lecture de la publicité, les marqueurs publicitaires se ajustent à nouveau après la recherche. La solution consiste à ne pas utiliser le rappel ITEM_UPDATED lors de la recherche.
   * Bogue n° 3779889 - L’appel complet n’est pas effectué lorsque vous atteignez la fin de la lecture de l’astuce dans les analyses vidéo.
   * Bogue #VA-779 - Le de changement de débit  la pulsation n’est pas envoyé pour l’amélioration des analyses vidéo avec la mise en oeuvre de référence de la prise en charge de la pulsation - La lecture de la vidéo n’est pas implémentée dans l’exemple d’application.

## Ressources utiles {#helpful-resources}

* Reportez-vous à la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.
