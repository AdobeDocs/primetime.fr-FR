---
title: Notes de mise à jour de TVSDK 2.4.1 pour Android
seo-title: Notes de mise à jour de TVSDK 2.4.1 pour Android
description: Les Notes de mise à jour de TVSDK 2.4.1 pour Android décrivent les nouvelles fonctionnalités et les fonctionnalités prises en charge, ainsi que les problèmes connus et les limitations de TVSDK Android 2.4.1.
seo-description: Les Notes de mise à jour de TVSDK 2.4.1 pour Android décrivent les nouvelles fonctionnalités et les fonctionnalités prises en charge, ainsi que les problèmes connus et les limitations de TVSDK Android 2.4.1.
uuid: 929fc577-e851-4e03-9201-13280cc6137a
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: a6dbcc4a-9e14-4452-9004-b39ed13fad6f
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Notes de mise à jour de TVSDK 2.4.1 pour Android {#tvsdk-for-android-release-notes}

Les Notes de mise à jour de TVSDK 2.4.1 pour Android décrivent les nouvelles fonctionnalités et les fonctionnalités prises en charge, ainsi que les problèmes connus et les limitations de TVSDK Android 2.4.1.

## TVSDK Android 2.4.1 {#tvsdk-android}

Adobe publie TVSDK 2.4.1 pour Android.

Pour utiliser cette version de TVSDK, assurez-vous que votre système est conforme aux exigences décrites à la section Configuration requise [pour le](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_2.5.pdf#page=6)système.

Vous trouverez ici la documentation :

・ Système d&#39;aide en ligne TVSDK 2.4 pour l&#39;aide Android

・ [Javadocs TVSDK 2.4 pour l’API Java Android](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/index.html)

Les Javadocs sont l’autorité ultime, car ils sont automatiquement générés directement à partir du code source TVSDK.

・ Documentation de l’API [C++ TVSDK 2.4 pour l’API C++ Android](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.4/namespaces.html)

Chaque classe Java possède une classe C++ correspondante, et la documentation C++ contient plus d’explications que les Javadocs. Consultez donc la documentation C++ pour en savoir plus sur l’API Java.

・ Guide de migration (Guide[de migration](../migration-guides/tvsdk-14-25-android.md)TVSDK 2.4 pour Android Migration Guide)

Ce guide explique ce que vous devez modifier pour migrer une application basée sur TVSDK 1.4 vers une application basée sur TVSDK 2.4.

## Nouvelles fonctionnalités {#new-features}

TVSDK 2.4.1 pour Android offre de nombreuses améliorations de performances par rapport aux versions antérieures. Il offre une expérience d’affichage de haute qualité.

Cette version comprend toutes les fonctionnalités des versions 2.4 et 2.4.1 et aucune fonctionnalité n’est obsolète.

Voici les principales nouvelles fonctionnalités de la version 2.4.1 :

* Fonctionnalités HLS version 4

   * **Lecture** vidéo (lecture, pause, recherche) avec contrôle du lecteur pour les flux en direct, linéaires et VOD.
   * **Sous-titrage.** TVSDK peut afficher des sous-titres 608/708 avec une sélection de polices, tailles de police, couleurs et arrière-plan. Il peut également prendre en charge les vidéos avec des légendes de cumul et basculer entre les pistes de langue si elles sont disponibles.
   * **Le mode** de lecture en mode Trick Play prend en charge l’avance rapide et le retour en arrière pour les flux HLS qui utilisent des I-Frames. Toutes les commandes de lecture vidéo fonctionnent sur le contenu. Le mouvement lent (vers l’avant) est disponible pour le mode de lecture vidéo externe avec des vitesses comprises entre 0 et 1.
   * **Le débit adaptatif (ABR)** permet au lecteur de sélectionner dynamiquement l’une des versions multiples du même flux de contenu à lire, en fonction du réseau et d’autres conditions. Vous pouvez définir des paramètres de manière dynamique ou dans le fichier manifeste pour effectuer une sélection parmi des stratégies de sélection agressives, modérées et conservatrices.
   * **Les plages** d’octets permettent à un seul fichier TS de contenir plusieurs segments TS.
   * **Les rendus** audio alternatifs permettent au lecteur de basculer entre les pistes audio disponibles.
   * **Prise en charge d’ID3.** TVSDK peut lire des flux audio et vidéo HLS contenant des métadonnées audio ID3, telles que le nom de l’artiste, le titre et l’album.
   * **Basculement. **TVSDK utilise des stratégies pour poursuivre la lecture ininterrompue, malgré les défaillances des serveurs hôtes, des fichiers de liste de lecture et des segments.
   * **Transmission audio  à plusieurs (DD+).** TVSDK peut transmettre les données audio Dolby Digital Plus (E-AC3) au matériel de prise en charge.

* Fonctionnalités de protection du contenu

   * **DRM pour HLS.** Toutes les API de lecture vidéo fonctionnent avec du contenu vidéo chiffré protégé par Adobe Access. Les fonctionnalités DRM suivantes sont prises en charge :

      * Rotation des licences
      * Rotation clé
      * Mise en cache des licences
      * Heure de la stratégie
      * Rotation IV

* **Lecture AES 128.** TVSDK peut lire le contenu HLS standard de chiffrement avancé (AES) avec une taille de clé de 128 bits.
* **Le protocole PHLS (Protected HLS)** fournit un ensemble limité de stratégies DRM prédéfinies, un sous-ensemble de ce qu’Adobe Access fournit, pour permettre la gestion des droits numériques légers sur HLS pour les flux en direct et VOD.

* Fonctionnalités de publicité/d’alternance de contenu et de monétisation

   * **Suivi des publicités insérées côté serveur.** TVSDK peut effectuer le suivi des publicités insérées par le service d’insertion de publicités Adobe Cloud. Il prend en charge les publicités linéaires aux formats VAST2, VAST3 et VMAP pour les flux VOD et les flux en direct/linéaires.
   * **Balises HLS personnalisées.** TVSDK utilise sa `MediaPlayerConfig` classe pour activer la notification au lecteur lorsque des balises HLS personnalisées apparaissent dans le flux.
   * **Insertion de publicité côté client.** La bibliothèque d’insertion d’annonces Auditude fonctionne avec les serveurs Adobe Auditude pour résoudre les publicités en vue de les insérer dynamiquement dans du contenu en direct, linéaire et VOD, aux positions preroll, mid-roll ou post-roll.
   * **Résolveurs publicitaires personnalisés.** Les interfaces `ContentResolver, OpportunityGenerator,` et `MediaPlayerClientFactory` permettent de mettre en oeuvre un programme de résolution de publicités/de contenu alternatif personnalisé et d’enregistrer un détecteur d’opportunités personnalisé pour travailler avec TVSDK. Les `TestAdResolver` classes et `AuditudeResolver` fournissent des exemples C++ d’implémentation d’un résolveur de contenu. Vous trouverez un exemple JavaScript à l’adresse `samples/jspsdk/testapp/psdk.js`.
   * **Comportement cohérent des publicités.** Utilisez l’ `AdPolicySelector` interface pour activer un comportement cohérent sur tous les lecteurs pour des opérations telles que la recherche et le jeu vidéo lorsque des publicités sont présentes dans le contenu. Si vous n’implémentez pas les vôtres, TVSDK les utilise `DefaultAdPolicySelector`.
   * **Supprimez/remplacez les publicités C3.** Utilisez l’API TVSDK appropriée pour supprimer des plages de contenu personnalisées et insérer dynamiquement de nouvelles publicités sans aucune préparation supplémentaire. C&#39;est pratique lorsque du contenu en direct/linéaire est diffusé, puis immédiatement disponible à la demande sans nettoyage.

Voici les principales nouvelles fonctionnalités de la version 2.4 :

* **Instant on for VOD and live** Lorsque vous activez l’activation instantanée, TVSDK initialise et met en mémoire tampon le média avant le  de lecture. Comme vous pouvez lancer plusieurs `MediaPlayerItemLoader` instances simultanément en arrière-plan, vous pouvez mettre en mémoire tampon plusieurs flux. Lorsqu’un utilisateur modifie le  du et que le flux a été mis en mémoire tampon correctement, la lecture sur le nouvel  de  immédiatement. TVSDK 2.4 prend également en charge Instant On pour les flux en direct. Les flux en direct sont remis en mémoire tampon lorsque la fenêtre active se déplace.

* **Améliorations des performances **La nouvelle architecture TVSDK 2.4 apporte diverses améliorations des performances :

   * **Sous-segmentation** - Le kit TVSDK réduit encore davantage la taille de chaque fragment pour qu’il soit lu  le plus tôt possible.
   * **Téléchargements** de publicités parallèles : TVSDK prérécupère les publicités en parallèle à la lecture du contenu avant d’atteindre les coupures publicitaires, ce qui permet une lecture transparente des publicités et du contenu.
   * **Résolution** des publicités irrégulières - Avec cette fonctionnalité, nous n&#39;attendons pas la résolution des publicités non preroll avant de commencer la lecture, ce qui réduit le temps de démarrage. Les API telles que la recherche et le jeu vidéo ne sont toujours pas autorisées tant que toutes les publicités ne sont pas résolues.

* **Lecture de contenu MP4**

Cette version de TVSDK prend en charge la lecture de MP4 en tant que contenu principal.

* **Connexions réseau persistantes**

TVSDK conserve un ensemble de connexions réseau réutilisables, de sorte qu’il n’est pas nécessaire de créer et de détruire une connexion réseau pour chaque demande de réseau.

* **Protection de la sortie basée sur la résolution**

Cette fonctionnalité associe les restrictions de lecture à des résolutions spécifiques, fournissant des commandes DRM plus fines.

* **Lecture avec débit binaire adaptatif (ABR)**

Cette fonctionnalité permet à TVSDK de basculer entre les flux iFrame en mode de lecture par astuce. Vous pouvez utiliser des non iFrame pour jouer à des vitesses de lecture inférieures.

* **Lissage du jeu**

Ces améliorations améliorent l’expérience des utilisateurs :

・ Sélection adaptative de la vitesse de transmission et de la fréquence d’images pendant la lecture de l’astuce, en fonction de la bande passante et des  de mémoire tampon

・ Utilisez le flux principal plutôt que le flux IDR pour obtenir une lecture rapide jusqu’à 30 i/s.

* **Logique ABR améliorée**

La nouvelle logique ABR est basée sur la longueur de la mémoire tampon, le taux de changement de la longueur de la mémoire tampon et la bande passante mesurée. Ainsi, l’ABR choisit le débit approprié lorsque la bande passante fluctue et optimise le nombre de fois où le commutateur de débit se produit réellement en surveillant le débit auquel la longueur de la mémoire tampon change.

* **Facturation**

TVSDK collecte automatiquement les mesures, en respectant le contrat de vente du client afin de générer des rapports d’utilisation périodiques requis pour la facturation. Sur chaque de flux  , TVSDK utilise l’API d’insertion de données Adobe Analytics pour envoyer des mesures de facturation telles que le type de contenu, les indicateurs activés pour l’insertion de publicités et les indicateurs activés pour l’insertion de données drm - en fonction de la durée du flux facturable - à la suite de rapports d’Adobe Analytics Primetime. Cela n’interfère pas avec les suites de rapports Adobe Analytics ou les appels au serveur du client ou ne les inclut pas. Sur demande, ce rapport sur l’utilisation de la facturation est envoyé régulièrement aux clients. Il s’agit de la première phase de la fonction de facturation qui prend uniquement en charge la facturation d’utilisation. Il peut être configuré en fonction du contrat de vente à l’aide des API décrites dans la documentation.

## Fonctionnalités prises en charge {#supported-features}

TVSDK pour Android 2.4 prend en charge un certain nombre de fonctionnalités que vous pouvez implémenter pour ajouter des fonctionnalités à vos applications vidéo.

>[!NOTE]
>
>Dans les tableaux de la matrice des fonctionnalités ci-dessous, un √ signifie que la fonctionnalité est prise en charge dans la version actuelle.

### Fonctions de lecture principales {#core-playback-features}

| **Fonctionnalité** | **Type de contenu** | **HLS** | **DASH** |
|---|---|---|---|
| Lecture générale (Lecture, Pause, Recherche) | VOD + Live | √ | √ (VOD uniquement) |
| FER - Lecture générale (Lecture, Pause, Recherche) | FER VOD | √ | Non pris en charge |
| MP3 | VOD | Non pris en charge | Non pris en charge |
| Lecture de contenu MP4 | VOD | √ | √ |
| Logique de commutation de débit adaptatif | VOD + Live | √ | Non pris en charge |
| Lecture audio uniquement | VOD + Live | √ | Non pris en charge |
| Sous-titres - 608/708 | VOD + Live | √ | √ (VOD uniquement) |
| Sous-titres - WebVTT | VOD + Live | √ | √ (VOD uniquement) |
| Basculement du manifeste | VOD + Live | √ | √ (VOD uniquement) |
| Basculement avancé | VOD + Live | √ | √ (VOD uniquement) |
| Notifications QoS et du lecteur | VOD + Live | √ | √ (VOD uniquement) |
| Prise en charge des en-têtes de cookie | VOD + Live | √ | √ (VOD uniquement) |
| Prise en charge des en-têtes personnalisés | VOD + Live | Non pris en charge | Non pris en charge |
| Définition des paramètres de contrôle de la mémoire tampon | VOD + Live | √ | √ (VOD uniquement) |
| Définition des contrôles de débit binaire adaptatif | VOD + Live | √ | √ (VOD uniquement) |
| Balises de manifeste personnalisées (HLS) / Flux de  (DASH) | VOD + Live | √ | √ (VOD uniquement) |
| Audio lié tardif | VOD + Live | √ | √ (VOD uniquement) |
| 302 Redirection | VOD + Live | √ | √ (VOD uniquement) |

### Fonctions de lecture avancées {#advanced-playback-features}

<table> 
 <tbody>
  <tr>
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Type de contenu</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>DASH</strong></td> 
  </tr>
  <tr>
   <td>Lecture avec décalage</td> 
   <td>Live</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Lecture audio uniquement</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Lecture de Trick </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Lecture lisse (avec ABR)</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Analyse ID3 (HLS) / Métadonnées minutées (DASH)</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Blackouts </td> 
   <td>VOD + Live</td> 
   <td>Non pris en charge</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Instant activé</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Prise en charge des marqueurs de discontinuité (HLS) </li> 
     <li>Multipériode (DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>302 Attractions de redirection</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√ (VOD uniquement)</td> 
  </tr>
  <tr>
   <td>Défilement par vignettes (Iframe et JPEG)</td> 
   <td>VOD + Live</td> 
   <td>Non pris en charge</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Intégrité du flux </td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
 </tbody>
</table>

### Fonctions d’insertion d’annonces principales (CSAI) {#core-ad-insertion-features-csai}

| **Fonctionnalité** | **Type de contenu** | **HLS** | **DASH** |
|---|---|---|---|
| Lecture générale, publicités activées | VOD + Live | √ | √ (Préroulements VOD uniquement) |
| Contenu FER avec publicités activées | VOD | √ | Non pris en charge |
| Comportements publicitaires par défaut | VOD + Live | √ | √ (Préroulements VOD uniquement) |
| VAST 2.0/3.0 | VOD + Live | √ | √ (Préroulements VOD uniquement) |
| VMAP 1.0 | VOD + Live | √ | √ (Préroulements VOD uniquement) |
| Annonces MP4 | VOD + Live | √ (du CS Ex) | √ (à partir de CRS, pré-rouleaux uniquement) |

### Fonctionnalités avancées d&#39;insertion d&#39;annonce (CSAI) {#advanced-ad-insertion-features-csai}

<table> 
 <tbody>
  <tr>
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Type de contenu</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>DASH</strong></td> 
  </tr>
  <tr>
   <td>Lecture à l'aide de publicités activée</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Publicité uniquement </td> 
   <td>VOD</td> 
   <td>Non pris en charge</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Paramètres de ciblage</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√ (Préroulements VOD uniquement)</td> 
  </tr>
  <tr>
   <td>Paramètres personnalisés</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√ (Préroulements VOD uniquement)</td> 
  </tr>
  <tr>
   <td>Comportements publicitaires personnalisés</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√ (Préroulements VOD uniquement)</td> 
  </tr>
  <tr>
   <td>Balises publicitaires personnalisées</td> 
   <td>Live</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Résolveurs publicitaires personnalisés</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Résolveur d’annonce personnalisé à roue libre</td> 
   <td>VOD</td> 
   <td>Non pris en charge</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Remplacement de publicité C3 </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Chargement de publicités différé</td> 
   <td>VOD</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Prise en charge des marqueurs de discontinuité - SSAI (HLS) </li> 
     <li>Multipériode (DASH)</li> 
    </ul> </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicités d’accompagnement, bannières publicitaires et publicités cliquables</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>√ (Préroulements VOD uniquement)</td> 
  </tr>
  <tr>
   <td>VPAID 2.0</td> 
   <td>VOD + Live</td> 
   <td>√ (JS) </td> 
   <td>√ (Préroulements VOD uniquement)</td> 
  </tr>
  <tr>
   <td>Sortie de publicité anticipée</td> 
   <td>Live</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Création VOD basée sur des règles + hiérarchisation en direct</td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Règles CRS </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
 </tbody>
</table>

## Fonctionnalités de protection du contenu {#content-protection-features}

| **Fonctionnalité** | **Type de contenu** | **HLS** | **DASH** |
|---|---|---|---|
| Chiffrement AES | VOD + Live | √ | √ (VOD uniquement) |
| Exemple de chiffrement AES | VOD + Live | √ |  |
| Flux jetés | VOD + Live | √ |  |
| DRM | VOD + Live | Primetime DRM uniquement (Futur : Widevine) | Widevine uniquement |
| Lecture externe (RBOP) | VOD + Live | DRM Primetime uniquement | Non pris en charge |
| Rotation de licence | VOD + Live | DRM Primetime uniquement | Non pris en charge |
| Rotation clé | VOD + Live | DRM Primetime uniquement | Non pris en charge |

### Fonctions d’intégration {#integration-features}

| **Fonctionnalité** | **Type de contenu** | **HLS** | **DASH** |
|---|---|---|---|
| Intégration d’Adobe Analytics VHL | VOD + Live | √ | √ |
| Facturation | VOD + Live | √ | Non pris en charge |

## Fonctions non prises en charge {#features-not-supported}

Cette version de TVSDK ne prend pas en charge :

* Blocage des publicités.
* Le mouvement lent dans le jeu.
* Recherchez et jouez avec du contenu MP4.
* Insertion d’une publicité avec le contenu principal MP4.
* Recherchez quand une publicité est en cours de lecture.
* Lecture des publicités avec support audio uniquement.

## Problèmes et limites connus {#known-issues-and-limitations}

Cette version de TVSDK présente les problèmes suivants :

* Un blocage VOD DRM LBA avec auditude spécifique au périphérique (Samsung Galaxy Tab 4) et un clic sur les publicités
* La publicité post-roll n’est pas lue pour un contenu spécifique.
* La définition de la légende de fermeture en langues CJC ne fonctionne pas.
* La vidéo peut sortir du mode de la ruse automatiquement entre VOD et live.
* VHL - Les appels de pulsation erronés sont envoyés lorsque nous un contenu à partir d’un décalage.
* Lorsque des publicités VPAID sont lues, il manque des appels de pulsation VHL pour :type:play.
* La publicité preroll est lue même si adBreakPolicy SKIP est sélectionné.
* Une fois que vous êtes entré dans le lecteur d’état complet, vous revenez à l’état Lecture avec SKIP adBreakPolicy pour les publicités post-roll.

Sans vidéo, il n’y a pas de dimension de fenêtre d’affichage et sans dimension de fenêtre d’affichage, vous ne pouvez pas afficher de graphiques pour les légendes.

## Ressources utiles {#helpful-resources}

* Reportez-vous à la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.