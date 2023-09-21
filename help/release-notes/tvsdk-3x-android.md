---
title: Notes de mise à jour de TVSDK 3.15 pour Android
description: Les notes de mise à jour de TVSDK 3.15 pour Android décrivent les nouveautés ou les modifications, les problèmes résolus et connus et les problèmes d’appareil dans TVSDK Android 3.15
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '5516'
ht-degree: 0%

---

# Notes de mise à jour de TVSDK 3.15 pour Android {#tvsdk-for-android-release-notes}

Les notes de mise à jour de TVSDK 3.15 pour Android décrivent les nouveautés ou les modifications, les problèmes résolus et connus et les problèmes d’appareil dans TVSDK Android 3.15.

Le lecteur de référence Android est inclus avec Android TVSDK dans le répertoire samples/ de votre distribution. Le fichier README.md qui l’accompagne explique comment créer le lecteur de référence.

>[!NOTE]
>
>Pour créer correctement le lecteur de référence, comme décrit dans le fichier README.md distribué avec la version, veillez à effectuer les opérations suivantes :
>
>1. Téléchargez VideoHeartbeat.jar depuis [https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) (Bibliothèque VideoHeartbeat pour Android v2.0.0)
>1. Extrayez VideoHeartbeat.jar dans le dossier libs/ .

TVSDK pour Android offre de nombreuses améliorations de performances par rapport aux versions précédentes. Il offre une expérience d’affichage de haute qualité et comprend toutes les fonctionnalités de la version 1.4, à l’exception de la prise en charge de plusieurs CDN.

