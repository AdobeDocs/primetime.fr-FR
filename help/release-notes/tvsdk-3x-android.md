---
title: Notes de mise à jour de TVSDK 3.11 pour Android
seo-title: Notes de mise à jour de TVSDK 3.11 pour Android
description: Les Notes de mise à jour de TVSDK 3.11 pour Android décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus et les problèmes de périphérique dans TVSDK Android 3.10
seo-description: Les Notes de mise à jour de TVSDK 3.11 pour Android décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus et les problèmes de périphérique dans TVSDK Android 3.11
uuid: 685d46f5-5a02-4741-af5c-91e91babd6f7
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: 3a27379f-3cef-4ea3-bcae-21382dc1e9fd
translation-type: tm+mt
source-git-commit: 33abc0364a7dbe123ef1e6e444ad8578b5596f63

---


# Notes de mise à jour de TVSDK 3.11 pour Android {#tvsdk-for-android-release-notes}

Les Notes de mise à jour de TVSDK 3.11 pour Android décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus et les problèmes de périphérique dans TVSDK Android 3.11.

Le lecteur de référence Android est inclus avec le SDK TVSDK Android dans le répertoire samples/ de votre distribution. Le fichier README.md qui l’accompagne explique comment créer le lecteur de référence.

>[!NOTE]
>
>Pour créer le lecteur de référence, comme décrit dans le fichier README.md distribué avec la version, veillez à effectuer les opérations suivantes :
>
>1. Téléchargez VideoHeartbeat.jar depuis [https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) (bibliothèque VideoHeartbeat pour Android v2.0.0).
>1. Extrayez VideoHeartbeat.jar dans le dossier libs/.
>



TVSDK pour Android offre de nombreuses améliorations de performances par rapport aux versions précédentes. Il offre une expérience d’affichage de haute qualité et intègre toutes les fonctionnalités de la version 1.4, à l’exception de la prise en charge de multi-CDN.

