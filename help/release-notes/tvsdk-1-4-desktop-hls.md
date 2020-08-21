---
title: Notes de mise à jour de TVSDK 1.4 pour Desktop HLS
seo-title: Notes de mise à jour de TVSDK 1.4 pour Desktop HLS
description: Les notes de mise à jour TVSDK for Desktop HLS décrivent les nouveautés ou les modifications, les problèmes résolus et connus de TVSDK DHLS.
seo-description: Les notes de mise à jour TVSDK for Desktop HLS décrivent les nouveautés ou les modifications, les problèmes résolus et connus de TVSDK DHLS.
uuid: 84da27b7-299b-478d-88f5-ef943f0a8321
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: e4437a26-9454-4da1-ae87-0fce664aac3d
translation-type: tm+mt
source-git-commit: 6da7d597503d98875735c54e9a794f8171ad408b
workflow-type: tm+mt
source-wordcount: '5222'
ht-degree: 0%

---


# Notes de mise à jour de TVSDK 1.4 pour Desktop HLS {#tvsdk-for-desktop-hls-release-notes}

Les notes de mise à jour TVSDK for Desktop HLS décrivent les nouveautés ou les modifications, les problèmes résolus et connus de TVSDK DHLS.

## Nouvelles fonctionnalités {#new-features}

**1.4.31**

* **Prise en charge multiCDN pour les annonces CRS**

   * Par défaut, toutes les ressources transcodées sont hébergées sur le réseau de diffusion de contenu détenu par l’Adobe sur Akamai. Avec la dernière version, Adobe Creative Repackaging Service (CRS) permet de télécharger les éléments créatifs transcodés sur plusieurs réseaux de diffusion de contenu selon les spécifications du client.
   * De nouvelles API sont ajoutées à TVSDK pour permettre la spécification de l’URL créative CRS finale lorsque l’URL par défaut n’est pas utilisée. Consultez la documentation pour savoir comment utiliser ces nouvelles API.

### Nouvelles fonctionnalités des versions précédentes {#new-features-previous}

**1.4.30**

* **Mesures de facturation**

Afin d’accommoder les clients qui souhaitent payer uniquement pour ce qu’ils utilisent, plutôt qu’un taux fixe, quelle que soit leur utilisation réelle, l’Adobe collecte des mesures d’utilisation et les utilise pour déterminer le montant à facturer aux clients.

**1.4.24**

* **Connexion réseau persistante**

Important : Vous devez avoir installé au moins Adobe Flash Player version 22 ou ultérieure.
Les connexions réseau persistantes créent et stockent une liste interne de connexions réseau qui peuvent être réutilisées pour plusieurs requêtes, au lieu d&#39;ouvrir une nouvelle connexion pour chaque requête réseau. Les connexions réseau persistantes doivent augmenter l&#39;efficacité et réduire la latence de votre code réseau.

Dans cette version, cette fonctionnalité n’est pas prise en charge dans Apple Safari et Mozilla Firefox sur Mac.

**1.4.19**

* Prise en charge de l’intégrité du flux pour les annonces VPAID.
* Activation de l’option de tabulation silencieuse dans le lecteur de Flash FP 20.0.0.267 pour Firefox 42 et versions ultérieures en corrigeant le problème de blocage.

**1.4.18**

* Primetime Desktop HLS TVSDK prend désormais en charge les éléments créatifs SWF linéaires VPAID 2.0 afin de permettre une expérience d’affichage d’annonces interactives enrichie en continu.

**1.4.10**