L’ensemble complet des fonctionnalités prises en charge et non prises en charge est présenté dans la section [Matrice de fonctionnalités](#feature-matrix) dans les notes de mise à jour.

## Android TVSDK 3.15

Cette version corrige le problème de blocage de l’application plusieurs fois lorsque la balise créative est manquante ou lorsque [!UICONTROL url CDATA] est vide dans [!UICONTROL VAST] réponse.

Pour en savoir plus sur les correctifs de bogues dans cette version et les versions précédentes, voir [problèmes résolus dans TVSDK pour Android](#resolved-issueszd).

### Nouvelles fonctionnalités et améliorations des versions précédentes

**Android TVSDK 3.14**

Cette version corrige le problème en raison duquel l’application se bloque lorsque [!UICONTROL CDATA] est vide pour l’un des [!UICONTROL ClickTracking], [!UICONTROL CustomClick] ou [!UICONTROL CompanionClickTracking] dans la réponse VAST.

**Android TVSDK 3.13**

Le flux DRM Widevine gèle ou montre des images noires sur les interrupteurs ABR sur les appareils FireTV, qui comprennent Fire TV 3e génération pendant et Fire TV Cube 1ère et 2e génération d&#39;appareils.

Pour résoudre ce problème, définissez l’API `MediaPlayer.flushVideoDecoderOnHeaderChange(true)` pour les appareils Fire TV spécifiés avant de lancer la lecture. La valeur par défaut est false.

**Android TVSDK 3.12**

Mise à jour de la version gradle de l’application Primetime Reference vers la version 5.6.4.

Pour configurer et exécuter l’application de référence à l’aide d’Android Studio, suivez les instructions du fichier ReadMe disponible avec le fichier zip TVSDK à l’adresse `TVSDK_Android_x.x.x.x/samples/PrimetimeReference/src/README.md`.

Les principaux problèmes des clients résolus dans la version actuelle sont mentionnés dans la section [problèmes résolus](#resolved-issues) .

**Android TVSDK 3.11**

* **Récupération autorisée de la zone d’en-tête spécifique au système de protection** - TVSDK permet la récupération de la zone d’en-tête spécifique au système de protection associée à la ressource de média chargée actuelle. Nouvelle API `getPSSH()` ajouté à `com.adobe.mediacore.drm.DRMManager`.

Pour plus d’informations, voir [Widevine DRM](../programming/tvsdk-3x-android-prog/android-3x-content-security/android-3x-drm-widevine.md).

**Android TVSDK 3.10**

Cette version était axée sur la résolution des principaux problèmes des clients, comme indiqué dans la section [problèmes résolus](#resolved-issues) .

**Android TVSDK 3.9**

* **Diffusion sécurisée via HTTPS** - Android TVSDK 3.9 a introduit les fonctionnalités de diffusion sécurisées via HTTPS pour diffuser du contenu en toute sécurité avec une échelle et des performances inégalées.

  Pour activer la diffusion sécurisée via HTTPS, une nouvelle API a été introduite dans `NetworkConfiguration` classe .

  `public void setForceHTTPS (boolean value)`

  `public boolean getIsForceHTTPS()`

**Android TVSDK 3.8**

* **Prise en charge de la fonction de prédéploiement avec coupure publicitaire partielle** - Grâce à cette amélioration, TVSDK 3.8 prend en charge les publicités preroll avec la fonctionnalité de coupure publicitaire partielle (PABI).

La publicité preroll, si elle est disponible, est lue, puis le contenu est lu à partir du point d’exécution qui imite l’expérience de la télévision en direct.

**Android TVSDK 3.7**

* Pour le contenu du test de version large, une nouvelle API `setMediaDrmCallback` dans la classe DRMManager est exposée pour remplacer l’implémentation par défaut de l’interface MediaDrmCallback .

  `public static void setMediaDrmCallback(MediaDrmCallback callback)`

* Correction d’une erreur AppCrash pour le non-traitement. `MediaPlayerEvent.ITEM_UPDATED` en couche C++ (Android 64 bits).

**Android TVSDK 3.6**

* **Amélioration de vos applications pour la configuration 64 bits** - Bibliothèque native `(libAVEAndroid.so)` est désormais mis à niveau et rendu disponible en deux versions. L’emplacement de la bibliothèque native d’armeabi (32 bits) existante a été modifié de `/framework/Player to /framework/Player/armeabi` et une bibliothèque arm64-v8a (64 bits) supplémentaire est introduite dans `/framework/Player/arm64-v8a.`

**Version 3.5**

* **Résolution de publicités juste à temps** - TVSDK 3.5 supprime la prise en charge des publicités lues de la chronologie.

* **Prise en charge activée de la lecture hors ligne** - Avec la lecture hors ligne, les utilisateurs peuvent désormais télécharger du contenu vidéo sur leurs appareils et le regarder lorsqu’ils ne sont pas connectés. Pour plus d’informations, voir &quot;[Lecture hors ligne avec Android](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_3.5.pdf).&quot;

**Version 3.4**

* TVSDK prend désormais en charge la lecture des diffusions CMAF pour les diffusions cryptées et ordinaires de la CBC.

**Version 3.3**

* **Modifications des API**

   * Une nouvelle API est ajoutée à `NetworkConfiguration::setNumOfTimesManifestRetryBeforeError(n)*` pour gérer les erreurs réseau et les dépassements de délai.
      * où (n) est le nombre de reprises.

**Version 3.2**

* **Prise en charge de la résolution d’annonce parallèle et du manifeste**

   * TVSDK 3.2 prend en charge la résolution simultanée, au lieu de la résolution séquentielle pour toutes les demandes d’annonces et coupures publicitaires, à l’exception de VMAP.

   * Tous les manifestes publicitaires d’une coupure publicitaire sont téléchargés simultanément.

* **Activation de la prise en charge de la résolution de l’annonce et du délai d’expiration du manifeste.**

   * Les utilisateurs peuvent désormais définir la valeur de délai d’expiration pour la résolution globale des publicités et les téléchargements de manifeste.  Dans le cas de VMAP, la valeur de délai d’expiration s’applique pour les coupures publicitaires individuelles, car toutes les coupures publicitaires sont résolues de manière séquentielle.

* **Introduction de nouvelles API dans la classe AdvertisingMetadata :**

   * `void setAdResolutionTimeout(int adResolutionTimeout)`

   * `int getAdResolutionTimeout()`

   * `void setAdManifestTimeout(int adManifestTimeout)`

   * `int getAdManifestTimeout()`

* **Suppression des API ci-dessous de la classe AdvertisingMetadata :**

   * `void setAdRequestTimeout(int adRequestTimeout)`

   * `int getAdRequestTimeout()`

* **Lecture activée des diffusions avec le codec audio AC3/EAC3**

   * `void alwaysUseAC3OnSupportedDevices(boolean val)` in `MediaPlayer` class

* **TVSDK prend en charge la lecture CMAF et de flux brut pour le widevine CTR crypté.**

* **La lecture des flux HEVC 4K est désormais prise en charge.**

* **Demandes d’appel de publicités parallèles** - TVSDK prérécupère désormais 20 demandes d’appel publicitaire en parallèle.

**Version 3.0**

* **TVSDK 3.0 prend en charge les flux de codage vidéo haute efficacité (HEVC).**

* **Juste à temps - Résolution des publicités plus proches des marqueurs publicitaires**
La résolution différée des publicités résout désormais chaque coupure publicitaire indépendamment. Auparavant, la résolution de la publicité était une approche en deux étapes : les preroll étaient résolus avant le début de la lecture et tous les créneaux mid/post-roll combinés après le démarrage de la lecture. Grâce à cette fonctionnalité améliorée, chaque coupure publicitaire est désormais résolue à un moment spécifique avant le point de repère publicitaire.

>[!NOTE]
>
>La résolution des publicités différées a désormais été modifiée pour être désactivée par défaut et doit explicitement être activée.

Une nouvelle API est ajoutée à `AdvertisingMetadata::setDelayAdLoadingTolerance` pour obtenir la tolérance de chargement de publicité différée associée à ces métadonnées de publicité.\
La recherche est désormais autorisée immédiatement après LA PRÉPARATION. La recherche sur plusieurs coupures publicitaires entraîne une résolution immédiate avant la fin de la recherche.\
Modes de signal `SERVER_MAP` et `MANIFEST_CUES` sont prises en charge.

Pour plus d’informations, voir [Guide du programmeur Android TVSDK 3.0](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/c-lazy-ad-resolving/c-lazy-ad-resolving.md) lors des modifications des API et des événements.

* **Mis à jour `targetSdkVersion` vers la dernière version**

Mis à jour `targetSdkVersion` de 19 à 27 pour un bon fonctionnement.

* **Placement.Type getPlacementType() est désormais une méthode sur l’interface TimelineMarker**

  Cette méthode renvoie un type d’emplacement de Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL ou Placement.Type.POST_ROLL. Si une coupure publicitaire n’est pas résolue, la méthode getDuration() de l’interface TimelineMarker renvoie 0.

**Version 2.5.6.**

* **TVSDK 2.5 prend en charge Android P.**

* **Activation de l’audio en arrière-plan**

  Pour activer la lecture audio lorsque l’application passe du premier plan à l’arrière-plan, l’application doit appeler `enableAudioPlaybackInBackground` API de MediaPlayer avec la valeur true en tant qu’argument lorsque le lecteur est à l’état PRÉPARÉ.

* **alwaysUseAudioOutputLatency(valeur booléenne) dans la classe MediaPlayer**

Lorsqu’elle est définie, utilisez la latence de sortie dans le calcul de l’horodatage audio.
Valeur des paramètres booléens : True utilise la latence de sortie audio dans le calcul de l’horodatage audio.

* **Optimisation pour obtenir la meilleure expérience de lecture même si la vitesse de bande passante diminue soudainement**

TVSDK annule désormais le téléchargement du segment en cours, si nécessaire, et passe dynamiquement au rendu approprié. Pour ce faire, il suffit de basculer facilement entre les débits sans interruption.

**Version 2.5.5**

* **Insertion de coupure publicitaire partielle**

  Expérience de type télévision consistant à se joindre au milieu d’une publicité sans déclencher le suivi pour la publicité visionnée partiellement.\
  Exemple : l’utilisateur se joint au milieu (à 40 secondes) d’une coupure publicitaire de 90 secondes composée de trois publicités de 30 secondes. Cette coupure intervient 10 secondes dans la seconde publicité.

   * La deuxième publicité est lue pendant la durée restante (20 secondes), suivie de la troisième publicité.

   * Les dispositifs de suivi des publicités pour la publicité partielle lue (deuxième publicité) ne sont pas déclenchés. Les dispositifs de suivi de la troisième publicité uniquement sont déclenchés.

* **Chargement sécurisé des publicités par HTTPS**

  Adobe Primetime offre une option pour demander le premier appel au serveur de publicités en temps réel et à CRS sur https.

* **Ajout d’AdSystem et d’un ID créatif aux requêtes CRS**

  Maintenant, incluez `AdSystem` et `CreativeId` comme nouveaux paramètres dans les requêtes 1401 et 1403.

* **API setEncodeUrlForTracking dans la classe NetworkConfiguration supprimée** car les caractères dangereux d’une URL doivent être codés.

**Version 2.5.4**

Android TVSDK v2.5.4 propose les mises à jour et modifications suivantes de l’API :

* Modifications de la valeur par défaut pour `WebViewDebbuging`

  `WebViewDebbuging` est définie sur `Fals`e par défaut. Pour l’activer, appelez `setWebContentsDebuggingEnabled(true)` dans l’application.

* **Mise à niveau de la version OpenSSL et Curl**

  Mise à jour de libcurl vers la version 7.57.0 et OpenSSL vers la version 1.0.2k.

* Accès au niveau de l’application pour l’objet de réponse VAST

  Introduction d’une nouvelle API `NetworkAdInfo::getVastXml()` qui donne accès à l’objet de réponse VAST à l’application.

**Version 2.5.3**

Android TVSDK v2.5.3 propose les mises à jour et modifications suivantes de l’API.

* Tous les clients TVSDK qui utilisent CRS sont encouragés à mettre à niveau leurs applications avec TVSDK 2.5.3.85 ou version ultérieure sur Android. Il s’agira d’un remplacement direct de la mise en oeuvre de l’application existante. Après la mise à niveau de TVSDK, recherchez les demandes d’URL créatives CRS dans un outil de proxy (ex : Charles) et vérifiez que le nom et la version de l’hôte dans le chemin d’accès se reflètent comme dans l’exemple de structure d’URL ci-dessous.

  `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* Agent utilisateur de TVSDK personnalisable : nous avons ajouté de nouvelles API pour personnaliser les agents utilisateurs.

   * `setCustomUserAgent(String value)`
   * `getCustomUserAgent()`

* Partager des cookies entre l’application Android et TVSDK : Android TVSDK prend désormais en charge l’accès aux cookies entre la couche JAVA (stockée dans CookieStore de l’application Android) et la couche C++ TVSDK. Désormais, il est possible de définir et/ou de modifier les cookies dans la couche C++ native, car ils seront exposés au magasin de cookies Java.

* Modifications des API :

   * Un nouvel événement `CookiesUpdatedEvent` est ajouté. Il est distribué par le lecteur multimédia lorsque son cookie est mis à jour.

   * Une nouvelle API est ajoutée à `NetworkConfiguration::set/ getCustomUserAgent()` pour utiliser un agent utilisateur personnalisé.

   * Une nouvelle API est ajoutée à `NetworkConfiguration::set/ getEncodedUrlForTracking` pour forcer le codage des caractères dangereux.

   * Une nouvelle API est ajoutée à `NetworkConfiguration::getNetworkDownVerificationUrl()` pour définir une URL de vérification du réseau en cas de basculement.

   * Une nouvelle propriété est ajoutée à `TextFormat::treatSpaceAsAlphaNum` qui définissent si l’espace doit être traité comme alphanumérique lors de l’affichage des légendes.

* Changements dans `SizeAvailableEvent`. Auparavant, `getHeight()` et `getWidth()` méthodes de `SizeAvailableEvent` dans la version 2.5.2, utilisé pour renvoyer la hauteur et la largeur d’image, qui ont été renvoyées par le format multimédia. Désormais, elle renvoie respectivement la hauteur et la largeur de sortie renvoyées par le décodeur.

* Changements du comportement de mise en mémoire tampon : le comportement de mise en mémoire tampon est modifié. Le développeur de l’application reste au responsable de ce qu’il souhaite faire en cas de mémoire tampon vide. La version 2.5.3 utilise la taille de la mémoire tampon de lecture en cas de vide de la mémoire tampon.

**Version 2.5.2**

Android TVSDK v2.5.2 propose des correctifs de bogues importants et quelques modifications de l’API.

**Version 2.5.1**

Nouvelles fonctionnalités importantes publiées dans Android 2.5.1.

* **Améliorations des performances -** La nouvelle architecture TVSDK 2.5.1 apporte un certain nombre d’améliorations de performances. Sur la base des statistiques d’une étude d’évaluation tierce, la nouvelle architecture offre une réduction de 5 fois le temps de démarrage et de 3,8 fois moins d’images perdues par rapport à la moyenne du secteur :

* **Instant on pour VOD et live -** Lorsque vous activez l’instantané, TVSDK s’initialise et met en mémoire tampon le média avant le début de la lecture. Comme vous pouvez lancer plusieurs instances MediaPlayerItemLoader simultanément en arrière-plan, vous pouvez mettre en mémoire tampon plusieurs flux. Lorsqu’un utilisateur modifie le canal et que la diffusion a été mise en mémoire tampon correctement, la lecture du nouveau canal commence immédiatement. TVSDK 2.5.1 prend également en charge Instant On pour **live** flux également. Les diffusions en direct sont mises en mémoire tampon à nouveau lorsque la fenêtre active se déplace.

* **Amélioration de la logique ABR -** La nouvelle logique ABR repose sur la longueur de la mémoire tampon, le taux de changement de la longueur de la mémoire tampon et la bande passante mesurée. Ainsi, l’ABR choisit le débit approprié lorsque la bande passante fluctue et optimise le nombre de fois où le changement de débit se produit réellement en surveillant la vitesse à laquelle la longueur de la mémoire tampon change.

* **Téléchargement de segment partiel/sous-segmentation -** TVSDK réduit davantage la taille de chaque fragment afin de lancer la lecture dès que possible. Le fragment ts doit disposer d’un cadre clé toutes les deux secondes.

* **Résolution publicitaire différée -** TVSDK n’attend pas la résolution des publicités non preroll avant de commencer la lecture, ce qui réduit le temps de démarrage. Les API telles que la recherche et le jeu vidéo ne sont toujours pas autorisées tant que toutes les publicités ne sont pas résolues. Ceci s’applique aux flux VOD utilisés avec l’interface de ligne de commande. Les opérations telles que la recherche et le transfert rapide ne sont pas autorisées tant que la résolution de la publicité n’est pas terminée. Pour les diffusions en direct, cette fonctionnalité ne peut pas être activée pour la résolution de publicités pendant un événement en direct.

* **Connexions réseau persistantes -** Cette fonctionnalité permet à TVSDK de créer et de stocker une liste interne de connexions réseau persistantes. Ces connexions sont réutilisées pour plusieurs requêtes, plutôt que d’ouvrir une nouvelle connexion pour chaque requête réseau, puis de la détruire par la suite. Cela augmente l’efficacité et réduit la latence du code de mise en réseau, ce qui entraîne des performances de lecture plus rapides.
Lorsque TVSDK ouvre une connexion, il demande au serveur de saisir *keep-alive* connexion. Certains serveurs peuvent ne pas prendre en charge ce type de connexion, auquel cas TVSDK revient à établir une connexion pour chaque demande. En outre, même si les connexions persistantes sont activées par défaut, TVSDK dispose désormais d’une option de configuration qui permet aux applications de désactiver les connexions persistantes si nécessaire.

* **Téléchargement parallèle -** Le téléchargement vidéo et audio en parallèle plutôt que dans les séries réduit les délais de démarrage. Cette fonctionnalité permet de lire les fichiers HLS Live et VOD, optimise l’utilisation de la bande passante disponible à partir d’un serveur, réduit la probabilité d’entrer dans des situations de mémoire tampon en cours d’exécution et réduit le délai entre le téléchargement et la lecture.

* **Téléchargements de publicités parallèles -** TVSDK récupère les publicités en parallèle à la lecture du contenu avant d’atteindre les coupures publicitaires, ce qui permet une lecture transparente des publicités et du contenu.

* **Lecture**

* **Lecture de contenu MP4 -** Il n’est pas nécessaire de recoder les extraits MP4 courts pour qu’ils soient lus dans TVSDK.

  >[!NOTE]
  >
  >Le changement ABR, la lecture de l’astuce, l’insertion de publicités, la liaison audio tardive et la sous-segmentation ne sont pas pris en charge pour la lecture MP4.

* **Lecture de la copie avec débit adaptatif (ABR) -** Cette fonctionnalité permet à TVSDK de basculer entre les diffusions iFrame en mode de lecture de l’astuce. Vous pouvez utiliser des profils non iFrame pour effectuer des opérations de lecture à des vitesses inférieures.

* **Lissage de la pièce -** Ces améliorations améliorent l’expérience utilisateur :

   * Sélection de débit et de débit d’image adaptatifs lors de la lecture de la astuce, en fonction de la bande passante et du profil de mémoire tampon

   * Utilisation de la diffusion principale au lieu de la diffusion IDR pour une lecture rapide jusqu’à 30 ips.

* **Protection du contenu**

   * **Protection des sorties basée sur la résolution -** Cette fonctionnalité associe les restrictions de lecture à des résolutions spécifiques, fournissant des contrôles DRM plus précis.

* **Prise en charge des workflows**

   * **Intégration de la facturation directe -** Cela envoie les mesures de facturation au serveur principal Adobe Analytics, qui est certifié par Adobe Primetime pour les diffusions utilisées par le client.

  TVSDK collecte automatiquement les mesures, en conformité avec le contrat de vente client, afin de générer des rapports d’utilisation périodiques requis à des fins de facturation. Pour chaque événement de démarrage de flux, TVSDK utilise l’API d’insertion de données d’Adobe Analytics pour envoyer des mesures de facturation telles que le type de contenu, les indicateurs activés pour l’insertion de publicités et les indicateurs activés pour la collecte de données drm (selon la durée du flux facturable) à la suite de rapports détenue par Adobe Analytics Primetime. Cela n’interfère ni n’est inclus dans les suites de rapports Adobe Analytics ou dans les appels au serveur du client. Sur demande, ce rapport sur l’utilisation de la facturation est envoyé régulièrement aux clients. Il s’agit de la première phase de la fonctionnalité de facturation prenant uniquement en charge la facturation de l’utilisation. Il peut être configuré en fonction du contrat de vente à l’aide des API décrites dans la documentation. Cette fonction est activée par défaut. Pour désactiver cette fonction, reportez-vous à l’exemple du lecteur de référence.

   * **Amélioration de la prise en charge du basculement -** Des stratégies supplémentaires ont été mises en oeuvre pour poursuivre la lecture ininterrompue, en dépit des échecs des serveurs d’hôtes, des fichiers de liste de lecture et des segments.

* **Publicité**

   * **Intégration de Moat -** Prise en charge de la mesure de la visibilité publicitaire de la souris.

   * **Bannières d’accompagnement -** Les bannières d’accompagnement s’affichent à côté d’une publicité linéaire et continuent souvent d’être affichées sur l’affichage après la fin de la publicité. Ces bannières peuvent être de type html (fragment de code de HTML) ou iframe (URL vers une page iframe).

* **Analytics**

   * **VHL 2.0 -** Il s’agit de la dernière intégration optimisée de la bibliothèque Video Heartbeats (VHL) pour la collecte automatique des données d’utilisation d’Adobe Analytics. La complexité des API a été réduite pour faciliter l’implémentation. Téléchargement de la bibliothèque VHL [v2.0.0 pour Android](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) et extrayez le fichier JAR dans le dossier libs .

* **SizeAvaliableEventListener**

   * `getHeight()` et `getWidth()` méthodes de `SizeAvailableEvent` renverra désormais respectivement la hauteur et la largeur. Le format d’affichage peut être calculé comme suit :

     ```java
     SizeAvailableEvent e;
     DAR = e.getWidth()/ e.getHeight();
     ```

     Le rapport d’aspect du stockage en termes de largeur de l’image et de hauteur de l’image peut également être utilisé pour calculer la largeur de l’image et la hauteur de l’image :

     ```java
     SAR = e.getSarWidth()/e.getSarHeight();
     frameHeight = e.getHeight();
     frameWidth = e.getWidth()/SAR;
     ```

* **Cookies**

   * Android TVSDK prend désormais en charge l’accès aux cookies JAVA stockés dans CookieStore de l’application Android. Une API de rappel (onCookiesUpdated) est fournie pour être enregistrée chaque fois qu’un nouveau cookie fait partie de la variable **Set-Cookie** En-tête de réponse. Ces cookies sont disponibles sous la forme d’une liste de cookies HttpCookie utilisés pour un URI/domaine différent en définissant ces valeurs de cookies sur cet URI/domaine particulier à l’aide de CookieStore. De même, les valeurs des cookies dans TVSDK sont mises à jour à l’aide de l’API d’ajout de CookieStore.

## Matrice de fonctionnalités {#feature-matrix}

TVSDK pour Android prend en charge plusieurs fonctionnalités que vous pouvez mettre en oeuvre pour ajouter des fonctionnalités à vos applications vidéo.

Dans les tableaux de fonctionnalités ci-dessous, un &quot;Y&quot; indique que la fonctionnalité est prise en charge dans la version actuelle.

| Fonctionnalité | Type de contenu | HLS |
|---|---|---|
| Lecture générale (Lecture, Pause, Recherche) | VOD + En direct | Y |
| FER - Lecture générale (Lecture, Pause, Recherche) | FER VOD | Y |
| Rechercher quand une publicité est en cours de lecture | VOD + En direct | Non pris en charge |
| Lecture HEVC | VOD + En direct | Conteneur fMP4 uniquement |
| AC3 et EAC3 | VOD + En direct | Non pris en charge |
| MP3 | VOD | Non pris en charge |
| Lecture de contenu MP4 | VOD | Y |
| Logique de changement de débit adaptatif | VOD + En direct | Y |
| Lecture audio uniquement | VOD + En direct | Y |
| Prise en charge multi-CDN | VOD + En direct | Non pris en charge |
| Lecture des publicités avec un média audio uniquement | VOD + En direct | Non pris en charge |
| Sous-titres codés - 608/708 | VOD + En direct | Y |
| Sous-titres codés - WebVTT | VOD + En direct | Y |
| Basculement du manifeste | VOD + En direct | Y |
| Basculement avancé | VOD + En direct | Y |
| Notifications QoS et du lecteur | VOD + En direct | Y |
| Prise en charge des en-têtes de cookie | VOD + En direct | Y |
| Prise en charge des en-têtes HTTP personnalisés | VOD + En direct | Y (liste autorisée requise) |
| Définition des paramètres de contrôle de la mémoire tampon | VOD + En direct | Y |
| Définition des contrôles de débit adaptatif | VOD + En direct | Y |
| Balises de manifeste personnalisées | VOD + En direct | Y |
| Liaison audio tardive | VOD + En direct | Y |
| Redirection 302 | VOD + En direct | Y |
| Lecture avec décalage | VOD + En direct | Y |
| Lecture de la carte | VOD + En direct | Y |
| Mouvement lent dans la lecture de la vidéo | VOD + En direct | Non pris en charge |
| Lecture de la case à cocher lissée (avec ABR) | VOD + En direct | Y |
| Analyse d’ID3 | VOD + En direct | Y |
| Blackout des publicités | VOD + En direct | Non pris en charge |
| Instant activé | VOD + En direct | Non pris en charge |
| Prise en charge des marqueurs de discontinuité | VOD + En direct | Y |
| 302 Redirect Stickiness | VOD + En direct | Y |

| Fonctionnalité | Type de contenu | HLS |
|---|---|---|
| Lecture générale, publicités activées | VOD + En direct | Y |
| Contenu FER avec publicités activées | VOD | Y |
| Comportements de publicité par défaut | VOD + En direct | Y |
| VAST 2.0/3.0 | VOD + En direct | Y |
| VMAP 1.0 | VOD + En direct | Y |
| Publicités MP4 | VOD + En direct | Y (provenant de CRS) |
| Lecture de la carte avec publicités activées | VOD + En direct | Y |
| Publicité uniquement | VOD | Y |
| Paramètres de ciblage | VOD + En direct | Y |
| Paramètres personnalisés | VOD + En direct | Y |
| Comportements publicitaires personnalisés | VOD + En direct | Y |
| Balises publicitaires personnalisées | En direct | Y |
| Résolveurs de publicités personnalisés | VOD + En direct | Y |
| Résolveur de publicité personnalisée à roue libre | VOD | Y |
| C3 | VOD + En direct | Non pris en charge |
| Résolution des publicités différées | VOD | Y |
| Prise en charge des marqueurs de discontinuité - SSAI | VOD + En direct | Y |
| Publicités d’accompagnement, bannières publicitaires et publicités cliquables | VOD + En direct | Y |
| VPAID 2.0 | VOD + En direct | Y (JS) |
| Sortie anticipée de publicité | En direct | Y |
| Hiérarchisation des créatifs basée sur des règles | VOD + En direct | Y |
| Règles CRS | VOD + En direct | Y |
| JSON Ad Resolver | VOD + En direct | Non pris en charge |
| Intégration de la souris | VOD + En direct | Y |
| Insertion de coupure publicitaire partielle | En direct | Y |

| Fonctionnalité | Type de contenu | HLS |
|---|---|---|
| Chiffrement AES | VOD + En direct | Y |
| Exemple de chiffrement AES | VOD + En direct | Y |
| Flux Tokenized | VOD + En direct | Y |
| Widevine DRM | VOD + En direct | Conteneur fMP4 uniquement |
| DRM Primetime | VOD + En direct | Y |
| Lecture externe (RBOP) | VOD + En direct | Primetime DRM uniquement |
| Rotation de licence | VOD + En direct | Primetime DRM uniquement |
| Rotation des clés | VOD + En direct | Primetime DRM uniquement |

| Fonctionnalité | Type de contenu | HLS |
|---|---|---|
| Intégration d’Adobe Analytics VHL | VOD + En direct | Y |
| Facturation | VOD + En direct | Y |

## Problèmes résolus {#resolved-issues}

Lorsque la résolution est associée à un problème signalé, une référence Zendesk s’affiche, par exemple ZD#xxxxx.

**Android TVSDK 3.15**

Cette section présente un résumé du problème résolu dans la version TVSDK 3.14 Android.

* ZD#46903 - L’application se bloque plusieurs fois lorsque la balise créative est manquante ou lorsque [!UICONTROL url CDATA] est vide dans [!UICONTROL VAST] réponse.

**Android TVSDK 3.14**

* ZD#46903 - L’application se bloque lorsque [!UICONTROL CDATA] est vide pour l’un des [!UICONTROL ClickTracking], [!UICONTROL CustomClick] ou [!UICONTROL CompanionClickTracking] élément dans [!UICONTROL VAST] réponse.

### Problèmes résolus dans les versions précédentes

**Android TVSDK 3.12**

* ZD#40584 - L’application de référence Primetime ne se crée pas avec la dernière version de gradle.

**Android TVSDK 3.11**

* ZD#41252 - Caractères coréens dans WebVTT rompus après Android 7.1.

**Android TVSDK 3.10**

* ZD#40340 - L’application se bloque avec l’erreur &quot;L’application ne répond pas&quot; lors de la tentative de lecture après la liste bloquée de tous les fichiers TS (TypeScript).

**Android TVSDK 3.8**

* Aucun nouveau problème n’a été ajouté.

**Android TVSDK 3.7**

* Aucun nouveau problème n’a été ajouté.

**Android TVSDK 3.6**

* Aucun nouveau problème n’a été ajouté.

**Version 3.5**

* ZD#37503 - Les réponses JSON des règles CRS sont mises en cache afin d’éviter la duplication des requêtes.

**Version 3.4**

* ZD#37996 - Correction d’un problème de lecture par accrochages pour les flux CMAF linéaire et VOD.
* ZD#37706 - Correction d’un problème de sous-titres altérés.
* ZD#37622 - Correction d’un problème lié aux erreurs URISyntaxErrors irrécupérables pour des publicités spécifiques.
* ZD#36938 - Correction d’un problème en raison duquel le débit de transmission était transmis au débit moyen, puis atteignait le débit le plus élevé après avoir quitté les lectures de la figure.

**Version 3.3**

* ZD#37394 - L’avance rapide de la ressource CMAF provoque des artefacts après les changements de vitesse.
   * Correction d’un problème qui se produisait lors d’un changement de profil lors de la lecture de l’astuce.
* ZD#37396 - Les événements de suivi des publicités sont manquants pour certains mid-rolls et post-rolls.
   * Correction d’un cas spécifique relatif aux événements de suivi des publicités.
* ZD#37491 - Le code d’état HTTP avec méta d’erreur n’est pas présent.
   * Travail sur la propagation des erreurs réseau plus haut dans la pile.
* ZD#37808 - Liste autorisée d’un nouvel en-tête personnalisé.
   * Ajout de la prise en charge de SSAI_TAG dans le cadre de ce correctif.
* ZD#37622 - Erreurs de syntaxe URIS à partir de capsules publicitaires spécifiques.
   * Correction d’un problème de blocage de la lecture en continu lorsque des publicités diffusées avec l’application Android du client contenaient un % non codé.
* ZD#37631 - Mécanisme de reprise du manifeste Principal pour Android TVSDK.
   * Ajout d’une nouvelle API dans la configuration réseau pour gérer cette amélioration. Si cette API n’est pas utilisée, la tentative de manifeste n’est pas effectuée à nouveau. S’il est utilisé, le manifeste sera de nouveau tenté pour gérer les erreurs réseau et les dépassements de délai.

**Version 3.2**

* ZD#37493 - Les balises de suivi pour la lecture en direct ne sont pas déclenchées par intermittence pour la première publicité dans la séquence.
* ZD#36985 - Les balises de suivi ne sont pas envoyées pour les coupures publicitaires vides dans la réponse VMAP.
* ZD#37134 - TVSDK renvoie par intermittence un ID incorrect pour la réponse VMAP.

**Version 3.0**

* ZD#33740 - TVSDK renvoie un avertissement inutile juste après la création d’un objet MediaPlayer et l’appel de replaceCurrentResource()

   * Amélioration de la correction précédente en appelant Restaurer uniquement lorsque le lecteur est en état suspendu

* ZD#36442 - Chaque nouvelle lecture déconnecte la session de débogage à distance, ce qui rend impossible le débogage.

   * Le débogage n’est pas possible par défaut sur l’affichage web, car le débogage n’est pas activé par défaut. L’application doit activer le débogage si nécessaire en appelant setWebContentsDebuggingEnabled(true) sur l’objet renvoyé par MediaPlayer.getCustomAdView().

* ZD#33688 - Prise en charge de l’heure juste et résolution

   * Les coupures publicitaires sont résolues à un intervalle spécifié avant la position de la coupure publicitaire.

* ZD#36441 - La durée de la fenêtre active continue d’augmenter au-delà de 5 minutes, ce qui entraîne plusieurs problèmes.

   * Correction d’un problème en raison duquel virtualStartTime était ajouté deux fois lors du calcul du point d’activation virtuel, ce qui entraînait ce problème.

**Android TVSDK 2.5.6**

* ZD #34992 - La langue est vide dans le libellé codé.

   * Correction d’un cas où TVSDK n’analysait pas #EXT-X-MEDIA:TYPE=CLOSED-CAPTIONS du manifeste principal pour obtenir les détails du suivi de la légende.

* ZD #35078 - Validation de P Android.

   * TVSDK 2.5.6 a été validé avec les derniers builds Android bêta. Aucun problème n’a été détecté en raison du nouveau système d’exploitation Android.

* ZD #34149 - Le lecteur continue à demander des manifestes même si une erreur se produit.

   * Correction du cas où TVSDK effectuait des appels répétitifs même lorsque tous les profils étaient en panne (erreur 404).

* ZD #31533 - Lecture audio sur Android une fois l’application envoyée en arrière-plan.

   * Ajout `enableAudioPlaybackInBackground` API de MediaPlayer qui doit être appelée avec &quot;True&quot; en tant qu’argument (lorsque le lecteur est à l’état PRÉPARÉ) pour activer la lecture du contenu audio lorsque l’application est en arrière-plan.

**Android TVSDK 2.5.5**

* ZD #21647 - Android TVSDK avertit 640x368 lorsque la taille réelle de la vidéo est de 640x360.

   * En raison de la variable m_nOutputHeight (dans AndroidMCVideoDecoder) mise à jour avec la hauteur d’image au lieu de la hauteur de sortie réelle. Apport de modifications appropriées dans la fonction getVideoFrame pour calculer correctement m_nOutputHeight.

* ZD #26614 - Urgent — Service publicitaire tiers / programmatique — échec de diffusion des impressions.

   * Amélioration de la correction précédente en gérant le cas dans l’analyse XML où le problème était reproductible lorsque &quot;espace&quot; est avant le signe &quot;égal&quot; comme &lt;vast version=&quot;2.0&quot;>

* ZD #29296 - Android : ajoutez AdSystem et Creative ID aux demandes CRS.

   * Incluez désormais &quot;AdSystem&quot; et &quot;CreativeId&quot; comme nouveaux paramètres dans les requêtes 1401 et 1403.

* ZD #33062 - TVSDK se bloque sur l’occurrence de barre verticale dans la réponse VAST sous le noeud CDATA

   * API setEncodeUrlForTracking dans la classe NetworkConfiguration supprimée en tant que caractères non sûrs dans une URL à coder

* ZD #33063 - La logique de sélection des fichiers CRS a été rompue - TVSDK n’envoyait pas de demande CRS pour le format webm, mais plutôt pour les fichiers 3gpp.

   * Correction de la logique maintenant. Lors de l’utilisation de fichiers multimédias au format webm et 3gpp, une demande CRS doit être envoyée pour le web. En outre, lorsque vous utilisez les deux fichiers multimédias au format 3gpp, la demande CRS doit être envoyée pour le fichier 3gpp à débit le plus élevé.

* ZD #33125 - L’application Android se bloque avec une balise DoubleClick spécifique dans le VMAP.

   * Correction du scénario pour éviter le blocage.

* ZD #32256 - License Rotation &amp; Key Rotation Problème - Adobe Access

   * Correction de l’initialisation des segments avec les métadonnées DRM pour le contenu SampleAES. Fonctionne correctement avec le contenu AES128.

* ZD #33619 - Transfert rapide d’un contenu de liste de lecture en augmentation bloqué à l’état de mise en mémoire tampon près d’un point de vie.

   * Traitement du cas lors du passage du point de vie en mode de lecture par astuces

* ZD #34151 - Objets TimedMetadata dans l’ordre.

   * Deux événements TimedMetadata s’affichaient dans un ordre aléatoire s’ils se trouvaient au même moment dans la chronologie. Maintien de leur ordre d’origine dans le manifeste.

* ZD #34189 - Problème lors de la recherche d’un début de coupure publicitaire.

   * Le problème était avec les publicités SSAI assemblées à l&#39;aide de discontinuité. Et la cause était un comportement quand nous cherchons au début de telles publicités, nous recherchons une image clé et nous ne la trouvons pas. La raison en était que l’horodatage audio principal de la publicité était avant l’horodatage vidéo principal. Par conséquent, nous finissons par rechercher une image clé à une mauvaise donnée fragmentDump. Corrigé maintenant.

* ZD #34528 - Résolution de la vidéo ne dépassant pas 640x360 sur le dongle 3e génération de FireTV.

   * Amélioration du correctif pour inclure les dernières mises à jour du micrologiciel

* ZD #34793 - TVSDK 2.5.x se bloquait avec le programme de résolution de contenu personnalisé dans certains cas lorsque VideoEngine supposait que les paramètres de Auditude étaient disponibles et qu’ils ne l’étaient pas.

   * Le blocage se produisait en raison d’un appel de fonction sur un pointeur partagé Null (auditudeSettings). Ajout d’une vérification conditionnelle dans VideoEngineTimeline::placeToSourceTimeline() pour s’assurer que auditudeSettings est disponible avant d’appeler quoi que ce soit sur cet objet.

* ZD #32584 - Impossible d’accéder aux informations complètes présentes dans le &lt;extensions> noeud d’une réponse VAST.

   * Correction d’un problème lié à l’analyse XML. Désormais, NetworkAdInfo fournit les informations complètes présentes dans la variable &lt;extensions> node

* ZD #35086 - Inrécupération des données d’extension complètes du lecteur en cas de réponses VMAP spécifiques.

   * Le problème était spécifique au xml d’extension car l’analyse XML ne fonctionnait pas si le xml d’extension contenait des guillemets doubles dans la valeur d’attribut. Correction du problème.

**Android TVSDK 2.5.4**

* ZenDesk#33659 - Session de lecture permettant le débogage à distance de l’affichage Web.

WebViewDebbuging est défini sur False par défaut. Pour activer le débogage, définissez sur true via l’application, à l’aide de setWebContentsDebuggingEnabled(true).

* ZenDesk#33011 - La chronologie de la publicité n’est pas résolue en cas d’échec de la requête CRS.

  Lorsqu’une requête CRS envoyée à une publicité échoue, la chronologie est résolue et les publicités restantes sont lues.

* ZenDesk#34528 - La résolution vidéo n’est pas mise à niveau au-delà de 640x360 sur le dongle de troisième génération de FireTV.

  La résolution vidéo bascule en tant que débit binaire.

* ZenDesk#33192 - AudioTrack possède un nom null lorsque track est récupéré via AudioUpdatedEventListener::onAudioUpdated.

  Dans certains scénarios sur une étiquette FireTV, l’événement onAudioUpdate était déclenché lorsqu’il n’y avait aucune mise à jour audio réelle. Ce problème a été corrigé maintenant.

**Android TVSDK 2.5.3**

* Zendesk#32216 - L’abonnement à la balise personnalisée TimedMetadata ne fonctionne pas.

  Nous renvoyons les données ID3 sous la forme d’un tableau d’octets (pour prendre en charge les données APIC ou génériques) au client, alors que dans la version 1.4, nous renvoyons une chaîne. Le tableau d’octets ne gère pas le caractère terminé nul lui-même. Par conséquent, il présentait un caractère spécial au client. Ce problème est maintenant résolu.
* Zendesk#32670 - Le lecteur ne tombe pas sur la liste de lecture redondante

  Cela fonctionne correctement maintenant et setNetworkDownVerificationUrl fonctionne comme prévu.
* Zendesk#32369 - La légende fermée affiche différentes couleurs d’ordures ou d’artefact.

  Correction d’un problème lié aux problèmes CC dans le dernier build.
* Zendesk#25590 - Amélioration : magasin de cookies TVSDK ( C++ vers JAVA )

  Android TVSDK prend désormais en charge l’accès aux cookies entre la couche JAVA (stockée dans CookieStore de l’application Android) et la couche C++ TVSDK.
* Zendesk#32252 - TVSDK_Android_2.5.2.12 ne semble pas avoir le correctif pour PTPLAY-20269

  Ce problème a été corrigé et intégré à la branche 2.5.2.
* Zendesk#31806 - Baguettes Auditude lors de la PRÉPARATION

  Le lecteur était bloqué dans l’état Préparation car le fichier xml de réponse avait une balise vide. Maintenant, le problème est résolu.
* Zendesk#31727 - Les caractères de sous-titres non intégrés TVSDK 2.5 sont ignorés ou mal orthographiés.

  Le problème est résolu et nous ne perdons aucun caractère pour l’orthographe.
* Zendesk#31485 - DrmManager dans 2.5

  Un problème s’est produit lors de la création de DrmManager via un nouveau DrmManager (contexte contextuel). Mise en oeuvre de la classe DRMService qui fournissait DRMManager.
* Flux de résolution Zendesk#32794-1080P non lu sur Android

  Nous avons modifié les méthodes SizeAvailableEvent et auparavant, getHeight() et getWidth() de SizeAvailableEvent dans la version 2.5 utilisées pour renvoyer la hauteur et la largeur d’image, qui étaient renvoyées par le format multimédia. Elle renvoie désormais la hauteur de sortie et la largeur de sortie respectivement renvoyées par le décodeur.
* Le Flash Player Zendesk #19359 se bloque en raison de la position de l’attribut #EXT-X-FAXS-CM dans le manifeste de niveau défini.

  La balise #EXT-X-FAXS-CM doit toujours apparaître sur la liste de lecture supérieure avant que chaque débit ou segment n’apparaisse dans la liste de lecture.

**Android TVSDK 2.5.2**

* Zendesk#17305 Artefacts dans des sous-titres non opaques en arrière-plan.

  La propriété setTextSpaceAsAlphaNum dans TextFormat est exposée. Par défaut, la propriété est False. Définissez la propriété sur True dans un client pour résoudre le problème d’espace sombre.

* L&#39;affichage Zendesk#25097 CC contient des artefacts visuels avec les paramètres CC.

  La propriété setTextSpaceAsAlphaNum dans TextFormat est exposée. Par défaut, la propriété est False. Définissez la propriété sur True dans un client pour résoudre le problème d’espace sombre.

* Zendesk #31620 La chaîne de l’agent utilisateur sortant du lecteur TVSDK est tronquée.

  La chaîne de l’agent utilisateur ne sera plus tronquée après 128 caractères.

  La chaîne de version Adobe Primetime est ajoutée à l’agent utilisateur système.

* Zendesk #30809 L’événement SEEK_END manquant empêche l’application de passer à un état de lecture.
* La couleur &quot;cyan&quot; du sous-titrage codé Zendesk #30415 est désormais une nuance plus sombre de bleu (turquoise), par rapport aux versions précédentes de TVSDK Primetime.

  La couleur est changée de DarkCyan en Cyan.

* Zendesk #30727 Les publicités VOD ne sont pas téléchargées/résolues.

  Dans VMAP XML s’il existe une balise VAST vide sans balise de fermeture explicite (&lt;/vast>&quot;) et sans caractère de saut de ligne après, le code XML VMAP n’est pas correctement analysé et les publicités peuvent ne pas être lues.

**Android TVSDK 2.5.1**

* Blocage spécifique à l’appareil (Samsung Galaxy Tab 4) ; VOD DRM LBA avec Auditude et clic sur les publicités.
* VHL - Des appels de pulsation incorrects sont envoyés lors du démarrage du contenu à partir d’un décalage.
* Lors de la lecture des publicités VPAID, les appels de pulsation VHL pour l’événement:type:la publicité de lecture est manquante.
* Après être passé à l’état COMPLETE, le lecteur revient à l’état LECTURE avec SKIP adBreakPolicy pour les publicités preroll.
* Les cookies ne sont pas associés aux rappels publicitaires sortants.
* Les repères de publicités ne sont pas visibles.
* HLS avec une piste SAP EAC3 distincte ne se charge pas.
* Le lecteur se bloque lorsque TVSDK reçoit l’intention d’écran activé une fois le lecteur multimédia restauré.

## Problèmes connus et limites {#known-issues-and-limitations}

**Android TVSDK 3.11**

* Aucune nouvelle limitation n’a été ajoutée.

### Problèmes connus et limites des versions précédentes

**Android TVSDK 3.10**

* Aucune nouvelle limitation n’a été ajoutée.

**Android TVSDK 3.8**

* Aucune nouvelle limitation n’a été ajoutée.

**Android TVSDK 3.7**

* Aucune nouvelle limitation n’a été ajoutée.

**Android TVSDK 3.6**

* Aucune nouvelle limitation n’a été ajoutée.

**Android TVSDK 3.5**

* Aucune nouvelle limitation n’a été ajoutée.

**Android TVSDK 3.4**

* ID3, Sous-titres codés, prise en charge de l’audio de liaison tardive n’a pas été vérifiée pour le flux CMAF (CBC).
* Sur certains appareils, il existe un problème de faible reproductibilité en raison duquel la distorsion vidéo peut apparaître en haut lors de la lecture de l’astuce sur les flux CMAF.

**Android TVSDK 3.3**

* les sous-titres clcp:c608 ne sont pas pris en charge pour la lecture de flux CMAF.

**Android TVSDK 3.2**

* TVSDK 3.2 ne prend pas en charge la lecture d’exemples de flux AES et AES128 CMAF.
* Les flux CMAF HEVC n’incluent pas la prise en charge de la lecture des sous-titres fermés.
* La coloration verte s’affiche pour les flux chiffrés en mode WV lorsque la recherche est effectuée autour du segment non chiffré.
* Les flux CMAF ne prennent pas en charge les événements ID3.
* Les flux HLS ne prennent pas en charge le format de sous-titres HTML.

**Android TVSDK 3.0**

* La prise en charge de HEVC présente les limites suivantes dans cette version

   * DRM non pris en charge
   * Prise en charge du CC (CEA 608/708) non vérifiée
   * La prise en charge de 4K n’est pas encore présente
   * Prise en charge des balises ID3 non vérifiée

* Pour les événements de progression de la publicité, la barre de chronologie peut ne pas refléter une durée de lecture de publicité entièrement précise. Pour pallier ce problème, vous pouvez utiliser `adcompleteevent` pour connaître la fin de la lecture de la publicité et mettre à jour l’interface utilisateur à diverses fins, comme mettre à jour la barre de chronologie, supprimer l’interface utilisateur associée à la publicité, etc.
* Les appels de publicités volumineux renvoyés par VMAP ne respectent pas la position de recherche en amont juste à temps.

**Android TVSDK 2.5.6**

* Plusieurs coupures publicitaires VMAP en même temps ne sont pas prises en charge.

**Android TVSDK 2.5.3**

Cette version présente les problèmes suivants :

* La lecture vidéo en direct peut présenter des problèmes de synchronisation audio-vidéo sur les appareils bas de gamme ou des conditions réseau médiocres.
* Pour les flux FER, virtualTime et localTime peuvent différer. En outre, FER avec décalage ne fonctionne pas.
* La lecture peut être bloquée lorsque la recherche porte sur les contenus audio de liaison tardive.
* Par intermittence, les sous-titres webVTT peuvent devenir désynchronisés pour le contenu LIVE.
* Par intermittence, la lecture rapide de quelques images peut être vue après la sortie d’une coupure publicitaire.
* Parfois, une erreur 303 est générée pour les coupures publicitaires Tripple Wrapper, même si des publicités sont lues.

**Android TVSDK 2.5.2**

Cette version présente les problèmes suivants :

* La lecture vidéo en direct peut présenter des problèmes de synchronisation audio-vidéo sur les appareils bas de gamme.
* La lecture peut parfois être bloquée lors de la recherche vers la fin du média VOD.
* Pour les flux FER, virtualTime et localTime peuvent différer. En outre, FER avec décalage ne fonctionne pas.

**Android TVSDK 2.5.1**

Cette version de TVSDK présente les problèmes suivants :

* La lecture vidéo en direct peut présenter des problèmes de synchronisation audio-vidéo sur les appareils bas de gamme.
* Pour les flux FER, virtualTime et localTime peuvent différer. En outre, FER avec décalage ne fonctionne pas.
* Dans VMAP XML, s’il existe une balise VAST vide sans balise de fermeture explicite (&lt;/vast>), et sans nouvelle ligne après, le code XML VMAP n’est pas analysé correctement et les publicités peuvent ne pas être lues.
* Les opérations post-roll VPAID ne sont pas prises en charge.

## Ressources utiles {#helpful-resources}

* [Configuration requise](/help/programming/tvsdk-3x-android-prog/android-3x-introduction/android-3x-requirements.md)
* [Guide du programmeur Android TVSDK 3.10](/help/programming/tvsdk-3x-android-prog/android-3x-introduction/overview-prod-audience-guide/android-3x-overview-prod-audience-guide.md)
* [Javadoc Android TVSDK pour référence API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html)
* [Document API TVSDK Android C++](https://help.adobe.com/en_US/primetime/api/psdk/cpp_3.5/namespaces.html) - Chaque classe Java possède une classe C++ correspondante et la documentation C++ contient plus de documents explicatifs que les Javadocs. Reportez-vous donc à la documentation C++ pour une compréhension plus approfondie de l’API Java.
* [Guide de migration de TVSDK 1.4 vers 2.5 pour Android (Java)](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-25-android.html)
* Pour gérer les scénarios d’activation/de désactivation d’écran, voir `Application_Changes_for_Screen_On_Off.pdf` inclus dans la version.
* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://helpx.adobe.com/support/primetime.html) page.
