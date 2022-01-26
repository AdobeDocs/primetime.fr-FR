---
title: Notes de mise à jour de TVSDK 2.7 pour Android™
description: Les notes de mise à jour de TVSDK 2.7 pour Android™ décrivent les nouveautés ou les modifications, les problèmes résolus et connus et les problèmes d’appareil dans TVSDK Android™ 2.7
products: SG_PRIMETIME
topic-tags: release-notes
exl-id: d64f0ef2-60a9-43a1-b2f9-44764a570538
source-git-commit: d2c8133f126db44b9c505dc0a21ba208fd6c01c8
workflow-type: tm+mt
source-wordcount: '4072'
ht-degree: 0%

---

# Notes de mise à jour de TVSDK 2.7 pour Android™ {#tvsdk-for-android-release-notes}

Les notes de mise à jour de TVSDK 2.7 pour Android™ décrivent les nouveautés ou les modifications, les problèmes résolus et connus et les problèmes d’appareil dans TVSDK Android™ 2.7

## TVSDK Android™ 2.7 {#tvsdk-android}

Le lecteur de référence Android™ est inclus avec Android™ TVSDK dans le répertoire samples/ de votre distribution. Le fichier README&lt;.md qui l’accompagne explique comment créer le lecteur de référence.

>[!NOTE]
>
>Pour créer correctement le lecteur de référence, comme décrit dans le fichier README.md distribué avec la version, veillez à effectuer les opérations suivantes :
>
>1. Téléchargez VideoHeartbeat.jar depuis [https://github.com/Adobe-Marketing-Cloud/media-sdks/releases](https://github.com/Adobe-Marketing-Cloud/media-sdks/releases) (Bibliothèque VideoHeartbeat pour Android™ v2.0.0)
>1. Extrayez VideoHeartbeat.jar dans le dossier libs/ .

>


## Nouvelles fonctionnalités {#new-features}

TVSDK 2.7 pour Android™ comprend toutes les fonctionnalités de la version 1.4, à l’exception des fonctionnalités non prises en charge répertoriées sous [Matrice de fonctionnalités](#feature-matrix).

**Android™ TVSDK 2.7**

* **Prise en charge parallèle de la résolution des publicités**

TVSDK 2.7 prend en charge la résolution simultanée de toutes les demandes d’annonce dans une coupure publicitaire, au lieu de la résolution séquentielle.

### Nouvelles fonctionnalités des versions précédentes {#new-features-previous-releases}

**Version 2.5.6**

* **TVSDK 2.5 prend en charge Android™ P**
* **Activation de l’audio en arrière-plan**

   Pour activer la lecture audio lorsque l’application passe du premier plan à l’arrière-plan, l’application doit appeler l’API enableAudioPlaybackInBackground de MediaPlayer avec la valeur true comme argument lorsque le lecteur est à l’état PRÉPARÉ.

* **alwaysUseAudioOutputLatency(valeur booléenne) dans la classe MediaPlayer**

Lorsqu’elle est définie, utilisez la latence de sortie dans le calcul de l’horodatage audio.
Valeur des paramètres booléens : la valeur True utilise la latence de sortie audio dans le calcul de l’horodatage audio.

* **Optimisé pour obtenir la meilleure expérience de lecture, même si la vitesse de bande passante diminue soudainement.**
TVSDK annule désormais le téléchargement du segment en cours, si nécessaire, et passe dynamiquement au rendu approprié. Pour ce faire, il suffit de basculer facilement entre les débits sans interruption.

**Version 2.5.5**

* **Insertion de coupure publicitaire partielle**

   Expérience de type télévision consistant à se joindre au milieu d’une publicité sans déclencher le suivi pour la publicité visionnée partiellement.\
   Exemple**: **L’utilisateur se joint au milieu (à 40 secondes) d’une coupure publicitaire de 90 secondes composée de trois publicités de 30 secondes. Cette coupure intervient 10 secondes dans la seconde publicité.
   * La deuxième publicité est lue pendant la durée restante (20 secondes), suivie de la troisième publicité.
   * Les dispositifs de suivi des publicités pour la publicité partielle lue (deuxième publicité) ne sont pas déclenchés. Les dispositifs de suivi de la troisième publicité uniquement sont déclenchés.

* **Chargement sécurisé des publicités par HTTPS**

   Adobe Primetime offre une option pour demander le premier appel au serveur de publicités en temps réel et à CRS sur https.

* **Ajout d’AdSystem et d’un ID créatif aux requêtes CRS**

   * Incluez désormais &quot;AdSystem&quot; et &quot;CreativeId&quot; comme nouveaux paramètres dans les requêtes 1401 et 1403.

* **API setEncodeUrlForTracking dans la classe NetworkConfiguration supprimée** car les caractères dangereux d’une URL doivent être codés.

**Version 2.5.4**

Android™ TVSDK v2.5.4 propose les mises à jour et modifications suivantes de l’API :

* Modifications de la valeur par défaut pour `WebViewDebbuging`

   `WebViewDebbuging` sont définies sur False par défaut. Pour l’activer, appelez setWebCon`tentsDebuggingEnabled(true) dans l’application.
* Mise à jour de la version OpenSSL et Curl `libcurl` vers la version 7.57.0 et OpenSSL vers la version 1.0.2k.
* Accès au niveau de l’application pour l’objet de réponse VAST Introduction d’une nouvelle API NetworkAdInfo::getVastXml() qui permet d’accéder à l’objet de réponse VAST de l’application.

**Version 2.5.3**

Android™ TVSDK v2.5.3 propose les mises à jour et modifications suivantes de l’API.

* Tous les clients TVSDK qui utilisent CRS sont encouragés à mettre à niveau leurs applications avec TVSDK 2.5.3.85 ou version ultérieure sur Android™. Il s’agit d’un élément de remplacement de la mise en oeuvre de l’application existante. Après la mise à niveau de TVSDK, recherchez les demandes d’URL créatives CRS dans un outil proxy (par exemple : Charles) et confirmez que le nom d’hôte et la version du chemin d’accès se reflètent comme dans l’exemple de structure d’URL ci-dessous.

   `https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784 bf3586d.m3u8`

* Agent utilisateur TVSDK personnalisable : nous avons ajouté de nouvelles API pour personnaliser les agents utilisateur.

   * `setCustomUserAgent`(valeur de chaîne)
   * `getCustomUserAgent`()

* Partagez des cookies entre l’application Android™ et TVSDK : Android™ TVSDK prend désormais en charge l’accès aux cookies entre la couche Java™ (stockée dans CookieStore de l’application Android™) et la couche C++ TVSDK. Désormais, il est possible de définir et/ou modifier les cookies dans la couche C++ native lorsqu’ils sont exposés au magasin de cookies Java™.
* Modifications des API :

   * Un nouvel événement CookiesUpdatedEvent est ajouté. Il est distribué par le lecteur multimédia lorsque son cookie est mis à jour.
   * Une nouvelle API est ajoutée à `NetworkConfiguration::set/ getCustomUserAgent()` pour utiliser un agent utilisateur personnalisé.
   * Une nouvelle API est ajoutée à `NetworkConfiguration::set/ getEncodedUrlForTracking` pour forcer le codage des caractères dangereux.
   * Une nouvelle API est ajoutée à `NetworkConfiguration::getNetworkDownVerificationUrl()` pour définir une URL de vérification réseau en cas de basculement.
   * Une nouvelle propriété est ajoutée à TextFormat::traînerSpaceAsAlphaNum, qui définit si l’espace doit être traité comme alphanumérique lors de l’affichage des légendes.

* Changements dans `SizeAvailableEvent`: Auparavant, les méthodes getHeight() et getWidth() de `SizeAvailableEvent` dans la version 2.5.2, utilisé pour renvoyer la hauteur et la largeur d’image, qui ont été renvoyées par le format multimédia. Désormais, elle renvoie respectivement la hauteur et la largeur de sortie renvoyées par le décodeur.
* Changements du comportement de la mise en mémoire tampon : Le comportement de la mise en mémoire tampon est modifié. Il reste au développeur d’applications ce qu’il souhaite faire s’il y a une mémoire tampon vide. La version 2.5.3 utilise la taille de la mémoire tampon de lecture en cas de vide de la mémoire tampon.

**Version 2.5.2**

Android™ TVSDK v2.5.2 propose des correctifs de bogues importants et quelques modifications de l’API.

**Version 2.5.1**

Nouvelles fonctionnalités importantes publiées dans Android™ 2.5.1.

* **Amélioration des performances** La nouvelle architecture TVSDK 2.5.1 apporte plusieurs améliorations de performances. Sur la base des statistiques d’une étude d’évaluation des performances tierce, la nouvelle architecture offre une réduction de 5 fois le temps de démarrage et de 3,8 fois moins d’images perdues que la moyenne du secteur :

   * **Instant on pour VOD et live -** Lorsque vous activez l’instantané, TVSDK s’initialise et met en mémoire tampon le média avant le début de la lecture. Comme vous pouvez lancer plusieurs instances MediaPlayerItemLoader simultanément en arrière-plan, vous pouvez mettre en mémoire tampon plusieurs flux. Lorsqu’un utilisateur modifie le canal et que la diffusion a été mise en mémoire tampon correctement, la lecture du nouveau canal commence immédiatement. TVSDK 2.5.1 prend également en charge Instant On pour **live** flux également. Les diffusions en direct sont mises en mémoire tampon lorsque la fenêtre active se déplace.

      * **Amélioration de la logique ABR -** La nouvelle logique ABR repose sur la longueur de la mémoire tampon, le taux de changement de la longueur de la mémoire tampon et la bande passante mesurée. Ainsi, l’ABR choisit le débit approprié lorsque la bande passante fluctue et optimise le nombre de fois où le changement de débit se produit réellement en surveillant la vitesse à laquelle la longueur de la mémoire tampon change.
      * **Téléchargement/sous-segmentation partiel -** TVSDK réduit davantage la taille de chaque fragment afin de lancer la lecture dès que possible. Le fragment ts doit disposer d’un cadre clé toutes les deux secondes.
      * **Résolution publicitaire différée -** TVSDK n’attend pas la résolution des publicités non preroll avant de commencer la lecture, ce qui réduit le temps de démarrage. Les API telles que la recherche et le jeu vidéo ne sont toujours pas autorisées tant que toutes les publicités ne sont pas résolues. Ceci s’applique aux flux VOD utilisés avec l’interface de ligne de commande. Les opérations telles que la recherche et le transfert rapide ne sont pas autorisées tant que la résolution de la publicité n’est pas terminée. Pour les diffusions en direct, cette fonctionnalité ne peut pas être activée pour la résolution de publicités au cours d’un événement en direct.
      * **Connexions réseau persistantes -** Cette fonctionnalité permet à TVSDK de créer et de stocker une liste interne de connexions réseau persistantes. Ces connexions sont réutilisées pour plusieurs requêtes, plutôt que d’ouvrir une nouvelle connexion pour chaque requête réseau, puis de la détruire par la suite. Cela augmente l’efficacité et réduit la latence du code de mise en réseau, ce qui entraîne des performances de lecture plus rapides.
Lorsque TVSDK ouvre une connexion, il demande au serveur une *keep-alive* connexion. Certains serveurs peuvent ne pas prendre en charge ce type de connexion. Dans ce cas, TVSDK revient à établir une connexion pour chaque demande à nouveau. En outre, alors que les connexions persistantes sont activées par défaut, TVSDK dispose désormais d’une option de configuration qui permet aux applications de désactiver les connexions persistantes si nécessaire.
      * **Téléchargement parallèle -** Le téléchargement vidéo et audio en parallèle plutôt que dans les séries réduit les délais de démarrage. Cette fonctionnalité permet de lire les fichiers HLS Live et VOD, optimise l’utilisation de la bande passante disponible à partir d’un serveur, réduit la probabilité d’entrer dans des situations de mémoire tampon en cours d’exécution et réduit le délai entre le téléchargement et la lecture.
      * **Téléchargements de publicités parallèles -** TVSDK récupère les publicités en parallèle à la lecture du contenu avant d’atteindre les coupures publicitaires, ce qui permet une lecture transparente des publicités et du contenu.

* **Lecture**

   * **Lecture de contenu MP4 -** Il n’est pas nécessaire de retranscoder les extraits MP4 courts pour les lire dans TVSDK.
Remarque : Le changement ABR, la lecture de l’astuce, l’insertion de publicités, la liaison audio tardive et la sous-segmentation ne sont pas pris en charge pour la lecture MP4.
   * **Lecture de la copie avec débit adaptatif (ABR) -** Cette fonctionnalité permet à TVSDK de basculer entre les diffusions iFrame en mode de lecture de l’astuce. Vous pouvez utiliser des profils non iFrame pour effectuer des opérations de lecture à des vitesses inférieures.
   * **Jeu de astuces lisser -** Ces améliorations améliorent l’expérience utilisateur :

          * Sélection de débit binaire adaptatif et de débit d’image lors de la lecture de l’astuce, en fonction de la bande passante et du profil de mémoire tampon
          * Utilisation de la diffusion principale au lieu de la diffusion IDR pour une lecture rapide jusqu’à 30 ips.
      
* **Protection du contenu**

   * **Protection des sorties basée sur la résolution -** Cette fonctionnalité associe les restrictions de lecture à des résolutions spécifiques, fournissant des contrôles DRM plus précis.

* **Prise en charge des workflows**

   * **Intégration de la facturation directe -** Cela envoie les mesures de facturation au serveur principal Adobe Analytics, qui est certifié par Adobe Primetime pour les diffusions utilisées par le client.
TVSDK collecte automatiquement les mesures, en conformité avec le contrat de vente client, afin de générer des rapports d’utilisation périodiques requis à des fins de facturation. Pour chaque événement de démarrage de flux, TVSDK utilise l’API d’insertion de données d’Adobe Analytics pour envoyer des mesures de facturation telles que le type de contenu, les indicateurs activés pour l’insertion de publicités et les indicateurs activés pour la collecte de données drm (selon la durée du flux facturable) à la suite de rapports détenue par Adobe Analytics Primetime. Cela n’interfère pas avec les suites de rapports Adobe Analytics ou les appels au serveur du client, ni ne les inclut dans celles-ci. Sur demande, ce rapport sur l’utilisation de la facturation est envoyé régulièrement aux clients. Il s’agit de la première phase de la fonctionnalité de facturation prenant uniquement en charge la facturation de l’utilisation. Il peut être configuré en fonction du contrat de vente à l’aide des API décrites dans la documentation. Cette fonction est activée par défaut. Pour désactiver cette fonctionnalité, reportez-vous à l’exemple du lecteur de référence.
   * **Amélioration de la prise en charge du basculement -** Des stratégies supplémentaires ont été mises en oeuvre pour poursuivre la lecture ininterrompue, en dépit des échecs des serveurs d’hôtes, des fichiers de liste de lecture et des segments.

* **Publicité**

   * **Intégration de Moat -** Prise en charge de la mesure de la visibilité publicitaire de la souris.
   * **Bannières d’accompagnement -** Les bannières d’accompagnement s’affichent à côté d’une publicité linéaire et continuent souvent d’être affichées sur l’affichage après la fin de la publicité. Ces bannières peuvent être de type html (fragment de code de HTML) ou iframe (URL vers une page iframe).

* **Analytics**

   * **VHL 2.0 -** Il s’agit de la dernière intégration optimisée de la bibliothèque Video Heartbeats (VHL) pour la collecte automatique des données d’utilisation d’Adobe Analytics. La complexité des API a été réduite pour faciliter l’implémentation. Téléchargement de la bibliothèque VHL [v2.0.0 pour Android™](https://github.com/Adobe-Marketing-Cloud/media-sdks/releases) et extrayez le fichier JAR dans le dossier libs .

* **SizeAvaliableEventListener**
   * Les méthodes getHeight() et getWidth() de SizeAvailableEvent renvoient désormais respectivement la sortie en hauteur et en largeur. Le format d’affichage peut être calculé comme suit :

      ```
      SizeAvailableEvent e;
      
      DAR = e.getWidth()/ e.getHeight();
      
      Storage Aspect Ratio in terms of Sar width and Sar height can also be used to calculate Frame width and Frame height:
      
      SAR = e.getSarWidth()/e.getSarHeight();
      
      frameHeight = e.getHeight();
      
      frameWidth = e.getWidth()/SAR;    
      ```

* **Cookies**

   * Android™ TVSDK prend désormais en charge l’accès aux cookies Java™ stockés dans CookieStore de l’application Android™. Une API de rappel (onCookiesUpdated) est fournie pour être enregistrée chaque fois qu’un nouveau cookie fait partie de l’en-tête de réponse &quot;Set-Cookie&quot;. Ces cookies sont disponibles sous la forme d’une liste de cookies HttpCookie utilisés pour un URI/domaine différent en définissant ces valeurs de cookies sur cet URI/domaine particulier à l’aide de CookieStore. De même, les valeurs des cookies dans TVSDK sont mises à jour à l’aide de l’API d’ajout de CookieStore.

## Matrice de fonctionnalités {#feature-matrix}

TVSDK pour Android™ prend en charge différentes fonctionnalités que vous pouvez mettre en oeuvre pour ajouter des fonctionnalités à vos applications vidéo.

Dans les tableaux de fonctionnalités ci-dessous, un &quot;Y&quot; indique que la fonctionnalité est prise en charge dans la version actuelle.

| Fonctionnalité | Type de contenu | HLS |
|---|---|---|
| Lecture générale (Lecture, Pause, Recherche) | VOD + En direct | Y |
| FER - Lecture générale (Lecture, Pause, Recherche) | FER VOD | Y |
| Rechercher quand une publicité est en cours de lecture | VOD + En direct | Non pris en charge |
| AC3 | VOD + En direct | Non pris en charge |
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
| Lecture audio seule | VOD + En direct | Y |
| Lecture de la carte | VOD + En direct | Y |
| Mouvement lent dans la lecture de la vidéo | VOD + En direct | Non pris en charge |
| Lecture lisser de la marque (avec ABR) | VOD + En direct | Y |
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

| Fonctionnalité | Type de contenu | HLS |
|---|---|---|
| Chiffrement AES | VOD + En direct | Y |
| Exemple de chiffrement AES | VOD + En direct | Y |
| Flux Tokenized | VOD + En direct | Y |
| DRM | VOD + En direct | Primetime DRM uniquement (Future : Widevine) |
| Lecture externe (RBOP) | VOD + En direct | Primetime DRM uniquement |
| Rotation de licence | VOD + En direct | Primetime DRM uniquement |
| Rotation des clés | VOD + En direct | Primetime DRM uniquement |

| Fonctionnalité | Type de contenu | HLS |
|---|---|---|
| Intégration d’Adobe Analytics VHL | VOD + En direct | Y |
| Facturation | VOD + En direct | Y |

## Problèmes résolus {#resolved-issues}

Lorsque la résolution est associée à un problème signalé, une référence Zendesk s’affiche, par exemple ZD#xxxxx

**Android™ TVSDK 2.7**

Cette section présente un résumé du problème résolu dans la version 2.7 de TVSDK.

* ZD#37166 - L’appel de suivi des erreurs est déclenché même lorsque la publicité est lue correctement.
* ZD#37134 - Les identifiants de publicité incorrects sont renvoyés, au cas où la publicité wrapper(3P) serait présente avec plusieurs publicités dans la réponse VMAP.

**Android™ TVSDK 2.5.6**

* ZD #34992 - La langue est vide dans le sous-titrage codé.
   * Correction d’un cas où TVSDK n’analysait pas #EXT-X-MEDIA:TYPE=CLOSED-CAPTIONS du manifeste principal pour obtenir les détails du suivi de la légende.
* ZD #35078 - Validation de P Android.
   * TVSDK 2.5.6 a été validé avec les dernières versions bêta d’Android™ P. Aucun problème n’a été détecté en raison du nouveau système d’exploitation Android™.
* ZD #34149 - Le lecteur continue à demander des manifestes même si une erreur se produit.
   * Correction du cas où TVSDK effectuait des appels répétitifs même lorsque tous les profils étaient en panne (erreur 404).
* ZD #31533 - Lecture audio sur Android™ après l’envoi de l’application en arrière-plan.
   * Ajout `enableAudioPlaybackInBackground` API de MediaPlayer qui doit être appelée avec &quot;True&quot; en tant qu’argument (lorsque le lecteur est à l’état PRÉPARÉ) pour activer la lecture du contenu audio lorsque l’application est en arrière-plan.

**Android™ TVSDK 2.5.5**

* ZD #21647 - Android TVSDK avertit 640x368 lorsque la taille réelle de la vidéo est de 640x360.
   * En raison de la variable m_nOutputHeight (dans AndroidMCVideoDecoder) mise à jour avec la hauteur d’image au lieu de la hauteur de sortie réelle. Apport de modifications appropriées dans la fonction getVideoFrame pour calculer correctement m_nOutputHeight.
* ZD #26614 - Urgent — service publicitaire tiers/programmatique — échec de diffusion d’impressions.
   * Amélioration de la correction précédente en gérant le cas dans l’analyse XML où le problème était reproductible lorsque &quot;espace&quot; est avant le signe &quot;égal&quot; comme &lt;vast version=&quot;2.0&quot;>
* ZD #29296 - Android : Ajoutez AdSystem et Creative ID aux requêtes CRS.
   * Incluez désormais &quot;AdSystem&quot; et &quot;CreativeId&quot; comme nouveaux paramètres dans les requêtes 1401 et 1403.
* ZD #33062 - TVSDK se bloque sur l’occurrence de barre verticale dans la réponse VAST sous le noeud CDATA
   * La classe API setEncodeUrlForTracking dans NetworkConfiguration a été supprimée en tant que caractères non sûrs dans une URL à coder.
* ZD #33063 - La logique de sélection des fichiers CRS a été rompue - TVSDK n’envoyait pas de demande CRS pour le format webm, mais plutôt pour les fichiers 3gpp.
   * Correction de la logique maintenant. Lors de l’utilisation de fichiers multimédias au format webm et 3gpp, une demande CRS doit être envoyée pour le web. En outre, lorsque vous utilisez les deux fichiers multimédias au format 3gpp, la demande CRS doit être envoyée pour le fichier 3gpp à débit le plus élevé.
* ZD #33125 - L’application Android se bloque avec une balise DoubleClick spécifique dans le VMAP.
   * Correction du scénario pour éviter le blocage.
* ZD #32256 - License Rotation &amp; Key Rotation Problème - Accès Adobe.
   * Correction de l’initialisation des segments avec les métadonnées DRM pour le contenu SampleAES. Fonctionne correctement avec le contenu AES128.
* ZD #33619 - Transfert rapide d’un contenu de liste de lecture en augmentation bloqué à l’état de mise en mémoire tampon près d’un point de vie.
   * Traitement du cas lors du passage du point d’entrée en mode de lecture par astuces.
* ZD #34151 - Objets TimedMetadata dans l’ordre.
   * Deux événements TimedMetadata s’affichaient dans un ordre aléatoire s’ils se trouvaient au même moment dans la chronologie. Maintien de leur ordre d’origine dans le manifeste.
* ZD #34189 - Problème lors de la recherche d’un début de coupure publicitaire.
   * Le problème était avec les publicités SSAI assemblées à l&#39;aide de discontinuité. Et la cause était un comportement quand nous cherchons au début de telles publicités, que nous recherchons une image clé et que nous ne la trouvons pas. La raison en était que l’horodatage audio principal de la publicité était avant l’horodatage vidéo principal. Par conséquent, nous finissons par rechercher une image clé à une mauvaise donnée fragmentDump. Corrigé maintenant.
* ZD #34528 - Résolution de la vidéo ne se mettant pas à niveau au-delà de 640x360 sur le dongle 3G FireTV.
   * Amélioration du correctif pour inclure les dernières mises à jour du micrologiciel.
* ZD #34793 - TVSDK 2.5.x se bloquait avec le résolveur de contenu personnalisé parfois lorsque VideoEngine supposait que les paramètres de Auditude sont disponibles et qu’ils ne l’étaient pas.
   * Le blocage se produisait en raison d’un appel de fonction sur un pointeur partagé Null (auditudeSettings). Ajout d’une vérification conditionnelle dans VideoEngineTimeline::placeToSourceTimeline() pour s’assurer que auditudeSettings est disponible avant d’appeler quoi que ce soit sur cet objet.
* ZD #32584 - Impossible d’accéder aux informations complètes présentes dans le &lt;extensions> noeud d’une réponse VAST.
   * Correction d’un problème lié à l’analyse XML. Désormais, NetworkAdInfo fournit les informations complètes présentes dans la variable &lt;extensions> noeud .
* ZD #35086 - Impossible d’obtenir des données d’extension complètes à partir du lecteur s’il existe des réponses VMAP spécifiques.
   * Le problème était spécifique au xml d’extension car l’analyse XML ne fonctionnait pas si le xml d’extension contenait des guillemets doubles dans la valeur d’attribut. Correction du problème.

**Android™ TVSDK 2.5.4**

* ZenDesk#33659 - Session de lecture permettant le débogage à distance de l’affichage Web.
   * WebViewDebbuging est défini sur False par défaut. Pour activer le débogage, définissez sur true via l’application, à l’aide de setWebContentsDebuggingEnabled(true).
* ZenDesk#33011 - La chronologie de la publicité n’est pas résolue en cas d’échec de la requête CRS.
   * Lorsqu’une requête CRS envoyée à une publicité échoue, la chronologie est résolue et les publicités restantes sont lues.
* ZenDesk#34528 - La résolution vidéo n’est pas mise à niveau au-delà de 640x360 sur le dongle de troisième génération de FireTV.
   * La résolution vidéo bascule en tant que débit binaire.
* ZenDesk#33192 - AudioTrack possède un nom null lorsque track est récupéré via AudioUpdatedEventListener::onAudioUpdated.
   * Dans certains scénarios sur une étiquette FireTV, l’événement onAudioUpdate était déclenché lorsqu’il n’y avait aucune mise à jour audio réelle. Ce problème a été corrigé maintenant.

**Android™ TVSDK 2.5.3**

* Zendesk#32216 - L’abonnement à la balise personnalisée TimedMetadata ne fonctionne pas.
   * Nous renvoyons les données ID3 sous la forme d’un tableau d’octets (pour prendre en charge les données APIC ou génériques) au client, alors que dans la version 1.4, nous renvoyons une chaîne. Le tableau d’octets ne gère pas le caractère terminé nul lui-même. Par conséquent, il présentait un caractère spécial au client. Ce problème est maintenant résolu.
* Zendesk#32670 - Le lecteur ne tombe pas sur la liste de lecture redondante
   * Cela fonctionne correctement maintenant et setNetworkDownVerificationUrl fonctionne comme prévu.
* Zendesk#32369 - La légende fermée affiche différentes couleurs d’ordures ou d’artefact.
   * Correction d’un problème lié aux problèmes CC dans le dernier build.
* Zendesk#25590 - Amélioration : Boutique de cookies TVSDK (C++ vers Java™)
   * Android™ TVSDK prend désormais en charge l’accès aux cookies entre la couche Java™ (stockée dans CookieStore de l’application Android™) et la couche C++ TVSDK.
* Zendesk#32252 - TVSDK_Android_2.5.2.12 ne semble pas avoir le correctif pour PTPLAY-20269 Ce problème a été corrigé et intégré à la branche 2.5.2.
* Zendesk#31806 - Les maquettes Auditude dans PRÉPARATION DU lecteur étaient bloquées à l’état Préparation car le fichier xml de réponse avait une balise vide. Le problème est maintenant résolu.
* Zendesk#31727 - Les caractères de sous-titres non intégrés TVSDK 2.5 sont ignorés ou mal orthographiés.
   * Le problème est résolu et nous ne perdons aucun caractère pour l’orthographe.
* Zendesk#31485 - DrmManager dans 2.5
   * Un problème s’est produit lors de la création de DrmManager via un nouveau DrmManager (contexte contextuel). Mise en oeuvre de la classe DRMService qui fournissait DRMManager.
* Zendesk#32794 - Flux de résolution 1080P non lu sur Android™.
   * Nous avons modifié SizeAvailableEvent. Auparavant, `getHeight()` et `getWidth()` Les méthodes de SizeAvailableEvent dans la version 2.5 sont utilisées pour renvoyer la hauteur de l’image et la largeur de l’image, qui a été renvoyée par le format multimédia. Elle renvoie désormais la hauteur de sortie et la largeur de sortie respectivement renvoyées par le décodeur.
* Le Flash Player Zendesk #19359 se bloque en raison de la position de l’attribut #EXT-X-FAXS-CM dans le manifeste de niveau défini.
   * La balise #EXT-X-FAXS-CM doit toujours apparaître sur la liste de lecture supérieure avant que chaque débit ou segment n’apparaisse dans la liste de lecture.

**Android™ TVSDK 2.5.2**

* Zendesk#17305 Artefacts dans des sous-titres non opaques en arrière-plan.
La propriété setTextSpaceAsAlphaNum dans TextFormat est exposée. Par défaut, la propriété est False. Définissez la propriété sur True dans un client pour résoudre le problème d’espace sombre.

* L&#39;affichage Zendesk#25097 CC contient des artefacts visuels avec les paramètres CC.
La propriété setTextSpaceAsAlphaNum dans TextFormat est exposée. Par défaut, la propriété est False. Définissez la propriété sur True dans un client pour résoudre le problème d’espace sombre.

* Zendesk #31620 La chaîne de l’agent utilisateur sortant du lecteur TVSDK est tronquée.
La chaîne de l’agent utilisateur ne sera plus tronquée après 128 caractères.
La chaîne de version Adobe Primetime est ajoutée à l’agent utilisateur système.

* Zendesk #30809 L’événement SEEK_END manquant empêche l’application de passer à un état de lecture.
* La couleur &quot;cyan&quot; du sous-titrage codé Zendesk #30415 est désormais une nuance plus sombre de bleu (turquoise), par rapport aux versions précédentes de TVSDK Primetime.

   La couleur passe de DarkCyan à Cyan.

* Zendesk #30727 Les publicités VOD ne sont pas téléchargées/résolues.

   Dans VMAP XML s’il existe une balise VAST vide sans balise de fermeture explicite (&lt;/vast>&quot;) et sans caractère de saut de ligne après, le code XML VMAP n’est pas correctement analysé et les publicités peuvent ne pas être lues.

**Android™ TVSDK 2.5.1**

* Crash spécifique à l’appareil (Samsung Galaxy Tab 4) ; VOD DRM LBA avec Auditude et cliquez sur les publicités.
* VHL - Des appels de pulsation incorrects sont envoyés lors du démarrage du contenu à partir d’un décalage.
* Lors de la lecture des publicités VPAID, les appels de pulsation VHL pour l’événement:type:la publicité de lecture est manquante.
* Après être passé à l’état COMPLETE, le lecteur revient à l’état LECTURE avec SKIP adBreakPolicy pour les publicités preroll.
* Les cookies ne sont pas associés aux rappels publicitaires sortants.
* Les repères de publicités ne sont pas visibles.
* HLS avec une piste SAP EAC3 distincte ne se charge pas.
* Le lecteur se bloque lorsque TVSDK reçoit l’intention d’écran activé une fois le lecteur multimédia restauré.

## Problèmes connus et limites {#known-issues-and-limitations}

**Android™ TVSDK 2.7**

* TVSDK 2.7 prend en charge la résolution simultanée de cinq publicités au maximum.
* Dans le cas d’une réponse VMAP, les appels de publicité s’effectuent simultanément en une seule coupure publicitaire et les coupures publicitaires sont résolues de manière séquentielle.
* Dans le cas d’un FER, les appels publicitaires dans chaque opportunité sont résolus simultanément.

### Problèmes connus et limites des versions précédentes{#known-issues-limitations-previous-releases}

**Android™ TVSDK 2.5.6**

* Plusieurs coupures publicitaires VMAP en même temps ne sont pas prises en charge.

**Android™ TVSDK 2.5.3**

Cette version présente les problèmes suivants :

* La lecture vidéo en direct peut présenter des problèmes de synchronisation audio-vidéo sur les appareils bas de gamme ou des conditions réseau médiocres.
* Pour les flux FER, virtualTime et localTime peuvent différer. En outre, FER avec décalage ne fonctionne pas.
* La lecture peut être bloquée lorsque la recherche porte sur les contenus audio de liaison tardive.
* Par intermittence, les sous-titres webVTT peuvent devenir désynchronisés pour le contenu LIVE.
* Par intermittence, la lecture rapide de quelques images peut être vue après la sortie d’une coupure publicitaire.
* Parfois, une erreur 303 est générée pour les coupures publicitaires du triple wrapper, même si des publicités sont lues.

**Android™ TVSDK 2.5.2**

Cette version présente les problèmes suivants :

* La lecture vidéo en direct peut présenter des problèmes de synchronisation audio-vidéo sur les appareils bas de gamme.
* La lecture peut parfois être bloquée lors de la recherche vers la fin du média VOD.
* Pour les flux FER, virtualTime et localTime peuvent différer. En outre, FER avec décalage ne fonctionne pas.

**Android™ TVSDK 2.5.1**

Cette version de TVSDK présente les problèmes suivants :

* La lecture vidéo en direct peut présenter des problèmes de synchronisation audio-vidéo sur les appareils bas de gamme.
* Pour les flux FER, virtualTime et localTime peuvent différer. En outre, FER avec décalage ne fonctionne pas.
* Dans VMAP XML, s’il existe une balise VAST vide sans balise de fermeture explicite (&lt;/vast>), et sans nouvelle ligne après, le code XML VMAP n’est pas analysé correctement et les publicités peuvent ne pas être lues.
* Les opérations post-roll VPAID ne sont pas prises en charge.

## Ressources utiles {#helpful-resources}

* [Configuration requise](https://experienceleague.adobe.com/docs/primetime/programming/tvsdk-2-7-for-android/overview/c-psdk-android-2.7-requirements.html?lang=en)
* [Guide du programmeur TVSDK 2.7 pour Android™](https://experienceleague.adobe.com/docs/primetime/programming/tvsdk-2-7-for-android/overview/c-psdk-android-2.7-overview-prod-audience-guide.html?lang=en)
* [TVSDK Android™ Javadoc pour référence d’API](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.7/index.html)
* [Document API TVSDK Android™ C++](https://help.adobe.com/en_US/primetime/api/psdk/cpp/namespaces.html) - Chaque classe Java™ possède une classe C++ correspondante et la documentation C++ contient plus de documents explicatifs que la documentation Java™. Reportez-vous donc à la documentation C++ pour une meilleure compréhension de l’API Java™.
* [Guide de migration de TVSDK 1.4 vers 2.5 pour Android™ (Java™)](https://experienceleague.adobe.com/docs/primetime/migration/tvsdk-14-25-android.html?lang=en)
* Pour gérer les scénarios d’activation/de désactivation d’écran, reportez-vous à la section `Application_Changes_for_Screen_On_Off.pdf` inclus dans la version.
* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://experienceleague.adobe.com/docs/primetime.html) page.