L’ensemble complet des fonctionnalités prises en charge et non prises en charge est présenté dans la section Matrice [des](#feature-matrix) fonctionnalités des notes de mise à jour.

<!-- ## New features {#new-features} -->

## Android TVSDK 3.11

**Extraire la zone PSSH (en-tête spécifique au système de protection) autorisée**

TVSDK permet désormais de récupérer la zone d’en-tête spécifique au système de protection associée à la ressource média chargée en cours. Une nouvelle API `getPSSH()` a été ajoutée à `com.adobe.mediacore.drm.DRMManager`.
Pour plus d’informations, voir [Widevine DRM](../programming/tvsdk-3x-android-prog/android-3x-content-security/android-3x-drm-widevine.md).

Les principaux problèmes des clients résolus dans la version actuelle sont mentionnés dans la section Problèmes [](#resolved-issues) résolus.

### Nouvelles fonctionnalités et améliorations des versions précédentes

**Android TVSDK 3.10**

Cette version s’est concentrée sur la résolution des principaux problèmes des clients, comme indiqué dans la section Problèmes [](#resolved-issues) résolus.

**Android TVSDK 3.9**

* **sécurisé via HTTPS** - Android TVSDK 3.9 introduit les fonctionnalités de sécurisé via HTTPS afin de diffuser du contenu en toute sécurité avec une échelle et des performances inégalées.

   Pour activer les  sécurisées via HTTPS, une nouvelle API est introduite dans `NetworkConfiguration` la classe.

   `public void setForceHTTPS (boolean value)`

   `public boolean getIsForceHTTPS()`

**Android TVSDK 3.8**

* **Prise en charge de la pré-lecture avec la fonction** Ad-Break partielle - Grâce à cette amélioration, TVSDK 3.8 prend en charge les publicités preroll avec la fonction Ad-Break partiel (PABI).

   La publicité preroll, si elle est disponible, est lue, puis le contenu est lu à partir du point de diffusion qui imite l’expérience de la télévision en direct.

**Android TVSDK 3.7**

* Pour le contenu du test Widevine, une nouvelle API `setMediaDrmCallback` dans la classe DRMManager est exposée pour remplacer l’implémentation par défaut de l’interface MediaDrmCallback.

   `public static void setMediaDrmCallback(MediaDrmCallback callback)`

* Correction d’une erreur AppCrash en raison de la non-gestion `MediaPlayerEvent.ITEM_UPDATED` du calque C++ (Android 64 bits).

**Android TVSDK 3.6**

* **Améliorez vos applications en fonction de la configuration requise** 64 bits : la bibliothèque native `(libAVEAndroid.so)` est désormais mise à niveau et mise à disposition dans deux versions. L’emplacement de la bibliothèque native armeabi (32 bits) existante a été modifié et une bibliothèque arm64-v8a (64 bits) supplémentaire a été introduite dans `/framework/Player to /framework/Player/armeabi``/framework/Player/arm64-v8a.`

**Version 3.5**

* **Résolution** des publicités juste à temps - TVSDK 3.5 supprime la prise en charge des publicités lues de la chronologie.
* **Prise en charge de la lecture** hors ligne activée : avec la lecture hors ligne, les utilisateurs peuvent désormais télécharger du contenu vidéo sur leurs appareils et le regarder lorsqu’ils ne sont pas connectés. Pour plus d’informations, reportez-vous à la section &quot;Lecture[hors ligne avec Android](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_3.5.pdf)&quot;.

**Version 3.4**

* TVSDK prend maintenant en charge la lecture des flux CMAF pour les flux cryptés et ordinaires de CBC.

**Version 3.3**

* **Modifications de l’API**

   * Une nouvelle API est ajoutée pour `NetworkConfiguration::setNumOfTimesManifestRetryBeforeError(n)*` gérer les erreurs réseau et les dépassements de délai.
      * où n) est le nombre de  de l&#39;.

**Version 3.2**

* **Prise en charge de la résolution des publicités parallèles et du téléchargement du manifeste**

   * TVSDK 3.2 prend en charge la résolution simultanée, au lieu de la résolution séquentielle pour toutes les demandes d’annonce et les coupures publicitaires, à l’exception de VMAP.
   * Tous les manifestes publicitaires d’une coupure publicitaire sont téléchargés simultanément.
* **Prise en charge de la résolution des publicités et du délai d’expiration du téléchargement du manifeste activée.**

   * Les utilisateurs peuvent désormais définir la valeur du délai d’expiration pour la résolution globale de la publicité et les téléchargements de manifeste.  Dans le cas du VMAP, la valeur du délai d’expiration s’applique aux coupures publicitaires individuelles, car toutes les coupures publicitaires sont résolues de manière séquentielle.
* **Ajout de nouvelles API dans la classe AdvertisingMetadata :**

   * void setAdResolutionTimeout(int adResolutionTimeout)
   * int getAdResolutionTimeout()
   * void setAdManifestTimeout(int adManifestTimeout)
   * int getAdManifestTimeout()
* **Supprimé sous les API de la classe AdvertisingMetadata :**

   * void setAdRequestTimeout(int adRequestTimeout)
   * int getAdRequestTimeout()
* **Lecture des flux activée avec le codec audio AC3/EAC3**

   * void alwaysUseAC3OnSupportedDevices(boolean val)dans la classe MediaPlayer
* **TVSDK prend en charge la lecture CMAF et des flux ordinaires pour la Widevine CTR cryptée.**
* **La lecture des flux 4K HEVC est maintenant prise en charge.**
* **Demandes** d’appel d’annonce parallèles : TVSDK prérécupère désormais 20 demandes d’appel d’annonce en parallèle.

**Version 3.0**

* **TVSDK 3.0 prend en charge les flux de codage vidéo haute efficacité (HEVC).**

* **Juste à temps - Résolution des publicités plus proches des marqueurs publicitaires**

   La résolution des publicités différées résout désormais chaque coupure publicitaire indépendamment. Auparavant, la résolution des publicités était une approche en deux phases : les pré-rouleaux ont été résolus avant la  de lecture et tous les emplacements milieu/post-roll combinés après le démarrage de la lecture. Grâce à cette fonctionnalité améliorée, chaque coupure publicitaire est maintenant résolue à un moment spécifique avant le point de repère publicitaire.

   **Veuillez noter : La résolution des publicités différées a désormais été désactivée par défaut et doit être explicitement activée.**

   Une nouvelle API est ajoutée à *AdvertisingMetadata::setDelayAdLoadingTolérance* pour obtenir la tolérance de chargement différé de publicité associée à ces métadonnées publicitaires.\
   La recherche sera maintenant autorisée immédiatement après PRÉPARATION, la recherche de coupures publicitaires survenues résultera en une résolution immédiate avant la fin de la recherche.\
   Les modes de signature SERVER_MAP et MANIFEST_CUES sont pris en charge.

   Pour plus d’informations, reportez-vous au guide du programmeur Android TVSDK 3.0 sur les modifications d’API et de  de l’.

* **Mise à jour `targetSdkVersion` de la dernière version\
   **Mise à jour `targetSdkVersion` de 19 à 27 pour un fonctionnement sans heurts.

* **Placement.Type getPlacementType() est désormais une méthode sur l’interface TimelineMarker**

   Cette méthode renvoie un type de placement de Placement.Type.PRE_ROLL, Placement.Type.MID_ROLL ou Placement.Type.POST_ROLL. Si une coupure publicitaire n’est pas résolue, la méthode getDuration() de l’interface TimelineMarker renvoie 0.

**Version 2.5.6**

* **TVSDK 2.5 prend en charge Android P.**

* **Activation de l’audio en arrière-plan**

   Pour activer la lecture audio lorsque l’application passe du premier plan à l’arrière-plan, l’application doit appeler `enableAudioPlaybackInBackground` l’API de MediaPlayer avec la valeur true en tant qu’argument lorsque le lecteur est à l’état PRÉPARÉ.

* **alwaysUseAudioOutputLatency(valeur booléenne) dans la classe MediaPlayer**

Une fois définie, utilisez la latence de sortie dans le calcul de l’horodatage audio.
Valeur des paramètres booléens : True utilise la latence de sortie audio dans le calcul de l&#39;horodatage audio.

* **Optimisé pour obtenir la meilleure expérience de lecture, même si la vitesse de bande passante tombe soudainement en panne**

TVSDK annule désormais le téléchargement du segment en cours, si nécessaire, et bascule dynamiquement vers le rendu approprié. Pour ce faire, il suffit de basculer entre les débits sans interruption.

**Version 2.5.5**

* **Insertion partielle de sauts publicitaires**

   Expérience de type TV consistant à se joindre au milieu d’une publicité sans déclencher le suivi pour la publicité partiellement visionnée.\
   Exemple : L’utilisateur se joint au milieu (à 40 secondes) d’une coupure publicitaire de 90 secondes composée de trois publicités de 30 secondes. Il s&#39;agit de 10 secondes dans la seconde publicité pendant la coupure.

   * La seconde publicité est lue pour la durée restante (20 s), suivie de la troisième publicité.
   * Les suivis publicitaires pour la publicité partielle lue (seconde publicité) ne sont pas déclenchés. Les outils de suivi de la troisième publicité sont déclenchés.

* **Chargement sécurisé des publicités via HTTPS**

   Adobe Primetime permet de demander un premier appel au serveur d’annonces en temps de veille et au serveur CRS sur https.

* **AdSystem et ID créatif ajoutés aux demandes CRS**

   * Incluez désormais &quot;AdSystem&quot; et &quot;CreativeId&quot; comme nouveaux paramètres dans les requêtes 1401 et 1403.

* **L&#39;API setEncodeUrlForTracking de la classe NetworkConfiguration a été supprimée** car les caractères dangereux d&#39;une URL doivent être codés.

**Version 2.5.4**

Android TVSDK v2.5.4  les mises à jour et les modifications d’API suivantes  le :

* Modifications de la valeur par défaut pour WebViewDebbuging

   La valeur WebViewDebbuging est définie sur False par défaut. Pour l’activer, appelez setWebContentDebuggingEnabled(true) dans l’application.

* Mise à niveau des versions d’OpenSSL et de Curl

   Mise à jour de libcurl vers v7.57.0 et OpenSSL vers v1.0.2k.

* Accès au niveau de l’application pour l’objet de réponse VAST

   Présentation d’une nouvelle API NetworkAdInfo::getVastXml() qui permet d’accéder à l’objet de réponse VAST de l’application.

**Version 2.5.3**

 d’Android TVSDK v2.5.3  les mises à jour et modifications d’API suivantes.

* Tous les clients de TVSDK qui utilisent CRS sont invités à mettre à niveau leurs applications avec TVSDK 2.5.3.85 ou version ultérieure sur Android. Il s’agira d’un complément à la mise en oeuvre de l’application existante. Après la mise à niveau de TVSDK, recherchez les demandes d’URL de création CRS dans un outil de proxy (ex. : Charles) et confirmez que le nom d’hôte et la version dans le chemin d’accès se reflètent comme dans l’exemple de structure d’URL ci-dessous.

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* Agent utilisateur de TVSDK personnalisable : nous avons ajouté de nouvelles API pour personnaliser les agents utilisateur.

   * setCustomUserAgent(valeur de chaîne)
   * getCustomUserAgent()

* Partagez des cookies entre l’application Android et TVSDK : Android TVSDK prend désormais en charge l’accès aux cookies entre le calque JAVA (stocké dans le magasin de cookies de l’application Android) et le calque C++ TVSDK. Désormais, il est possible de définir et/ou de modifier les cookies dans le calque C++ natif, car ils seront exposés au magasin de cookies Java.
* Modifications de l’API :

   * Un nouvel  CookiesUpdateEvent est ajouté. Il est distribué par le lecteur de médias lorsque son cookie est mis à jour.

   * Une nouvelle API est ajoutée à NetworkConfiguration::set/ getCustomUserAgent() pour utiliser l&#39;agent utilisateur personnalisé.

   * Une nouvelle API est ajoutée à NetworkConfiguration::set/ getEncodedUrlForTracking pour forcer le codage des caractères dangereux.

   * Une nouvelle API est ajoutée à NetworkConfiguration::getNetworkDownVerifyUrl() pour définir une URL de vérification réseau en cas de basculement.

   * Une nouvelle propriété est ajoutée à TextFormat::trahirSpaceAsAlphaNum qui définit si l’espace doit être traité comme alphanumérique lors de l’affichage des légendes.

* Modifications dans SizeAvailableEvent : Auparavant, les méthodes getHeight() et getWidth() de SizeAvailableEvent dans la version 2.5.2 étaient utilisées pour renvoyer la hauteur et la largeur d’image, qui étaient renvoyées par le format multimédia. Désormais, il renvoie respectivement la hauteur et la largeur de sortie renvoyées par le décodeur.

* Modifications du comportement de mise en mémoire tampon : Le comportement de mise en mémoire tampon est modifié. Il reste aux développeurs d’applications ce qu’ils veulent faire en cas de vide de la mémoire tampon. 2.5.3 utilise la taille du tampon de lecture en cas de vide du tampon.

**Version 2.5.2**

Android TVSDK v2.5.2   des correctifs importants et quelques modifications d’API.

**Version 2.5.1**

Les nouvelles fonctionnalités importantes d’Android 2.5.1.

* **Améliorations** des performancesLa nouvelle architecture TVSDK 2.5.1 apporte un certain nombre d’améliorations des performances. Sur la base des statistiques d’une étude d’analyse comparative tierce, la nouvelle architecture offre une réduction de 5 fois du temps de démarrage et de 3,8 fois moins d’images perdues par rapport à la moyenne du secteur :

   * **Instant on for VOD and live -** Lorsque vous activez l’activation instantanée, TVSDK initialise et met en mémoire tampon le média avant le  de lecture. Comme vous pouvez lancer plusieurs instances MediaPlayerItemLoader simultanément en arrière-plan, vous pouvez mettre en mémoire tampon plusieurs flux. Lorsqu’un utilisateur modifie le  du et que le flux a été mis en mémoire tampon correctement, la lecture sur le nouvel  de  immédiatement. TVSDK 2.5.1 prend également en charge l’installation pour les flux **en direct** . Les flux en direct sont remis en mémoire tampon lorsque la fenêtre active se déplace.

   * **Logique ABR améliorée -** La nouvelle logique ABR est basée sur la longueur de la mémoire tampon, le taux de changement de la longueur de la mémoire tampon et la bande passante mesurée. Ainsi, l’ABR choisit le débit approprié lorsque la bande passante fluctue et optimise le nombre de fois où le commutateur de débit se produit réellement en surveillant le débit auquel la longueur de la mémoire tampon change.

   * **Téléchargement de segment partiel / Sous-segmentation -** TVSDK réduit davantage la taille de chaque fragment, afin de  la lecture le plus tôt possible. Le fragment de texte doit avoir une image clé toutes les deux secondes.

   * **Résolution des publicités irrégulières -** TVSDK n’attend pas la résolution des publicités non preroll avant de commencer la lecture, ce qui réduit le temps de démarrage. Les API telles que la recherche et le jeu vidéo ne sont toujours pas autorisées tant que toutes les publicités ne sont pas résolues. Ceci s’applique aux flux VOD utilisés avec l’ISAC. Les opérations telles que la recherche et l’avance rapide ne sont pas autorisées tant que la résolution de la publicité n’est pas terminée. Pour les flux en direct, cette fonction ne peut pas être activée pour la résolution des publicités pendant un  en direct.

   * **Connexions réseau persistantes -** Cette fonctionnalité permet à TVSDK de créer et de stocker un interne de connexions réseau persistantes. Ces connexions sont réutilisées pour plusieurs requêtes, plutôt que d’ouvrir une nouvelle connexion pour chaque requête réseau, puis de la détruire par la suite. Cela augmente l’efficacité et diminue la latence du code réseau, ce qui accélère les performances de lecture.
Lorsque TVSDK ouvre une connexion, il demande au serveur d’établir une connexion *continue* . Certains serveurs peuvent ne pas prendre en charge ce type de connexion. Dans ce cas, TVSDK revient à établir une connexion pour chaque requête. En outre, bien que les connexions persistantes soient activées par défaut, TVSDK dispose désormais d’une option de configuration qui permet aux applications de désactiver les connexions persistantes si nécessaire.

   * **Téléchargement parallèle -** Le téléchargement vidéo et audio en parallèle plutôt qu’en série réduit les délais de démarrage. Cette fonctionnalité permet la lecture des fichiers HLS Live et VOD, optimise l’utilisation de la bande passante disponible à partir d’un serveur, réduit la probabilité d’accès à des situations de mémoire tampon en cours d’exécution et réduit le délai entre le téléchargement et la lecture.

   * **Téléchargements de publicités parallèles : TVSDK prérécupère les publicités en parallèle à la lecture du contenu avant d’atteindre les coupures publicitaires, ce qui permet une lecture transparente des publicités et du contenu.**

* **Lecture**

   * **Lecture de contenu MP4 : il n’est pas nécessaire de recoder les clips courts MP4** pour les lire dans TVSDK.
      > [!NOTE]
      >
      > Le basculement ABR, la lecture de l’astuce, l’insertion d’annonces publicitaires, la liaison audio tardive et la sous-segmentation ne sont pas pris en charge pour la lecture au format MP4.

   * **Lecture vidéo avec débit binaire adaptatif (ABR) -** Cette fonctionnalité permet à TVSDK de basculer entre les flux iFrame en mode de lecture par astuce. Vous pouvez utiliser des non iFrame pour jouer à des vitesses de lecture inférieures.

   * **Lecture plus fluide -** Ces améliorations améliorent l’expérience des utilisateurs :

      * Sélection adaptative de la vitesse de transmission et de la fréquence d’images lors de la lecture de l’astuce, en fonction de la bande passante et des  de mémoire tampon

      * Utilisez le flux principal au lieu du flux IDR pour obtenir une lecture rapide jusqu’à 30 ips.

* **Protection du contenu**

   * **Protection de sortie basée sur la résolution -** cette fonctionnalité associe les restrictions de lecture à des résolutions spécifiques, fournissant des commandes DRM plus fines.

* **Prise en charge des processus**

   * **Intégration de la facturation directe : envoie les mesures de facturation au serveur principal d’Adobe Analytics, qui est certifié par Adobe Primetime pour les flux utilisés par le client.**
   TVSDK collecte automatiquement les mesures, en respectant le contrat de vente du client afin de générer des rapports d’utilisation périodiques requis pour la facturation. Sur chaque de flux  , TVSDK utilise l’API d’insertion de données Adobe Analytics pour envoyer des mesures de facturation telles que le type de contenu, les indicateurs activés pour l’insertion de publicités et les indicateurs activés pour l’insertion de données drm - en fonction de la durée du flux facturable - à la suite de rapports d’Adobe Analytics Primetime. Cela n’interfère pas avec les suites de rapports Adobe Analytics ou les appels au serveur du client ou ne les inclut pas. Sur demande, ce rapport sur l’utilisation de la facturation est envoyé régulièrement aux clients. Il s’agit de la première phase de la fonction de facturation qui prend uniquement en charge la facturation d’utilisation. Il peut être configuré en fonction du contrat de vente à l’aide des API décrites dans la documentation. Cette fonction est activée par défaut. Pour désactiver cette fonctionnalité, reportez-vous à l’exemple du lecteur de référence.

   * **Prise en charge du basculement améliorée -** Des stratégies supplémentaires ont été mises en oeuvre pour poursuivre la lecture ininterrompue, malgré les échecs des serveurs hôtes, des fichiers de liste de lecture et des segments.


* **Publicité**

   * **Intégration des douves -** Prise en charge de la mesure de la capacité d’affichage des publicités à partir de la couche.

   * **Bannières d’accompagnement :** les bannières d’accompagnement s’affichent à côté d’une publicité linéaire et continuent souvent d’être affichées sur le  après la fin de la publicité. Ces bannières peuvent être de type html (fragment de code HTML) ou iframe (URL d’une page iframe).

* **Analytics**

   * **VHL 2.0 -** Il s’agit de la dernière intégration de la bibliothèque Video Heartbeats (VHL) optimisée pour la collecte automatique des données d’utilisation d’Adobe Analytics. La complexité des API a été réduite pour faciliter l’implémentation. Téléchargez la bibliothèque VHL [v2.0.0 pour Android](https://github.com/Adobe-Marketing-Cloud/video-heartbeat-v2/releases) et extrayez le fichier JAR dans le dossier libs.

* **SizeAvaliableEventListener**

   * Les méthodes getHeight() et getWidth() de SizeAvailableEvent renvoient désormais respectivement la sortie en hauteur et en largeur. Le format d’affichage peut être calculé comme suit :

   ```java
   SizeAvailableEvent e;
   DAR = e.getWidth()/ e.getHeight();
   ```

    rapport L/H  du en termes de largeur et de hauteur de l’Ear peuvent également être utilisés pour calculer la largeur et la hauteur de l’image :

   ```java
   SAR = e.getSarWidth()/e.getSarHeight();
   frameHeight = e.getHeight();
   frameWidth = e.getWidth()/SAR;
   ```

* **Cookies**

   * Android TVSDK prend désormais en charge l’accès aux cookies JAVA stockés dans le magasin de cookies de l’application Android. Une API de rappel (onCookiesUpdate) est fournie pour l’enregistrement chaque fois qu’un nouveau cookie est inclus dans l’en-tête de réponse &quot;Set-Cookie&quot;. Ces cookies sont disponibles en tant que  de cookie(s) HttpCookie(s) utilisé(s) pour un URI/domaine différent en définissant ces valeurs de cookie sur cet URI/domaine particulier à l’aide de CookieStore. De même, les valeurs de cookie dans TVSDK sont mises à jour à l’aide de l’API d’ajout CookieStore.

## Matrice des fonctionnalités {#feature-matrix}

TVSDK pour Android prend en charge un certain nombre de fonctionnalités que vous pouvez implémenter pour ajouter des fonctionnalités à vos applications vidéo.

Dans les tableaux de fonctionnalités ci-dessous, un Y indique que la fonctionnalité est prise en charge dans la version actuelle.

| Fonctionnalité | Type de contenu | HLS |
|---|---|---|
| Lecture générale (Lecture, Pause, Recherche) | VOD + Live | Y |
| FER - Lecture générale (Lecture, Pause, Recherche) | FER VOD | Y |
| Rechercher quand une publicité est en cours de lecture | Live | Non pris en charge |
| AC3 | VOD + Live | Non pris en charge |
| MP3 | VOD | Non pris en charge |
| Lecture de contenu MP4 | VOD | Y |
| Logique de commutation de débit adaptatif | VOD + Live | Y |
| Lecture audio uniquement | VOD + Live | Y |
| Prise en charge multi-CDN | VOD + Live | Non pris en charge |
| Lecture des publicités avec support audio uniquement | VOD + Live | Non pris en charge |
| Sous-titres - 608/708 | VOD + Live | Y |
| Sous-titres - WebVTT | VOD + Live | Y |
| Basculement du manifeste | VOD + Live | Y |
| Basculement avancé | VOD + Live | Y |
| Notifications QoS et du lecteur | VOD + Live | Y |
| Prise en charge des en-têtes de cookie | VOD + Live | Y |
| Prise en charge des en-têtes HTTP personnalisés | VOD + Live | Y (liste blanche requise) |
| Définition des paramètres de contrôle de la mémoire tampon | VOD + Live | Y |
| Définition des contrôles de débit binaire adaptatif | VOD + Live | Y |
| Balises de manifeste personnalisées | VOD + Live | Y |
| Liaison audio tardive | VOD + Live | Y |
| 302 Redirection | VOD + Live | Y |
| Lecture avec décalage | VOD + Live | Y |
| Lecture audio uniquement | VOD + Live | Y |
| Lecture de Trick | VOD + Live | Y |
| Mouvement lent dans la lecture en bande | VOD + Live | Non pris en charge |
| Lecture lisse (avec ABR) | VOD + Live | Y |
| Analyse ID3 | VOD + Live | Y |
| Blocage des publicités | VOD + Live | Non pris en charge |
| Instant activé | VOD + Live | Non pris en charge |
| Prise en charge des marqueurs de discontinuité | VOD + Live | Y |
| 302 Réorientation | VOD + Live | Y |

| Fonctionnalité | Type de contenu | HLS |
|---|---|---|
| Lecture générale, publicités activées | VOD + Live | Y |
| Contenu FER avec publicités activées | VOD | Y |
| Comportements publicitaires par défaut | VOD + Live | Y |
| VAST 2.0/3.0 | VOD + Live | Y |
| VMAP 1.0 | VOD + Live | Y |
| Annonces MP4 | VOD + Live | Y (provenant de CRS) |
| Lecture à l&#39;aide de publicités activée | VOD + Live | Y |
| Publicité uniquement | VOD | Y |
| Paramètres de ciblage | VOD + Live | Y |
| Paramètres personnalisés | VOD + Live | Y |
| Comportements publicitaires personnalisés | VOD + Live | Y |
| Balises publicitaires personnalisées | Live | Y |
| Résolveurs publicitaires personnalisés | VOD + Live | Y |
| Résolveur d’annonce personnalisé à roue libre | VOD | Y |
| C3 | VOD + Live | Non pris en charge |
| Résolution de publicité différée | VOD | Y |
| Prise en charge des marqueurs de discontinuité - SSAI | VOD + Live | Y |
| Publicités d’accompagnement, bannières publicitaires et publicités cliquables | VOD + Live | Y |
| VPAID 2.0 | VOD + Live | Y (JS) |
| Sortie de publicité anticipée | Live | Y |
| Hiérarchisation créative basée sur des règles | VOD + Live | Y |
| Règles CRS | VOD + Live | Y |
| JSON Ad Resolver | VOD + Live | Non pris en charge |
| Intégration de Moat | VOD + Live | Y |

| Fonctionnalité | Type de contenu | HLS |
|---|---|---|
| Chiffrement AES | VOD + Live | Y |
| Exemple de chiffrement AES | VOD + Live | Y |
| Flux jetés | VOD + Live | Y |
| DRM | VOD + Live | Primetime DRM uniquement (Futur : Widevine) |
| Lecture externe (RBOP) | VOD + Live | DRM Primetime uniquement |
| Rotation de licence | VOD + Live | DRM Primetime uniquement |
| Rotation clé | VOD + Live | DRM Primetime et DRM Widevine |

| Fonctionnalité | Type de contenu | HLS |
|---|---|---|
| Intégration d’Adobe Analytics VHL | VOD + Live | Y |
| Facturation | VOD + Live | Y |

## Problèmes résolus {#resolved-issues}

Lorsque la résolution est associée à un problème signalé, une référence Zendesk s’affiche, par exemple ZD#xxxxx.

**Android TVSDK 3.11**

Cette section présente un résumé du problème résolu dans la version Android 3.11 de TVSDK.

* ZD# - Les caractères coréens sont affichés comme symboles de glyphe manquants pour les manifestes HLS avec WebVTT dans l’application de référence Android TVSDK.

### Problèmes résolus dans les versions précédentes

**Android TVSDK 3.10**

* ZD#40340 - L’application se bloque avec l’erreur &quot;App Not Responding&quot; lors de la tentative de lecture après la mise en liste noire de tous les fichiers TS (TypeScript).

**Android TVSDK 3.8**

* Aucun nouveau problème ajouté.

**Android TVSDK 3.7**

* Aucun nouveau problème ajouté.

**Android TVSDK 3.6**

* Aucun nouveau problème ajouté.

**Version 3.5**

* ZD#37503 - Les réponses JSON pour les règles CRS sont mises en cache afin d’éviter les demandes de  du.

**Version 3.4**

* ZD#37996 - Correction d’un problème de lecture en bloc pour les flux HEVC CMAF linéaires et VOD.
* ZD#37706 - Correction d’un problème lié aux légendes altérées.
* ZD#37622 - Correction d’un problème concernant les erreurs URISyntaxErrors irrécupérables pour des annonces spécifiques.
* ZD#36938 - Correction d’un problème en raison duquel le débit descendait vers le débit moyen, puis atteignait le débit le plus élevé après avoir quitté les lectures de la série.

**Version 3.3**

* ZD#37394 - Une ressource CMAF avance rapide provoque des artefacts après le changement de vitesse.
   * Correction d’un problème qui se produisait lors d’un changement de  au cours d’une lecture par astuce.
* ZD#37396 - Il manque des  de suivi des publicités pour certains mi-parcours et post-roulements.
   * Correction d’un cas spécifique concernant les  de suivi des publicités.
* ZD#37491 - Code d’état HTTP avec méta d’erreur absent.
   * A travaillé à la propagation des erreurs réseau plus haut dans la pile.
* ZD#37808 - Nouvelle liste blanche en-tête personnalisé.
   * Prise en charge de SSAI_TAG ajoutée dans le cadre de ce correctif.
* ZD#37622 - Erreurs de syntaxe URIS à partir de capsules publicitaires spécifiques.
   * Correction d’un problème de blocage de la lecture en flux continu lorsque des publicités destinées à l’application Android du client contenaient un % non codé.
* ZD#37631 - Mécanisme de nouvelle tentative de manifeste principal pour le SDK TVSDK Android.
   * Ajout d’une nouvelle API dans la configuration réseau pour gérer cette amélioration. Si cette API n’est pas utilisée, le manifeste n’est pas réessayé. S&#39;il est utilisé, le manifeste est alors réessayé pour gérer les erreurs réseau et les dépassements de délai.

**Version 3.2**

* ZD#37493 - Les balises de suivi pour la lecture en direct ne sont pas déclenchées par intermittence pour la première publicité dans la séquence.
* ZD#36985 - Les balises de suivi ne sont pas envoyées pour les coupures publicitaires vides dans la réponse VMAP.
* ZD#37134 - TVSDK renvoie par intermittence un ID incorrect pour la réponse VMAP.

**Version 3.0**

* ZD#33740 - TVSDK lance un avertissement inutile juste après la création d’un objet MediaPlayer et l’appel de replaceCurrentResource()

   * Amélioration du correctif précédent en appelant la restauration uniquement lorsque le lecteur est en état de suspension

* ZD#36442 - Chaque nouvelle lecture déconnecte la session de débogage à distance, rendant impossible le débogage.

   * Le débogage n’est pas possible par défaut sur le Web  car le débogage n’est pas activé par défaut. L’application doit activer le débogage si nécessaire en appelant setWebContentDebuggingEnabled(true) sur l’objet renvoyé par MediaPlayer.getCustomAdView().

* ZD#33688 - Prise en charge de l’heure juste et résolution

   * Les coupures publicitaires sont résolues à un intervalle spécifié avant la position de la coupure publicitaire.

* ZD#36441 - La durée de la fenêtre active continue d’augmenter au-delà de 5 minutes, provoquant de nombreux problèmes.

   * Correction d’un problème en raison duquel la valeur virtualStartTime était ajoutée deux fois lors du calcul du point de direct virtuel, ce qui entraînait ce problème.

**Android TVSDK 2.5.6**

* ZD #34992 - La langue est vide dans la légende fermée.

   * Correction d’un cas où TVSDK n’analysait pas #EXT-X-MEDIA:TYPE=CLOSED-CAPTIONS du manifeste principal pour obtenir les détails du suivi de la légende.

* ZD #35078 - Validation P Android.

   * TVSDK 2.5.6 a été validé avec les dernières versions bêta d’Android P. Aucun problème n’a été détecté en raison du nouveau système d’exploitation Android.

* ZD #34149 - Le lecteur continue à demander des manifestes même en cas d’erreur.

   * Correction du cas où TVSDK effectuait des appels répétitifs même lorsque tous les  étaient en panne (erreur 404).

* ZD #31533 - Lecture audio sur Android après l’envoi de l’application en arrière-plan.

   * Ajout `enableAudioPlaybackInBackground` d’une API de MediaPlayer qui doit être appelée avec &quot;True&quot; comme argument (lorsque le lecteur est à l’état PRÉPARÉ) pour activer la lecture audio lorsque l’application est en arrière-plan.

**Android TVSDK 2.5.5**

* ZD #21647 - Le kit TVSDK Android signale le format 640x368 lorsque la taille réelle de la vidéo est de 640x360.

   * En raison de la variable m_nOutputHeight (dans AndroidMCVideoDecoder) mise à jour avec la hauteur d’image au lieu de la hauteur de sortie réelle. Modification appropriée de la fonction getVideoFrame pour calculer correctement m_nOutputHeight.

* ZD #26614 - Urgent — Service d&#39;annonce tiers / programmatique — échec de diffusion des impressions.

   * Amélioration du correctif précédent en gérant la casse dans l’analyse XML où le problème était reproductible lorsque &quot;space&quot; est placé avant le signe &quot;égal&quot; comme &lt;VAST version =&quot;2.0&quot;>

* ZD #29296 - Android : Ajouter AdSystem et ID Creative aux demandes CRS.

   * Incluez désormais &quot;AdSystem&quot; et &quot;CreativeId&quot; comme nouveaux paramètres dans les requêtes 1401 et 1403.

* ZD #33062 - Le TVSDK se bloque lors de l’occurrence du caractère pipe dans la réponse VAST sous le noeud CDATA

   * API setEncodeUrlForTracking dans la classe NetworkConfiguration supprimée en tant que caractères dangereux dans une URL à coder

* ZD #33063 - La logique de sélection des fichiers CRS a été rompue - TVSDK n&#39;envoyait pas de demande CRS pour le format web, mais pour les fichiers 3gpp à la place.

   * Correction de la logique maintenant. Lors de l&#39;utilisation de fichiers multimédias au format Web et 3gpp, le CRS demande à être envoyé pour le Web. Et en utilisant les deux fichiers de support au format 3gpp, la demande CRS à envoyer pour le fichier 3gpp à débit le plus élevé.

* ZD #33125 - L’application Android se bloque avec une balise DoubleClick spécifique dans le VMAP.

   * Correction du scénario pour éviter le blocage.

* ZD #32256 - Problème de rotation des licences et de rotation des clés - Adobe Access

   * Correction de l’initialisation des segments avec les métadonnées DRM pour le contenu SampleAES. Fonctionne correctement avec le contenu AES128.

* ZD #33619 - Transfert rapide d’un contenu de liste de lecture en croissance bloqué à l’état de mise en mémoire tampon près du point de production.

   * Traitement de l’affaire lors du passage du point de vie en mode de jeu par astuces

* ZD #34151 - Objets TimedMetadata dans l’ordre irrégulier.

   * Deux de métadonnées de type TimedMetadata s’affichaient dans un ordre aléatoire s’ils appartenaient à la même époque dans la chronologie. Maintien de leur ordre d’origine dans le manifeste.

* ZD #34189 - Problème lors de la recherche d’un début de coupure publicitaire.

   * Le problème concernait les publicités SSAI assemblées à l’aide de la discontinuité. Et la cause était un comportement quand nous cherchons au début de telles publicités, nous cherchons une image-clé et nous ne la trouvons pas. L’horodatage audio principal de la publicité était antérieur à l’horodatage vidéo principal. Par conséquent, nous finissons par rechercher une image clé à un fragmentDonnées de suppression erronées. Corrigé maintenant.

* ZD #34528 - Résolution vidéo ne passant pas au-delà de 640x360 sur le dongle 3e génération de FireTV.

   * Amélioration du correctif pour inclure les dernières mises à jour du microprogramme

* ZD #34793 - TVSDK 2.5.x se bloquait avec le programme de résolution de contenu personnalisé dans certains cas, lorsque VideoEngine supposait que les paramètres d’audience étaient disponibles et qu’ils ne l’étaient pas.

   * Le blocage survenait en raison d’un appel de fonction sur un pointeur partagé Null (auditudeSettings). Ajout d’une vérification conditionnelle dans VideoEngineTimeline::placeToSourceTimeline() pour vérifier que auditudeSettings est disponible avant d’appeler quoi que ce soit sur cet objet.

* ZD #32584 - Impossible d’accéder à l’information complète présente dans le noeud &lt;Extensions> d’une réponse VAST.

   * Correction d’un problème lié à l’analyse XML. Désormais, NetworkAdInfo fournit les informations complètes présentes dans le noeud &lt;Extensions>.

* ZD #35086 - Pas d’obtention des données d’extension complètes du lecteur en cas de réponses VMAP spécifiques.

   * Le problème était spécifique au xml d’extension, car l’analyse XML ne fonctionnait pas si le xml d’extension contenait des guillemets dans la valeur d’attribut. Correction du problème.

**Android TVSDK 2.5.4**

* ZenDesk#33659 - Session de lecture permettant le débogage à distance de la vue Web.

WebViewDebbuging est défini sur False par défaut. Pour activer le débogage, définissez la valeur sur true dans l’application, à l’aide de setWebContentDebuggingEnabled(true).

* ZenDesk#33011 - La chronologie de l’annonce n’est pas résolue en cas d’échec de la demande CRS.

   Lorsqu’une demande CRS envoyée à une publicité échoue, la chronologie est résolue et les publicités restantes sont lues.

* ZenDesk#34528 - La résolution vidéo n’est pas mise à niveau au-delà de 640x360 sur un dongle de troisième génération FireTV.

   La résolution vidéo s’affiche sous forme de commutateurs de débit binaire.

* ZenDesk#33192 - AudioTrack a un nom nul lorsque le suivi est récupéré via AudioUpdateEventListener::onAudioUpdate.

   Dans quelques scénarios sur FireTV Stick, le onAudioUpdate était déclenché lorsqu’il n’y avait pas de mise à jour audio réelle. C&#39;est réglé maintenant.

**Android TVSDK 2.5.3**

* Zendesk#32216 - Balise personnalisée TimedMetadata  le ne fonctionne pas.

   Nous renvoyons les données ID3 sous forme de tableau d’octets (pour prendre en charge les données APIC ou génériques) au client alors que dans la version 1.4, la chaîne de renvoi est renvoyée. Le tableau d’octets ne gère pas le caractère terminé nul lui-même. Par conséquent, il présentait un caractère spécial au client. Ce problème est maintenant résolu.
* Zendesk#32670 - Le lecteur n&#39;échoue pas sur la liste de lecture redondante

   Cela fonctionne correctement maintenant et setNetworkDownVerifyUrl fonctionne comme prévu.
* Zendesk#32369 - La légende fermée présente différentes couleurs de déchets ou d’artefacts.

   Le problème des problèmes CC a été résolu dans la dernière version
* Zendesk#25590 - Enhance : Boutique de cookies TVSDK ( C++ vers JAVA )

   Android TVSDK prend désormais en charge l’accès aux cookies entre le calque JAVA (stocké dans le magasin de cookies de l’application Android) et le calque C++ TVSDK.
* Zendesk#32252 - TVSDK_Android_2.5.2.12 ne semble pas avoir le correctif pour PTPLAY-20269

   Ce problème a été corrigé et intégré à la branche 2.5.2.
* Zendesk#31806 - Colonnes d&#39;Auditude pour PRÉPARATION

   Le lecteur était bloqué dans l’état Préparation, car le xml de réponse avait une balise vide. Le problème est maintenant résolu.
* Zendesk#31727 - Les caractères de sous-titrage codé TVSDK 2.5 sont ignorés ou mal orthographiés.

   Le problème est résolu et nous ne supprimons ni n’épelons aucun caractère par erreur.
* Zendesk#31485 - DrmManager dans la version 2.5

   Un problème est survenu lors de la création de DrmManager via le nouveau contexte DrmManager (contexte). Mise en oeuvre de la classe DRMService qui fournirait DRMManager.
* Flux de résolution Zendesk#32794- 1080P non lu sur Android

   nous avons modifié les méthodes SizeAvailableEvent et précédemment, getHeight() et getWidth() de SizeAvailableEvent dans la version 2.5 afin de renvoyer la hauteur et la largeur d’image, qui ont été renvoyées par le format multimédia. Il renvoie désormais respectivement la hauteur et la largeur de sortie renvoyées par le décodeur.
* Zendesk #19359 Flash Player se bloque en raison de la position de l’attribut #EXT-X-FAXS-CM dans le manifeste de niveau défini.

   La balise #EXT-X-FAXS-CM doit toujours apparaître dans la liste de lecture supérieure avant que le débit ou les segments individuels n’apparaissent dans la liste de lecture.

**Android TVSDK 2.5.2**

* Zendesk#17305 Artefacts dans des sous-titres codés avec un arrière-plan non opaque.

   La propriété setTreatSpaceAsAlphaNum de TextFormat est exposée. Par défaut, la propriété est False. Définissez la propriété sur True dans un client pour résoudre le problème de l’espace sombre.

* L’affichage Zendesk#25097 CC comporte des artefacts visuels avec les paramètres CC.

   La propriété setTreatSpaceAsAlphaNum de TextFormat est exposée. Par défaut, la propriété est False. Définissez la propriété sur True dans un client pour résoudre le problème de l’espace sombre.

* Zendesk #31620 La chaîne de l’agent utilisateur sortant du lecteur TVSDK est tronquée.

   La chaîne de l’agent utilisateur ne sera plus tronquée après 128 caractères.

   La chaîne de version Adobe Primetime est ajoutée à l’agent utilisateur système.

* Le SEEK_END manquant de Zendesk #30809 empêche l’application de passer à un état de lecture.
* La couleur &quot;cyan&quot; de Zendesk #30415 Closed Caption est maintenant une teinte plus foncée de bleu (turquoise), par rapport aux versions précédentes de Primetime TVSDK.

   La couleur est passée de DarkCyan à Cyan.

* Les annonces VOD #30727 Zendesk ne sont pas téléchargées/résolues.

   Dans VMAP XML, s’il existe une balise VAST vide sans balise de fermeture explicite (&quot;&lt;/VAST>&quot;) et sans caractère de nouvelle ligne après, le code VMAP XML n’est pas analysé correctement et les publicités peuvent ne pas être lues.

**Android TVSDK 2.5.1**

* Crash spécifique au périphérique (Samsung Galaxy Tab 4) ; VOD DRM LBA avec Auditude et cliquez sur les annonces.
* VHL - Des appels de pulsation incorrects sont envoyés lors du démarrage du contenu à partir d’un décalage.
* Lors de la lecture des publicités VPAID, les appels de pulsation VHL pour les annonces:type:play sont manquants.
* Après avoir atteint l’état COMPLET, le lecteur revient à l’état LECTURE avec SKIP adBreakPolicy pour les publicités postroulantes.
* Les cookies ne sont pas associés aux rappels publicitaires sortants.
* Les indices publicitaires ne sont pas visibles.
* HLS avec une piste SAP EAC3 séparée ne se charge pas.
* Le lecteur se bloque lorsque TVSDK reçoit un message d’activation d’écran après la restauration du lecteur multimédia.

## Problèmes et limites connus {#known-issues-and-limitations}

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

* ID3, Sous-titres, Prise en charge de l’audio de liaison tardive n’a pas été vérifiée pour le flux CMAF (CBC).
* Sur certains appareils, il existe un problème de faible reproductibilité dû à la distorsion vidéo qui peut apparaître en haut lors de la lecture de l’astuce sur les flux CMAF.

**Android TVSDK 3.3**

* Les légendes clcp:c608 ne sont pas prises en charge pour la lecture de flux CMAF.

**Android TVSDK 3.2**

* TVSDK 3.2 ne prend pas en charge la lecture des flux CMAF Sample AES et AES128.
* Les flux CMAF HEVC ne prennent pas en charge la lecture des sous-titres.
* La coloration verte s’affiche pour les flux chiffrés WV lorsque la recherche est effectuée autour du segment non chiffré.
* Les flux CMAF ne prennent pas en charge les  ID3.
* Les flux HLS ne prennent pas en charge le format des légendes HTML.

**Android TVSDK 3.0**

* La prise en charge de HEVC présente les restrictions suivantes dans cette version

   * DRM non pris en charge
   * Prise en charge CC (CEA 608/708) non vérifiée
   * La prise en charge de 4K n&#39;est pas encore présente
   * Prise en charge des balises ID3 non vérifiée

* Pour les  de progression de la publicité, la barre de chronologie peut ne pas refléter une durée de lecture de la publicité 100 % précise. Pour pallier ce problème, vous pouvez `adcompleteevent` connaître l’achèvement de la lecture de la publicité et mettre à jour l’interface utilisateur à diverses fins, comme la mise à jour de la barre de chronologie, la suppression de l’interface utilisateur associée à la publicité, etc.
* Les appels de publicités volumineuses renvoyés par VMAP ne respectent pas la position d’anticipation Juste à Temps.

**Android TVSDK 2.5.6**

* Plusieurs pauses publicitaires VMAP en même temps ne sont pas prises en charge.

**Android TVSDK 2.5.3**

Cette version présente les problèmes suivants :

* La lecture vidéo en direct peut présenter des problèmes de synchronisation audio-vidéo sur les périphériques bas de gamme ou de mauvaises conditions réseau.
* Pour les flux FER, virtualTime et localTime peuvent différer. FER avec décalage ne fonctionne pas non plus.
* La lecture peut être bloquée lorsque la recherche porte sur le contenu de l’audio de liaison tardive.
* Par intermittence, les légendes webVTT peuvent devenir désynchronisées pour le contenu LIVE.
* Par intermittence, la lecture rapide de quelques images peut être vue après une coupure publicitaire.
* Parfois, une erreur 303 est générée pour Tripple Wrapper Ad Breaks, même si des publicités sont lues.

**Android TVSDK 2.5.2**

Cette version présente les problèmes suivants :

* La lecture vidéo en direct peut présenter des problèmes de synchronisation audio-vidéo sur les périphériques bas de gamme.
* La lecture peut s’interrompre à certains moments lorsqu’il s’agit d’atteindre la fin du média VOD.
* Pour les flux FER, virtualTime et localTime peuvent différer. En outre, FER avec décalage ne fonctionne pas.

**Android TVSDK 2.5.1**

Cette version de TVSDK présente les problèmes suivants :

* La lecture vidéo en direct peut présenter des problèmes de synchronisation audio-vidéo sur les périphériques bas de gamme.
* Pour les flux FER, virtualTime et localTime peuvent différer. En outre, FER avec décalage ne fonctionne pas.
* Dans VMAP XML, s’il existe une balise VAST vide sans balise de fermeture explicite (&lt;/VAST>) et sans nouvelle ligne après, le fichier VMAP XML n’est pas analysé correctement et les publicités peuvent ne pas être lues.
* Les post-roulements VPAID ne sont pas pris en charge.

## Ressources utiles {#helpful-resources}

* [Configuration système requise](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-requirements.html)
* [Guide du programmeur Android TVSDK 3.10](https://docs.adobe.com/content/help/en/primetime/programming/tvsdk-3x-android-prog/introduction/android-3x-overview-prod-audience-guide.html)
* [Javadoc Android TVSDK pour référence API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.5/index.html)
* [](https://help.adobe.com/en_US/primetime/api/psdk/cpp_3.5/namespaces.html) d’API C++ TVSDK Android C++ - Chaque classe Java possède une classe C++ correspondante et la documentation C++ contient plus de texte explicatif que les Javadocs. Reportez-vous donc à la documentation C++ pour une meilleure compréhension de l’API Java.
* [Guide de migration de TVSDK 1.4 à 2.5 pour Android (Java)](https://helpx.adobe.com/primetime/migration-guides/tvsdk-14-25-android.html)
* Pour gérer les scénarios d’activation/désactivation d’écran, consultez le `Application_Changes_for_Screen_On_Off.pdf` fichier inclus dans la version.
* Reportez-vous à la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.