* **Retournement de publicité, chaînement de banqueroute dans la logique de sélection des publicités (Zendesk #3103)** Pour les publicités VAST (créatifs) avec la règle de secours activée, TVSDK traite une publicité avec un type MIME non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.

Pour plus d’informations, voir Reprise [publicitaire pour les annonces VAST et VMAP](../programming/tvsdk-1.4-for-android/ad-insertion/ad-fallback/android-1.4-ad-fallback.md).

**1.4.8**

* **Mise à jour de la bibliothèque Video Heartbeats Library (VHL) vers la version 1.5**

   * Capacité d’envoyer des métadonnées avec un début vidéo et/ou un début vidéo/publicitaire/chapitre en tant que données contextuelles
   * Moins de trafic réseau : les pulsations sont moins nombreuses en moyenne et de taille plus petite.

**1.4.7**

* **Prise en charge de l’individualisation sur site**

Prise en charge des installations sur site de l’Adobe Individualization Server pour personnaliser la demande d’individualisation du client afin d’accéder à un autre point de terminaison.

**1.4.6**

* **Exemple de chiffrement AES (nécessite la version 17.0.0.134 du Flash Player)**

Le chiffrement AES basé sur des exemples est désormais pris en charge.

**1.4.2**

* **Mise à jour de la bibliothèque Video Heartbeats Library (VHL) vers la version 1.4.0.1**

   * ajouté la possibilité de regrouper différents cas d’utilisation des analyses, provenant d’autres kits SDK ou lecteurs, avec Adobe Analytics Video Essentials.
   * Le suivi des publicités a été optimisé en supprimant les méthodes trackAdBreakStart et trackAdBreakComplete. La coupure publicitaire est déduite des appels des méthodes trackAdStart et trackAdComplete.
   * La propriété playhead n’est plus nécessaire lors du suivi des publicités.

**1.4.0**

* **Signalisation par coupure de courant avec remplacement** de contenu alternatif Dans le cadre de la mise à jour TVSDK 1.4, TVSDK prend également en charge la prise en charge et le retour des coupures régionales par rapport au contenu linéaire. TVSDK peut maintenant traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d&#39;arrêt même lorsque la programmation alternative est présentée à la programmation originale.

* **Supprimez/Remplacez les publicités** C3 Maintenant, aucune préparation supplémentaire n’est nécessaire pour insérer dynamiquement de nouvelles publicités dans les ressources vidéo à la demande (VOD) qui sortent de la fenêtre C3. TVSDK fournit désormais une API permettant de supprimer des plages de contenu personnalisées et d’insérer dynamiquement de nouvelles publicités. Cette nouvelle fonctionnalité puissante est également utile dans les cas où du contenu en direct/linéaire est diffusé pendant la diffusion et est immédiatement retiré pour être utilisé comme contenu à la demande sans le temps nécessaire pour &quot;nettoyer&quot; la ressource.

## Problèmes résolus {#resolved-issues}

>[!NOTE]
>
>Tous les clients TVSDK qui utilisent CRS sont fortement encouragés à effectuer la mise à niveau vers au moins TVSDK 1.4.32 sur iOS, Android et Desktop HLS. Cette mise à niveau remplacera la mise en oeuvre de l’application existante. Après la mise à niveau, recherchez les demandes d’URL créatives CRS dans un outil proxy (Charles, par exemple) pour vérifier que la version du chemin d’accès reflète la version 3.1. Par exemple,
>
>`https://adunit.cdn.auditude.com/assets/3p/v3.1/218747/94b/c1b/94bc1b964cc67e115a5a6781c7329b90_ee92607938ffff46b083121f044c2746.m3u8`

**Version 1.4.41**

* Zendesk #33777 - Le fichier SWF de jeton Localhost pour la version de distribution DHLS a expiré.

   Mise à jour du jeton localhost pour la démonstration PMP sur DHLS.

### Problèmes résolus dans les versions précédentes {#resolved-issues-previous}

**Version 1.4.38** (891)

* Zendesk #30731 - TVSDK ne lit pas plusieurs publicités VPAID dans une AdBreak.

   Correction de la lecture de plusieurs annonces VPAID dans un AdBreak.

* Zendesk #29968 - Panneau d&#39;affichage Doublon.

   Le lecteur vidéo peut répéter le dernier segment d’une période lorsqu’un commutateur ABR se produit. En raison de cela, il arrive que le dernier segment de pré-lecture se répète. Ce problème a été résolu.

**Version 1.4.35** (879)

* Zendesk #26058 - Prend en charge les événements VPAID natifs

**Version 1.4.33** (873)

* Zendesk #21701 - Envoyez l’URL de création originale pour la demande CRS 1401 au lieu de l’URL normalisée.

   Le problème où des URL déjà reconditionnées sont demandées pour le transcodage a été corrigé, conformément aux exigences du serveur principal CRS.
* Zendesk #26197 - Compression anamorphique non rejouée dans la résolution d’affichage souhaitée.

   **Remarque**: Ce problème nécessite le lecteur de Flash version 24.0.0.194 ou ultérieure.

   Le problème d’utilisation des entrées manquantes dans les tableaux des proportions pour calculer la largeur de sortie a été corrigé.

* Zendesk #26840 - Échec de la détection HDCP sur IE11 + Windows7 après la deuxième tentative.

   **Remarque**: Ce problème nécessite Flash Player 24.0.0.218 ou version ultérieure.

   Ce problème a été résolu en modifiant le traitement de la file d’attente des messages principale d’AdobeCP afin qu’elle parcourt la file d’attente entière, plutôt que de se contenter de bloquer le tout premier message.

* Zendesk #27460 - Le nouveau compte Akamai ne peut pas gérer une demande CDN POST.

   Le nouveau compte CDN ne peut pas gérer une demande CDN POST. Ce problème a été résolu en mettant à jour le code afin que la demande d’annonce cdn.auditude.com soit GET et non POST.
* Zendesk #27619 - Flash crash sous Windows 10

   **Remarque**: Ce problème nécessite Flash Player 24.0.0.218 ou version ultérieure.

   Ce problème a été résolu en empêchant un problème suite à de longues URL.

* Zendesk #28218 - Le événement de suivi ne se déclenche pas pendant que l&#39;apposition du point de reprise

   Ce problème est le même que dans Zendesk #26592. Le problème en raison duquel les opérations de recherche étaient autorisées lorsque le lecteur multimédia était à l’état PRÉPARÉ pour les flux VOD a été résolu.

**Version 1.4.32** (867)

* Le événement de suivi Zendesk #26592 ne se déclenche pas lorsque la lecture début à partir du point de reprise.

Le code ne mettait pas à jour l’élément de coupure publicitaire preroll lorsque le point de reprise n’était pas zéro. Ce problème a été résolu en ajoutant une logique pour actualiser le code lorsque les débuts de la plage ne correspondent pas.

* Zendesk #27022 Les publicités ne sont pas lues la deuxième fois qu’une ressource est lue

Les exceptions aux méthodes de tableau ont été corrigées.

**Version 1.4.30** (855)

Les problèmes suivants ont été résolus pour TVSDK dans cette version :

* Zendesk #22898 - Les sous-titres manquants ne doivent pas entraîner l’échec de la lecture.

**Remarque**: Ce problème nécessite Flash Player 23.0.0.185 ou version ultérieure.

Ce problème a été résolu en permettant à TVSDK de poursuivre la lecture, même si le manifeste ne comporte pas le WebVTT M3U8, et en enregistrant simplement un avertissement.

* Zendesk #23454 - Les publicités tierces (VPAID) ne sont pas correctement gérées.

Ce problème a été résolu en gérant correctement les publicités VPAID en fonction des ID de contenu plutôt que des plages de temps.

* Zendesk #24528 - Mesures d’utilisation du SDK pour la facturation.

Important : Ce problème nécessite Flash Player 23.0.0.185 ou version ultérieure.

* Problème de sous-titrage Zendesk # 25432 lors du redimensionnement du lecteur.

Important : Ce problème nécessite Flash Player 23.0.0.185 ou version ultérieure.

Le code de mappage de texture d’affichage de la légende a été corrigé pour gérer correctement les coordonnées pendant le redimensionnement du lecteur.

La bibliothèque Video Heartbeat (VHL) a été mise à jour vers la version 1.5.9 afin de résoudre les problèmes suivants :

* Zendesk #23730 - Les mesures de débit sont vides

Ce problème a été résolu en suivant les changements de débit dans VideoAnalyticsTracker.

* ajouté une nouvelle API, assetDuration, à PTVideoAnalyticsTrackingMetadata pour mettre à jour la durée des ressources pour les flux en direct/linéaires.

**Version 1.4.28** (848)

* Zendesk #25027 - Auditude ne fonctionne pas dans la version de bureau 1.4.27

Ce problème a été résolu en ajoutant le code permettant de vérifier AUDITUDE_METADATA_KEY et en rendant interchangeables AUDITUDE_METADATA_KEY et ADVERTISING_METADATA_KEY.

* Zendesk #24428 - Problème de mise en mémoire tampon fréquente lors de l’utilisation de TVSDK pour lire une archive HLS DRM

Ce problème a été résolu en prenant en compte le fait que, en l’absence de configuration de publicité, TVSDK peut accélérer le traitement en éliminant la suspension de publicité preroll et la suspension de réservation en direct sur la chronologie conçue pour synchroniser l’insertion de publicité.

* Zendesk #24344 - Désactivation des fichiers WebVTT pour améliorer les temps de début.

**Remarque**: Ce problème nécessite le lecteur de Flash 23 ou une version ultérieure.

Ce problème a été résolu en chargeant les fichiers WebVTT uniquement lorsque des légendes doivent être affichées.

* Zendesk #24994 - Le sous-titrage fermé est retiré du lecteur en revenant d&#39;une pause commerciale.

**Remarque**: Ce problème nécessite le lecteur de Flash 23 ou une version ultérieure.

Le code EOC fallacieux a provoqué la disparition de l’affichage de la légende. Ce problème a été résolu en forçant les codes de sous-titrage 608 RU2, RU3 et RU4 à fournir la visibilité correcte dans la principale fenêtre active.

**Version 1.4.27** (844)

* Zendesk #21554 - Balises d’erreur TVSDK non déclenchées pour le type d’application = video/mp4

Ce problème a été résolu en permettant à TVSDK d’effectuer un test ping sur les URL de suivi des erreurs correctes sur les formats de fichier non valides.

* Zendesk #23402 - Lecture de publicité incomplète

**Remarque**: Ce problème nécessite le lecteur de Flash 23 ou une version ultérieure.

Après avoir obtenu une erreur 404 sur certaines requêtes, un blocage peut se produire. Ce problème a été résolu en s&#39;assurant que la connexion ne s&#39;arrête pas pendant que la réponse est gérée. La résolution permet de s’assurer que les fichiers d’annonce VPAID ne sont pas comptabilisés incorrectement. Ils ne sont donc pas publiés pendant le téléchargement.

* Zendesk #23621 - La nouvelle tentative échoue sur les versions 400 et 404

**Remarque**: Ce problème nécessite le lecteur de Flash 23 ou une version ultérieure.

Correction d’un problème en raison duquel les métadonnées DRM étaient endommagées lors du basculement d’un profil à l’autre.

* Zendesk #23705 - Blocage des publicités vidéo pendant les pauses AdStitched

**Remarque**: Ce problème nécessite le lecteur de Flash 23 ou une version ultérieure.

Ce problème est le même que dans Zendesk #23621.

* Zendesk n° 23905 - Certaines coupures publicitaires ignorent les coupures publicitaires

**Remarque**: Ce problème nécessite le lecteur de Flash 23 ou une version ultérieure.

Le code réseau natif Windows a été corrigé afin de s&#39;assurer que les connexions ne ferment pas les poignées actuellement utilisées par d&#39;autres connexions.

* Billet #24029 - Les flux RSS HLS ne lisent pas toutes les publicités mid-roll dans le fichier .json mid-roll.

Ce problème a été résolu en permettant aux clients de définir des paramètres personnalisés séparément sur l&#39;instance Opportunité afin que les clients n&#39;aient pas à remplacer OpportunitéGenerator.

**Version 1.4.26** (839)

* Zendesk #18854 - Mettre à jour la logique de sélection créative en fonction des règles CRS
   * Assistance pour la mise à jour de la logique de sélection créative en fonction des règles CRS

* Zendesk #22725 - mise en oeuvre de playbackManager.beginPlayback() dans l’exemple d’application pour bureau

   * Corrigé en supprimant cet appel redondant à la fin de startPlaybackFromFlashVars lorsque la méthode est appelée à partir de setupVideo()

* Zendesk #22807 - Exception de référence nulle de SeekManager

   * Correction en fournissant la protection nécessaire du pointeur NULL à l’intérieur de SeekManager en rapport avec _dispatcher

* Zendesk #22822 - Mise en mémoire tampon fréquente lors de l’utilisation de TVSDK pour lire un HLS clair

   * Correction en supprimant l&#39;opportunité initiale générée par adSignalingModeOpportunityGenerator en l&#39;absence de publicité

* Zendesk #23378 - L’intégrité du flux bloque le fichier rules.xml

   * Corrigé en chargeant le fichier règles.xml via le flux de travaux d’intégrité du flux de travaux

**Version 1.4.24** (817)

* Zendesk #19851 - Lorsque le lecteur s’adapte à un débit différent, il saute quelques images dans le temps sur le nouveau débit binaire, ce qui rend l’expérience difficile.

**Remarque**: Ce problème nécessite Flash Player 22.0.0.175 ou version ultérieure.

Le problème de réinitialisation de l&#39;adaptateur DRM après le téléchargement d&#39;une petite partie d&#39;un segment n&#39;est pas restauré correctement a été résolu.

* Zendesk #20784 - Analytics : Déclenchement du contenu terminé pour les transitions de vidéo en direct

Ce problème a été résolu en ajoutant une API (trackVideoComplete) pour déclencher manuellement la fin du contenu au cours d’une session de suivi vidéo LINEAR/LIVE.

Les bibliothèques suivantes ont été mises à jour :

* Zendesk #21643 - Les publicités VPAID ne sont pas lues en intégralité

   * Bibliothèque AdobeMobile vers la version 4.10.0
   * Bibliothèque VHL vers 1.5.6
   * Bibliothèque VHL-Nielsen à 1.6.7

Ce problème a été résolu en utilisant une fenêtre d’affichage à hauteur nulle pour remplir l’étape de lecture d’une publicité VPAID.

* Zendesk #22110 - Analytics : ajouter un champ h:sc:ssl aux appels de suivi de pulsation

Les problèmes liés au protocole SSL ont été résolus et la bibliothèque VHL utilisée dans TVSDK a été mise à jour vers la dernière version.

* Zendesk #22608 - La vidéo affiche un écran noir par intermittence (nécessite le Flash Player 22.0.0.175 ou une version ultérieure)

Pendant le débit adaptatif, avec la limite de débit maximale, le rechargement de la vidéo affiche par intermittence un écran noir, même si le client voit les mises à jour pour se positionner, et que le client se comporte comme s’il lisait du contenu.

**Version 1.4.23** (809)

* Zendesk #2887 - Problème de saut d’annonce après la diffusion lorsque la logique de règle d’annonce s’appliquait à TVSDK

**Remarque**: Ce problème nécessite Flash Player 21.0.0.240 ou version ultérieure.

Correction du problème de saut des publicités post-roll lorsque la logique de la règle publicitaire était appliquée à TVSDK.

* Zendesk #19863 - Annonce avec fichier média VPAID ignoré

Si une vaste publicité intégrée comporte plusieurs fichiers multimédias avec une publicité VPAID comme première publicité, la publicité intégrée n’est pas lue pour les flux en direct. Ce problème a été résolu en sélectionnant un autre fichier multimédia à la place.

* Zendesk #21021 - Liaison tardive de l’audio qui entraîne des répétitions de segments audio

**Remarque**: Ce problème nécessite Flash Player 21.0.0.240 ou version ultérieure.

Le problème de répétition audio a été corrigé.

* Zendesk #21125 - Retour d’une coupure publicitaire linéaire/en direct tôt

**Remarque**: Ce problème nécessite Flash Player 21.0.0.240 ou version ultérieure.

Cette version permet de revenir d’une coupure publicitaire tôt avant que la coupure publicitaire ne soit lue jusqu’à la fin. Un retour anticipé est indiqué par le biais d’une balise de manifeste personnalisée.

* Zendesk n° 21369 La liaison tardive de données audio provoque une incohérence

**Remarque**: Ce problème nécessite Flash Player 21.0.0.240 ou version ultérieure.

Le problème de répétition audio qui a été corrigé a également résolu ce problème.

* Zendesk #21760, 20921 - Desynchronisation de vidéos audio sur Seek.

**Remarque**: Ce problème nécessite Flash Player 21.0.0.240 ou version ultérieure.

Le problème de répétition audio a été corrigé.

* Zendesk #22024 - Erreur lors de l’exécution de TVSDK

Le problème en raison duquel le lecteur de référence ne lisait aucun flux et renvoyait une exception au début a été résolu.

**Version 1.4.22** (791)

* Zendesk #17580 - Erreur d’exécution Primetime avec le code 3357

**Remarque**: Ce problème nécessite le lecteur de Flash version 21.0.0.197 ou ultérieure.

Les erreurs 3357 aléatoires survenues lors de l’initialisation correcte de deviceID lors de l’appel de storeVoucher() ont été corrigées.

* Zendesk #21334 - Valeur du délai d’expiration de la demande d’annonce TVSDK pour les demandes d’annonce tierces

Dans cette version, le délai d’attente global de la demande d’annonce a été ajouté.

**Version 1.4.21** (782)

* Zendesk #19580 TVSDK attend la fin du programme de résolution de contenu avant d’envoyer des `PTTimedMetadataChangedNotification` notifications

**Remarque**: Ce problème nécessite Flash Player 21.0.0.182 ou version ultérieure.

Ce problème a été résolu dans le lecteur de référence pour ordinateur en permettant de définir des balises publicitaires et en ajoutant un générateur d’opportunités personnalisé qui montre comment s’abonner à des indices personnalisés et comment traiter ces indices dans un fichier VOD.

* Zendesk #20806 Les futures publicités milieu-roll dans la fenêtre DVR ne se déclenchent pas après le permutation de cames

**Remarque**: Ce problème nécessite Flash Player 21.0.0.182 ou version ultérieure.

Ce problème a été résolu en mettant à jour l’application pour définir _resource.metadata.setValue(DefaultMetadataKeys.ENABLE_LIVE_PREROLL, &quot;false&quot;) afin de désactiver l’insertion de publicités preroll dans un échange PIP et, par conséquent, aucune opportunité pre-roll n’est générée.

Une fonctionnalité de tri a été introduite pour corriger l’emplacement d’annonce non séquentiel qui résultait en une durée de contenu principal négative.

* Zendesk #20522 : Impossible d&#39;ignorer les publicités VPAID 2.0

**Remarque**: Ce problème nécessite Flash Player 21.0.0.182 ou version ultérieure.

* Ce problème a été résolu en ignorant les publicités VPAID pendant la remise des publicités.
* Lorsque la stratégie adbreak est définie sur saut, les événements de coupures publicitaires et publicitaires sont toujours distribués. L’état du lecteur est incohérent.

Ce problème a été résolu afin de se comporter correctement et de ne pas distribuer de événements lorsque la coupure publicitaire est ignorée.

* Zendesk #20955 Définition de paires clé-valeur dans la propriété customParameters via le générateur d’opportunités

**Remarque**: Ce problème nécessite Flash Player 21.0.0.182 ou version ultérieure.

La requête Auditude analyse les paramètres AuditudeSettings pour les paramètres personnalisés lors de la création d&#39;une unité publicitaire pour les requêtes publicitaires.

Ce comportement a été modifié afin d’inclure des paramètres personnalisés de l’objet Opportunité dans la requête. En outre, plusieurs opportunités avec différents paramètres personnalisés ne peuvent pas être incluses dans une seule requête Auditude.

* Zendesk #21227 - m3u8 ne joue pas de manière cohérente

**Remarque**: Ce problème nécessite Flash Player 21.0.0.211 ou version ultérieure.

Ce problème a été résolu en permettant à TVSDK d’ignorer le manifeste (sous-profils HLS) qui contient le codec AC3 que TVSDK ne prend pas en charge (surround).

**Version 1.4.20** (762)

* Zendesk #19181 - Les trompes jouent vite en avant pour un point de vie verrouille le flux.

**Remarque**: Ce problème nécessite Flash Player 20.0.0.306 ou version ultérieure.

* Zendesk #19286 - Un Flash Player s&#39;est écrasé alors qu&#39;il faisait des allers-retours dans un flux FER.

**Remarque**: Ce problème nécessite Flash Player 20.0.0.306 ou version ultérieure.

Les blocages occasionnels survenant lors de la recherche dans Google Chrome ont été résolus en arrêtant les requêtes, si les requêtes prennent trop de temps pour obtenir une réponse ou si le socket est en cours d’arrêt.

* Zendesk #19305 - Lecture choppy rencontrée lors de la lecture d’un flux avec des discontinuités A/V.

**Remarque**: Ce problème nécessite Flash Player 20.0.0.306 ou version ultérieure.

Ce problème a été résolu par le rapports d’un avertissement.

* Zendesk # 19359 - Flash Player s&#39;est écrasé à cause de la position de #EXT-X-FAXS-CM : dans le manifeste de niveau défini.

Ce problème a été résolu lorsque la balise #EXT-X-FAXS-CM apparaît dans la liste de lecture supérieure avant le débit ou les segments individuels dans la liste de lecture.

* Zendesk #19489 - Module externe d’étals Fast Forward to Live Point (flux en direct)

Ce problème est identique à celui de Zendesk #19181.

* Zendesk #19699 - TVSDK ne parvient pas à basculer entre les pistes de sous-titres WebVTT

Ce problème a été résolu en faisant le vidage du lecteur et en rechargeant le manifeste lorsqu’un suivi change et en corrigeant le problème de conversion de chaîne UTF8 qui affectait les noms de suivi des sous-titres WebVTT sur doublon d’octets.

**Version 1.4.19** (1.4.19.738)

* Zendesk #18234 - Flash Player se bloque en lisant les flux avec des chaînes Unicode en CC

Ce problème nécessite le Flash Player FP 20.0.0.267 ou une version ultérieure et a été résolu en gérant correctement la chaîne Unicode.

* Zendesk #18304 - Prise en charge de l’intégrité des flux pour les publicités VPAID

Cette fonctionnalité nécessite le Flash Player FP 20.0.0.267 ou une version ultérieure et a été introduite dans la version 1.4.19.

* Zendesk #18766 - Le lecteur de référence ne peut pas afficher les caractères unicode non latins dans les noms de pistes CC

Cette fonctionnalité nécessite le Flash Player FP 20.0.0.267 ou une version ultérieure et a été corrigée en gérant correctement la chaîne Unicode.

* Zendesk #18804 - Accident du lecteur dans Firefox 42

Ce problème nécessite le Flash Player FP 20.0.0.235 ou une version ultérieure et est identique à celui de Zendesk #18723.

* Zendesk #18864 - Flash Player de blocage du module externe complet

Ce problème nécessite le Flash Player FP 20.0.0.235 ou supérieur et est identique à Zendesk #18723.

* Zendesk #18998 - Si les horodatages audio et vidéo ne correspondent pas, un téléchargement sans fin de segments en cas de discontinuité s’est produit.

Ce problème a été résolu en ignorant l’intervalle entre les horodatages et en lisant simplement le contenu téléchargé.

* Zendesk #19093 - Les publicités intermédiaires ne peuvent être regardées qu’une seule fois avec du contenu en direct et en événement complet, mais ces publicités ne peuvent plus être regardées lors d’un transfert rapide ou d’une recherche après les publicités.

Dans le sélecteur de stratégie publicitaire par défaut de Primetime, si une publicité preroll est visionnée, la coupure publicitaire n’est pas déplacée à la position recherchée lorsque vous effectuez une recherche. Pour lire à nouveau la publicité, après la recherche, l’application doit remplacer la fonction selectAdBreaksToPlay().

* Zendesk #19101 - La conversion en publicités Midroll non résolues supprime l’emplacement de la publicité.

Ce problème a été résolu en permettant au lecteur de mettre à jour l’heure de playbackMetrics, la durée minimaleOpportunityTime et la chronologie.

* Zendesk #19102 - Problèmes avec le mode FER et astuces

Ce problème nécessite le Flash Player FP 20.0.0.267 ou une version ultérieure et a été résolu en définissant correctement le paramètre advertisingMetadata.adSignalingMode.

* Zendesk #19175 - Parfois, les publicités preroll ne s’affichent pas la première fois que le flux est lu.

Ce problème a été résolu en ajoutant une nouvelle API, adRequestTimeout, à AuditudeSettings pour un délai d’attente de demande d’annonce. Les utilisateurs peuvent désormais remplacer le délai d’expiration de la demande d’annonce des 10 s par défaut.

**Version 1.4.18** (1.4.18.722)

* Zendesk #3324 - Le rapports publicitaire Primetime ne suit pas les coupures publicitaires lorsqu’il n’y a aucun média publicitaire dans un VMAP.

Lorsqu’une coupure publicitaire est vide, le début de coupure publicitaire et les événements de suivi complets n’étaient pas en cours d’épinglage. Ce problème a été résolu en envoyant des pings de début de coupures publicitaires lors de coupures publicitaires vides, telles que VMAP AdBreak, avec un noeud AdSource valide.

**Version 1.4.17** (1.4.17.702)

* Zendesk #17168 - Les légendes n’apparaissent pas pendant environ 10 secondes après avoir basculé en visibilité.

Ce problème a été résolu en prenant en charge la balise EXT-X-MEDIA-TIME pour les fichiers de sous-titrage vtt.

* Zendesk #17983 - Le fait de ne pas télécharger de clés pour un manifeste provoque l&#39;échec de la lecture complète du manifeste

**Remarque**: Vous devez avoir au moins Flash Player FP 19.0.0.245 ou supérieur.

Lorsque vous lisez parfois du contenu en direct, il peut y avoir des clés non valides dans le manifeste (par exemple, pour les périodes d’interruption), mais d’autres plages de temps peuvent avoir des clés valides et seront toujours lues. Auparavant, lorsqu’une clé répertoriée dans un manifeste ne pouvait pas être téléchargée, l’intégralité du manifeste échouait. Désormais, le manifeste échoue uniquement lorsque toutes les clés répertoriées ne peuvent pas être téléchargées. Si certaines clés sont valides, mais que certaines d’entre elles n’ont pas pu être téléchargées, le contenu est lu. Nous échouerons encore si nous tentons de jouer un segment qui nécessite une clé que nous n&#39;avons pas.

* Zendesk #18554 - Intégrité du flux qui réduit les cookies dans certains cas

**Remarque**: Vous devez avoir au moins Flash Player FP 19.0.0.245 ou supérieur.

Correction d’un bogue dans le code de manipulation des cookies qui pouvait tronquer les valeurs des cookies.

**Version 1.4.16** (1.4.16.684)

* Zendesk #3732 - Ajoutez la prise en charge des proxies dans Chrome pour l’intégrité du flux (nécessite Flash Player FP 19.0.0.207 ou version ultérieure)

C&#39;est une amélioration.

* Zendesk #4244 - Problèmes de diffusion en continu lors du survol PTS

Ce problème a été résolu en détectant le roulement et en gérant la discontinuité par type de charge utile et non pas de manière générique.

* Zendesk #4487 - Suivi du Canal linéaire du contenu

Ce problème a été résolu en réinitialisant le suivi de pulsation vidéo au cours d’une session de lecture de flux linéaire.

* Zendesk #17427 - Adobe Stream Integrity not working through a proxy on Chrome (Win7) ()

**Remarque**: La résolution requiert le Flash Player FP 19.0.0.207 ou une version ultérieure.

Ce problème est le même que Zendesk #3732.

* Zendesk #17907 - Poignardage sur le flux en direct pHLS avec le Flash Player 19

**Remarque**: La résolution requiert le Flash Player FP 19.0.0.207 ou une version ultérieure.

Ce problème a été résolu en gérant les flux en direct dans lesquels les domaines des fichiers TS changent lors du rechargement du manifeste en direct et les fichiers ont été téléchargés deux fois.

* Zendesk #17931 - Le contenu HLS avec ardoise au début échoue à la lecture.

**Remarque**: La résolution requiert le Flash Player FP 19.0.0.207 ou une version ultérieure.

Le problème a été résolu en gérant les flux sans audio dans les 2 premières secondes du premier fichier TS.

* Zendesk #17934 - Échec de la diffusion en continu en direct avec le Flash 19.0.0.185

**Remarque**: La résolution requiert le Flash Player FP 19.0.0.207 ou une version ultérieure.

Le problème a été résolu en gérant les flux en direct avec le décalage temporel entre les images audio et vidéo sur les limites des segments.

* Zendesk #17973 - Dernier Flash Player 19.0.0.185 crashs au milieu du rouleau

**Remarque**: La résolution requiert le Flash Player FP 19.0.0.207 ou une version ultérieure.

Le problème a été résolu en gérant des fichiers audio non muxés avec insertion de publicités mid-roll. (Le commutateur d’analyseur se produit et, à tout moment de la lecture, le contenu s’transition à la publicité preroll mid, ou au milieu de la lecture de la publicité, etc.)

* Zendesk #18049 - crash du Flash 19 avec la version bêta de Firefox 42

Ce problème est identique à celui de Zendesk #17973.

**Version 1.4.15** (1.4.15.678)

* Zendesk #4377 : Incendez le événement AD_BREAK_SKIPPED lors de l’abandon d’une coupure publicitaire en raison de la stratégie publicitaire.

Le correctif consistait à ajouter AD_BREAK_SKIPPED si une publicité est ignorée.

* Zendesk #4496 - Intégrité du flux : Erreur 102100 avec redirections vers des flux jetés.

Le correctif consistait à ajouter la prise en charge de la définition de la propriété AVNetworkConfiguration useCookieHeaderForAllRequests via TVSDK.

* Zendesk #17179 - Le lecteur de Flash se bloque sur plusieurs modifications SAP pour le contenu chiffré.

Un blocage au cours de la lecture de certains contenus chiffrés a été corrigé.

**Remarque**: Le correctif nécessite le Flash Player 19.0.0.200 ou supérieur.

* Zendesk #17499 - comment ne pas supprimer les midrolls après la surveillance mais supprimer les pré-péages du contenu frelaté

ajouté un type à AdBreakTimelineItem (AdBreakTimelineItem.placementType) afin qu’AdPolicySelector puisse renvoyer une stratégie différente pour le contenu preroll, mid-roll et post-roll.

* Zendesk #17665 - Bandwidth Throttling

Le correctif consistait à supprimer la logique permettant de modifier la taille de la mémoire tampon de cible en taille de mémoire tampon initiale au début de la mise en mémoire tampon.

**Version 1.14.14** (1.4.14.771)

* Zendesk #17363 - Correction de la documentation README pour le lecteur de référence

   * Précisez les instructions de téléchargement et d’installation de playerglobal.swc.
   * ajoutez les instructions pour mettre à jour la configuration du projet avec une version spécifique du lecteur Flash.
   * Mettez à jour la configuration du projet AdvertisingOverlay pour utiliser la version minimale du lecteur.
   * Mise à jour de la configuration de projet de base Reference pour utiliser la version 11.9 du lecteur spécifique

* Zendesk #17471 - Le Joueur gèle

Correction partielle d’un problème en raison duquel une publicité n’est pas lue depuis le début après la recherche.

* Zendesk #17496 - Le Podbuster n&#39;est pas résolu lors de la recherche en retour dans la fenêtre du RVR

Fournissez des paramètres personnalisés pour chaque coupure publicitaire.

**Version 1.4.13** (1.4.13.660)

* Zendesk #4037 - Aucune erreur de Profil utilisable (nécessite le Flash Player 18.0.0.232 ou version ultérieure)

correction d’un problème d’analyse d’URL lorsque le paramètre de requête contient &quot;http&quot;

* Zendesk #4260 - Flash Player 18 se bloque dans IE11 (nécessite le Flash Player 18.0.0.232 ou supérieur)

Correction d’un blocage lors de la lecture d’une vidéo en mode plein écran avec IE11.

* Zendesk #4262 - Le lecteur Adobe Primetime se bloque sur Windows 10 (nécessite le Flash Player 18.0.0.232 ou supérieur)

Correction d’un blocage lors de la lecture d’une vidéo en mode plein écran avec FireFox sous Windows.

* Zendesk #4279 - HLS TVSDK et insertion -302 problème de redirection sur iOS et sur le bureau

Correction d’un problème en raison duquel une URL ne faisait pas reconnaître correctement son type car elle n’avait pas d’extension.

* Zendesk n° 4306 - Flash Player crash lors du passage en plein écran sous Windows uniquement (nécessite le Flash Player 18.0.0.232 ou supérieur)

Correction d’un blocage lors de la lecture d’une vidéo en mode plein écran sous Windows.

* Zendesk #4480 - événements de balises ID3 manquants (nécessite le Flash Player 18.0.0.232 ou version ultérieure)

**1.4.12 **(1.4.12.656)

* Zendesk #2751 - CSAI et CRS | Améliorer : Gérez les éléments dynamiques dans certaines URL de fichier multimédia.

Mise à jour de Creative Repackaging Service afin de gérer correctement les publicités avec des URL créatives dynamiques.

* PTPLAY - 2114 - Prise en charge de la lecture MP4.

La lecture de base du contenu MP4 est désormais prise en charge, y compris la lecture, la mise en pause et la recherche.

Le Flash Player 18.0.0.225 ou supérieur est requis pour les éléments suivants :

* Zendesk #3992 - Vitesses TrickPlay supplémentaires.

TrickPlay accepte désormais des taux supérieurs à 16x : +/- 32, +/-64 et +/-128.

* Zendesk #3113 - Le module Flash Player se bloque

Correction d’un blocage lors de la tentative de lecture d’une publicité de redirection sur Mac Firefox.

* Zendesk #4037 - Aucune erreur de Profil utilisable
* Zendesk #4262 - Le lecteur Adobe Primetime se bloque sur Windows 10

Correction d’un blocage dans Windows Firefox lors de la lecture en mode plein écran.

**Version 1.4.11** (1.4.11.648)

* Zendesk #1869 - Problème de modification de la taille de la police (nécessite le Flash Player 18.0.0.200)

Autorisez l’utilisation des tailles de légende dans le code de légende WebVTT.

* Zendesk #3113 - Flash Player Plugin Crashing (nécessite Flash Player 18.0.0.200)
* Zendesk #3268 - Bureau : Débuts du lecteur vidéo clignotant après +- 40/50 secondes et débuts noirs après +- 90 secondes (Flash Player 18.0.0.200 requis)

Correction d’un bogue vidéo d’étape.

* Zendesk #3670 - Erreur INVALID_PARAMETER dans VOD lors de la recherche dans le lecteur de référence (nécessite le Flash Player 18.0.0.200)

InvalidateProfiles dans ThreadSeek lorsqu’une nouvelle période est détectée.

* Zendesk #3896 - Flash Player de blocage avec l’intégrité du flux définie sur ON sur ON sur Chrome (nécessite le Flash Player 18.0.0.200)

Correction d&#39;un blocage en mode réseau natif dans pepper

* Zendesk #3905 - Le lecteur TVSDK ne se charge pas lorsqu’il est hébergé sur CDN

Correction de problèmes de recherche de jeton générique lorsque pageDomain est différent du domaine swf.

**Version 1.4.10** (1.4.10.642)

* Zendesk #3249 - Le lecteur web TVSDK bloque le Flash sur Firefox

Correction d’un blocage occasionnel du Flash Player avec Firefox sur Mac lorsqu’un flux, lu sur un moniteur externe, basculait vers un flux à débit plus élevé.(nécessite le Flash Player 18.0.0.160)

* Zendesk #3268 - Bureau : Débuts du lecteur vidéo clignotant après `+-` 40/50 secondes et débuts noirs après `+-` 90 secondes

Correction d’un problème sur Mac Chrome en raison duquel le flux début à scintiller et finit par devenir noir. (nécessite le Flash Player 18.0.0.161)

* Zendesk #3304 - Macro VAST 3.0 `[ERRORCODE]` non renseignée

   * le code d’erreur 400 sera affiché si la publicité intégrée comporte un élément créatif incorrect.
   * `[ERRORCODE]` macro sera encodée dans l&#39;URL

* Zendesk #3601 - Demande d&#39;amélioration : Gestion des compagnons d&#39;enveloppement

   * TVSDK affiche le compagnon d&#39;enveloppes qui contient des ressources (html, iframe ou static ) se ferme à la ligne d&#39;entrée. (si la ligne d’entrée ne contient pas une pour cette taille)
   * Les compagnons d&#39;enveloppes avec ressource, à moins qu&#39;ils ne soient utilisés pour l&#39;affichage, seront ignorés. (non utilisé pour le suivi)
   * Seuls les compagnons d&#39;enveloppe sans ressource seront utilisés à des fins de suivi. ( compagnon wrapper ne contenant que le suivi )

**Version 1.4.9**

* Zendesk #2615 - problème de suppression de la vue HLS de l&#39;affichage sur ordinateur de bureau

Méthode clearVideo() Ajoutée à MediaPlayer. Efface la trame vidéo affichée en effaçant AVStream de l&#39;objet StageVideo. Doit être appelé uniquement si la vidéo est en pause et replaceCurrentResource ou replaceCurrentItem doit être appelé avant que play() puisse être appelé à nouveau.

* Zendesk #3169 - Mise à jour du lecteur de référence avec l’intégration Adobe Analytics

Le lecteur de référence a été mis à jour avec l’intégration Adobe Analytics.

* Zendesk #3296 - Desktop HLS TVSDK - Publicités tierces VAST non lues

les types mime pour le format HLS étaient sensibles à la casse, ce n’était pas correct et a été modifié afin qu’ils ne soient plus sensibles à la casse.

**Version 1.4.8**

* Zendesk #2737 - Lecteur de bureau - Erreur 106000 (nécessite le Flash Player 17.0.0.184)
* Zendesk #3007 - Publicités preroll n’apparaissant pas après la mise à jour vers le Flash Player 17 (nécessite le Flash Player 17.0.0.184)
* Zendesk #3085 - Le lecteur HLS de bureau lance une erreur 106000 après 60 secondes (nécessite le Flash Player 17.0.0.184)

**Version 1.4.7**

* Zendesk #2760 - Balise DISCONTINUITY ignorée en mode TrickPlay (nécessite la version 17.0.0.158 du Flash Player)
* Zendesk #2760 - Balise DISCONTINUITY ignorée en mode TrickPlay (nécessite la version 17.0.0.158 du Flash Player)

**Version 1.4.6**

* Zendesk #2652 - Documentation Auditude pour HLS de bureau, Clarified Auditude media_id pour la documentation HLS de bureau

**Version 1.4.5**

* Zendesk #2256 - Accès à la liste de lecture du Principal, mise à jour du PSDK pour distribuer des événements de métadonnées temporisées pour les balises abonnées sur la liste de lecture principale. (nécessite la version 17.0.0.134 du Flash Player)
* Zendesk #2417 - Lecteur essayant de télécharger des sous-titres avant le début de lecture, WebVTT utilisait la variable de numéro de segment incorrecte pour la correspondance des numéros de segment. Le bogue ne s’affichait que pour les médias dont les indices de segmentation commençaient à zéro. (nécessite la version 17.0.0.134 du Flash Player)
* Zendesk #2537 - Le lecteur de Flash se bloque lors de l’utilisation du module externe pepper avec Chrome (nécessite la version 17.0.0.134 du Flash Player)
* Zendesk #2547 - Sous-titres arabes : Le texte doit être aligné à droite (nécessite la version 17.0.0.134 du Flash Player).

**Version 1.4.4**

* Zendesk #1561 - Objet : `[Adobe Primetime]` Mise à jour : Prise en charge du basculement sur incident basé sur le client HLS pour PROGRAMME-DATE-TIME dans le PSDK de bureau (nécessite la version 16.0.0.305 du Flash Player ou ultérieure)
* Zendesk #2197 - `[Ads]` Suivi des erreurs et des erreurs
* Zendesk #2286 - Demande de fonctionnalités : Fournir des informations sur l&#39;état du chargement des publicités (VPAID)
* Zendesk #2285 - Demande de fonctionnalités : Ignorer la publicité après une durée de temporisation spécifiée
* Bogue #3921755 - Mise à jour de la bibliothèque OpenSSL vers la version 1.0.1L en Flash Player (nécessite la version 16.0.0.305 du Flash Player ou une version ultérieure)

**Version 1.4.2**

* Zendesk #1303 - Décalage vertical pour légende fermée (nécessite la version 16.0.0.235 du Flash Player ou une version ultérieure, date de publication prévue : Décembre 2014)
* Zendesk #1870 - Sous-titrage fermé Activé et désactivé (nécessite la version 16.0.0.235 ou ultérieure du Flash Player, date de publication prévue : Décembre 2014)
* Zendesk #2110 - La lecture reste bloquée après avoir tenté d’entrer en mode plein écran pendant une publicité VPAID (nécessite la version 16.0.0.235 ou ultérieure du Flash Player, date de publication prévue : Décembre 2014)
* Zendesk #2199 - `[VPAID]` Le lecteur ne répond pas lorsqu’il recherche une coupure publicitaire passée
* Zendesk #2358 - Objet : `[Analytics]` Données de chapitre incorrectes

**Version 1.4.1**

* Mise à jour de l&#39;API Blackouts pour assurer la cohérence avec la mise en oeuvre d&#39;Android et d&#39;iOS.

**Version 1.4.0**

* Zendesk #1024 - Fonction permettant de supprimer une publicité du flux via un manifeste
* Zendesk #1423 - L’échec de lecture HLS verrouille le Flash Player (sans qu’aucune erreur ne soit signalée)
* Zendesk #1674 - ClosedCaption Ne s’affiche pas, la légende 708 correcte s’affiche lorsque les codes ETX 0x03 sont manquants.

</p>
</details>

## Problèmes connus {#known-issues}

* La légende fermée ne fonctionne pas avec le contenu audio uniquement, car le système de sous-titrage a besoin de vidéo pour fonctionner.
Sans vidéo, il n’y a pas de dimension de fenêtre d’affichage et sans dimension de fenêtre d’affichage, vous ne pouvez pas afficher de graphiques pour les légendes.
* L’intégrité du flux est légèrement plus lente dans Google Chrome en raison des restrictions du sandbox Chrome.
* Dans TVSDK 1.4, si vous désactivez autoPlay, une erreur DRM peut se produire lorsque le lecteur reste inactif pendant au moins une minute. Pour contourner ce problème, lorsque vous désactivez autoPlay mais que vous préchargez des ressources, modifiez `ReferenceCore.as` en modifiant le contenu de `onPlaybackManagerPrepared`:

```
if (_playbackManager.autoPlay) {
_playbackManager.play();
} else {
_playbackManager.play();
_playbackManager.pause();
}
```

* **Version 1.4.13** PTPLAY-8501 - Lorsque VMAP renvoie deux publicités MP4 directes non transcodées, la même publicité de repli est lue deux fois.

* **Version 1.4.2** Dans la version 16 du Flash Player, un problème a été identifié avec la logique ABR de &quot;basculement&quot;, une fois que le lecteur est entré dans un événement de mise en mémoire tampon vide. Le problème empêche le débit de basculer dans les environnements de bande passante inappropriés une fois que le lecteur est mis en mémoire tampon. Pour résoudre le problème, demandez à votre application de définir la valeur `BufferControlParameters.initialBufferTime` de manière à être la même que `BufferControlParameters.playbackBufferTime` temporairement pendant l’état de mise en mémoire tampon (c’est-à-dire sur un `BufferEvent.BUFFERING_BEGIN` événement), puis de la réinitialiser aux valeurs définies le `BufferEvent.BUFFERING_END` événement. Le correctif de ce problème sera disponible dans la prochaine version de correctif de Flash Player version 16.

* **Version 1.4.0**

   * PTPLAY-1634 - La même balise Abonné comporte différents horodatages dans différentes fenêtres dynamiques. Lorsque des fenêtres actives se déplacent, la même balise dans chacune d’elles doit comporter les mêmes horodatages. Cependant, il arrive que les mêmes balises aient des horodatages différents.
   * PTPLAY-28 - La chronologie MediaPlayer n’inclut pas les pauses vides.
   * Un fichier de stratégie interdomaines (crossdomain.xml) est requis pour l’autorisation de diffuser en continu du contenu à partir d’un autre domaine. [Définition d’un fichier crossdomain.xml pour la diffusion en flux continu](https://www.adobe.com/devnet/adobe-media-server/articles/cross-domain-xml-for-streaming.html)HTTP.
   * Bogue n° 3694203 - Dans un flux d’enregistrement vidéo numérique (DVR), la recherche d’une lecture intermédiaire dans une autre publicité intermédiaire peut entraîner un blocage du navigateur.
   * Bogue #3753725 - selectPolicyForSeekIntoAd ne prend pas en compte si la coupure publicitaire a été observée.
   * Bogue #3754529 - Les publicités preroll ne sont pas supprimées du flux lorsque vous effectuez une recherche dans un flux DVR en direct.
   * Bogue n° 3761896 - Si la recherche est autorisée pendant la lecture de la publicité, les marqueurs publicitaires se ajustent de nouveau après la recherche. La solution consiste à ne pas utiliser le rappel ITEM_UPDATED lors de la recherche.
   * Bogue #3779889 - L’appel complet n’est pas effectué lorsque vous atteignez la fin de la lecture de l’astuce dans les analyses vidéo.
   * Bogue #VA-779 - La pulsation du événement de changement de débit n’est pas envoyée pour l’analyse vidéo améliorée avec la mise en oeuvre de référence de la prise en charge de Heartbeat - La lecture de la vidéo n’est pas implémentée dans l’exemple d’application.

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète sur la page de formation et d’assistance [](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.
