---
title: Notes de mise à jour de TVSDK 2.4.1 pour Android
description: Les notes de mise à jour de TVSDK 2.4.1 pour Android décrivent les nouvelles fonctionnalités et les fonctionnalités prises en charge, ainsi que les problèmes et limitations connus de TVSDK Android 2.4.1.
topic-tags: release-notes
products: SG_PRIMETIME
exl-id: 3de09048-ae32-43b4-a019-34b217931a4c
source-git-commit: 3b051c3188c81673129e12dfeb573aaf85c15c97
workflow-type: tm+mt
source-wordcount: '1962'
ht-degree: 0%

---

# Notes de mise à jour de TVSDK 2.4.1 pour Android {#tvsdk-for-android-release-notes}

Les notes de mise à jour de TVSDK 2.4.1 pour Android décrivent les nouvelles fonctionnalités et les fonctionnalités prises en charge, ainsi que les problèmes et limitations connus de TVSDK Android 2.4.1.

## TVSDK Android 2.4.1 {#tvsdk-android}

Adobe publie TVSDK 2.4.1 pour Android.

Pour utiliser cette version de TVSDK, assurez-vous que votre système respecte la configuration requise décrite à la section [Configuration requise](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_2.5.pdf#page=6).

Vous trouverez la documentation suivante :

・ Aide du système d’aide en ligne TVSDK 2.4 pour Android

・ [Javadocs TVSDK 2.4 pour l’API Java Android](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/index.html)

Les Javadocs constituent l’autorité ultime, car ils sont générés automatiquement directement à partir du code source TVSDK.

・ [Documentation de l’API C++ TVSDK 2.4 pour l’API Android C++](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.4/namespaces.html)

Chaque classe Java possède une classe C++ correspondante et la documentation C++ contient plus de documents explicatifs que les Javadocs. Consultez donc la documentation C++ pour une meilleure compréhension de l’API Java.

・ Guide de migration ([Guide de migration de TVSDK 2.4 pour Android](../migration-guides/tvsdk-14-25-android.md))

Ce guide explique ce que vous devez modifier pour migrer une application basée sur TVSDK 1.4 vers une application basée sur TVSDK 2.4.

## Nouvelles fonctionnalités {#new-features}

TVSDK 2.4.1 pour Android offre de nombreuses améliorations de performances par rapport aux versions antérieures. Il offre une expérience de visionnage de haute qualité.

Cette version comprend toutes les fonctionnalités des versions 2.4 et 2.4.1 et aucune fonctionnalité n’est obsolète.

Voici les principales nouvelles fonctionnalités de la version 2.4.1 :

* Fonctionnalités HLS version 4

   * **Lecture vidéo** (lecture, pause, recherche) avec contrôle du lecteur pour les flux en direct, linéaires et VOD.
   * **Sous-titrage codé.** TVSDK peut afficher 608/708 sous-titres avec une sélection de polices, de tailles de police, de couleurs et d’arrière-plan. Il peut également prendre en charge les vidéos avec des sous-titres de cumul et passer d’un suivi de langue à l’autre s’ils sont disponibles.
   * **Mode de lecture des tropiques** prend en charge les flux HLS rapides en avant et en arrière qui utilisent des I-Frames. Toutes les commandes de lecture vidéo fonctionnent sur le contenu. Le mouvement lent (avant) est disponible pour le mode de lecture vidéo externe avec des taux compris entre 0 et 1.
   * **Débit adaptatif (ABR)** permet au lecteur de sélectionner dynamiquement la ou les versions multiples d’un même flux de contenu à lire, en fonction du réseau et d’autres conditions. Vous pouvez définir des paramètres dynamiquement ou dans le fichier de manifeste pour effectuer une sélection parmi des stratégies de sélection agressives, modérées et conservatrices.
   * **Périodes** Activez un seul fichier TS pour contenir plusieurs segments TS.
   * **Autres rendus audio** Permet au lecteur de basculer entre les pistes audio disponibles.
   * **Prise en charge d’ID3.** TVSDK peut lire des flux audio et vidéo HLS contenant des métadonnées audio ID3, telles que le nom de l’artiste, le titre et l’album.
   * **Basculement. **TVSDK utilise des stratégies pour poursuivre la lecture ininterrompue, en dépit des échecs des serveurs d’hôtes, des fichiers de liste de lecture et des segments.
   * **Diffusion audio multicanal (DD+).** TVSDK peut transmettre des données audio Dolby Digital Plus (E-AC3) au matériel de prise en charge.

* Fonctionnalités de protection du contenu

   * **DRM pour HLS.** Toutes les API de lecture vidéo fonctionnent avec du contenu vidéo chiffré protégé par Accès aux Adobes. Les fonctionnalités DRM suivantes sont prises en charge :

      * Rotation des licences
      * Rotation des clés
      * Mise en cache de licence
      * Durée de la stratégie
      * Rotation IV

* **Lecture AES 128.** TVSDK peut lire le contenu HLS standard de chiffrement avancé (AES) avec une taille de clé de 128 bits.
* **HLS protégé (PHLS)** fournit un ensemble limité de stratégies DRM préconfigurées, un sous-ensemble de ce qu’fournit Adobe Access, afin d’activer la DRM légère sur HLS pour les flux VOD et en direct.

* Fonctionnalités publicitaires/de contenu alternatif et de monétisation

   * **Suivi des publicités insérées côté serveur.** TVSDK peut effectuer le suivi des publicités insérées par le service d’insertion de publicités Adobe Cloud. Il prend en charge les publicités linéaires aux formats VAST2, VAST3 et VMAP pour les diffusions VOD et live/linear.
   * **Balises HLS personnalisées.** TVSDK utilise son `MediaPlayerConfig` pour activer la notification de l’application du lecteur lorsque des balises HLS personnalisées apparaissent dans le flux.
   * **Insertion de publicités côté client.** La bibliothèque d’insertion de publicités Auditude fonctionne avec les serveurs Adobe Auditude pour résoudre les publicités en vue d’une insertion dynamique dans du contenu dynamique, linéaire et VOD, aux positions preroll, mid-roll ou post-roll.
   * **Résolveurs de publicités personnalisés.** Le `ContentResolver, OpportunityGenerator,` et `MediaPlayerClientFactory` Les interfaces vous permettent de mettre en oeuvre un résolveur de contenu alternatif/publicité personnalisé et d’enregistrer un détecteur d’opportunités personnalisé pour travailler avec TVSDK. Le `TestAdResolver` et `AuditudeResolver` Les classes fournissent des exemples C++ d’implémentation d’un résolveur de contenu. Vous trouverez un exemple JavaScript à l’adresse `samples/jspsdk/testapp/psdk.js`.
   * **Comportement cohérent de la publicité.** Utilisez la variable `AdPolicySelector` pour permettre un comportement cohérent sur tous les lecteurs pour des opérations telles que la recherche et le jeu vidéo lorsque des publicités sont présentes dans le contenu. Si vous n’implémentez pas le vôtre, TVSDK utilise `DefaultAdPolicySelector`.
   * **Supprimez/remplacez des publicités C3.** Utilisez l’API TVSDK appropriée pour supprimer des plages de contenu personnalisées et insérer dynamiquement de nouvelles publicités sans préparation supplémentaire. Cela s’avère pratique lorsque le contenu en direct/linéaire est diffusé, puis rendu disponible immédiatement à la demande sans nettoyage.

Voici les principales nouvelles fonctionnalités de la version 2.4 :

* **Installez pour VOD et live** Lorsque vous activez l’instantané, TVSDK s’initialise et met en mémoire tampon le média avant le début de la lecture. Parce que vous pouvez lancer plusieurs `MediaPlayerItemLoader` instances simultanément en arrière-plan, vous pouvez mettre en mémoire tampon plusieurs diffusions. Lorsqu’un utilisateur modifie le canal et que la diffusion a été mise en mémoire tampon correctement, la lecture du nouveau canal commence immédiatement. TVSDK 2.4 prend également en charge Instant On pour les diffusions en direct. Les diffusions en direct sont mises en mémoire tampon à nouveau lorsque la fenêtre active se déplace.

* **Amélioration des performances **La nouvelle architecture de TVSDK 2.4 apporte diverses améliorations de performances :

   * **Sous-segmentation** - TVSDK réduit davantage la taille de chaque fragment afin de démarrer la lecture dès que possible.
   * **Téléchargements de publicités parallèles** - TVSDK récupère les publicités en parallèle de la lecture du contenu avant d’atteindre les coupures publicitaires, ce qui permet une lecture transparente des publicités et du contenu.
   * **Lazy ad resolution** - Avec cette fonctionnalité, nous n’attendons pas la résolution des publicités non preroll avant de commencer la lecture, ce qui réduit le temps de démarrage. Les API telles que la recherche et le jeu vidéo ne sont toujours pas autorisées tant que toutes les publicités ne sont pas résolues.

* **Lecture du contenu MP4**

Cette version de TVSDK prend en charge la lecture de MP4 en tant que contenu principal.

* **Connexions réseau persistantes**

TVSDK conserve un ensemble de connexions réseau réutilisables. Il n’entraîne donc pas de surcharge lors de la création et de la destruction d’une connexion réseau pour chaque demande de réseau.

* **Protection des sorties basée sur la résolution**

Cette fonctionnalité associe les restrictions de lecture à des résolutions spécifiques, fournissant des contrôles DRM plus précis.

* **Lecture de la vidéo avec débit adaptatif (ABR)**

Cette fonctionnalité permet à TVSDK de basculer entre les diffusions iFrame en mode de lecture de l’astuce. Vous pouvez utiliser des profils non iFrame pour effectuer des opérations de lecture à des vitesses inférieures.

* **Jeu de tour lisser**

Ces améliorations améliorent l’expérience utilisateur :

・ Sélection de débit binaire adaptatif et de débit d’image lors de la lecture de l’astuce, en fonction de la bande passante et du profil de mémoire tampon

・ Utilisez la diffusion principale au lieu de la diffusion IDR pour une lecture rapide jusqu’à 30 ips.

* **Amélioration de la logique ABR**

La nouvelle logique ABR repose sur la longueur de la mémoire tampon, le taux de changement de la longueur de la mémoire tampon et la bande passante mesurée. Ainsi, l’ABR choisit le débit approprié lorsque la bande passante fluctue et optimise le nombre de fois où le changement de débit se produit réellement en surveillant la vitesse à laquelle la longueur de la mémoire tampon change.

* **Facturation**

TVSDK collecte automatiquement les mesures, en conformité avec le contrat de vente client, afin de générer des rapports d’utilisation périodiques requis à des fins de facturation. Pour chaque événement de démarrage de flux, TVSDK utilise l’API d’insertion de données d’Adobe Analytics pour envoyer des mesures de facturation telles que le type de contenu, les indicateurs activés pour l’insertion de publicités et les indicateurs activés pour la collecte de données drm (selon la durée du flux facturable) à la suite de rapports détenue par Adobe Analytics Primetime. Cela n’interfère pas avec les suites de rapports Adobe Analytics ou les appels au serveur du client, ni ne les inclut dans celles-ci. Sur demande, ce rapport sur l’utilisation de la facturation est envoyé régulièrement aux clients. Il s’agit de la première phase de la fonctionnalité de facturation prenant uniquement en charge la facturation de l’utilisation. Il peut être configuré en fonction du contrat de vente à l’aide des API décrites dans la documentation.

## Fonctionnalités prises en charge {#supported-features}

TVSDK pour Android 2.4 prend en charge plusieurs fonctionnalités que vous pouvez mettre en oeuvre pour ajouter des fonctionnalités à vos applications vidéo.

>[!NOTE]
>
>Dans les tableaux de la matrice des fonctionnalités ci-dessous, un √ signifie que la fonctionnalité est prise en charge dans la version actuelle.

### Fonctions de lecture principales {#core-playback-features}

| **Fonctionnalité** | **Type de contenu** | **HLS** | **DASH** |
|---|---|---|---|
| Lecture générale (Lecture, Pause, Recherche) | VOD + En direct | √ | √ (VOD uniquement) |
| FER - Lecture générale (Lecture, Pause, Recherche) | FER VOD | √ | Non pris en charge |
| MP3 | VOD | Non pris en charge | Non pris en charge |
| Lecture de contenu MP4 | VOD | √ | √ |
| Logique de changement de débit adaptatif | VOD + En direct | √ | Non pris en charge |
| Lecture audio uniquement | VOD + En direct | √ | Non pris en charge |
| Sous-titres codés - 608/708 | VOD + En direct | √ | √ (VOD uniquement) |
| Sous-titres codés - WebVTT | VOD + En direct | √ | √ (VOD uniquement) |
| Basculement du manifeste | VOD + En direct | √ | √ (VOD uniquement) |
| Basculement avancé | VOD + En direct | √ | √ (VOD uniquement) |
| Notifications QoS et du lecteur | VOD + En direct | √ | √ (VOD uniquement) |
| Prise en charge des en-têtes de cookie | VOD + En direct | √ | √ (VOD uniquement) |
| Prise en charge des en-têtes personnalisés | VOD + En direct | Non pris en charge | Non pris en charge |
| Définition des paramètres de contrôle de la mémoire tampon | VOD + En direct | √ | √ (VOD uniquement) |
| Définition des contrôles de débit adaptatif | VOD + En direct | √ | √ (VOD uniquement) |
| Balises de manifeste personnalisées (HLS) / Flux d’événements (DASH) | VOD + En direct | √ | √ (VOD uniquement) |
| Audio liée tardive | VOD + En direct | √ | √ (VOD uniquement) |
| Redirection 302 | VOD + En direct | √ | √ (VOD uniquement) |

### Fonctionnalités de lecture avancées {#advanced-playback-features}

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
   <td>En direct</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Lecture audio uniquement</td> 
   <td>VOD + En direct</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Lecture de la carte </td> 
   <td>VOD + En direct</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Lecture lisser de la marque (avec ABR)</td> 
   <td>VOD + En direct</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Analyse ID3 (HLS) / Métadonnées temporelles (DASH)</td> 
   <td>VOD + En direct</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Noires </td> 
   <td>VOD + En direct</td> 
   <td>Non pris en charge</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Instant activé</td> 
   <td>VOD + En direct</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Prise en charge des marqueurs de discontinuité (HLS) </li> 
     <li>Multi-périodes (DASH)</li> 
    </ul> </td> 
   <td>VOD + En direct</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Attractivité de redirection 302</td> 
   <td>VOD + En direct</td> 
   <td>√</td> 
   <td>√ (VOD uniquement)</td> 
  </tr>
  <tr>
   <td>Défilement des miniatures (Iframe et JPEG)</td> 
   <td>VOD + En direct</td> 
   <td>Non pris en charge</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Intégrité des diffusions </td> 
   <td>VOD + En direct</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
 </tbody>
</table>

### Principales fonctionnalités de l’Ad Insertion (CSAI) {#core-ad-insertion-features-csai}

| **Fonctionnalité** | **Type de contenu** | **HLS** | **DASH** |
|---|---|---|---|
| Lecture générale, publicités activées | VOD + En direct | √ | √ (Pré-enregistrements VOD uniquement) |
| Contenu FER avec publicités activées | VOD | √ | Non pris en charge |
| Comportements de publicité par défaut | VOD + En direct | √ | √ (Pré-enregistrements VOD uniquement) |
| VAST 2.0/3.0 | VOD + En direct | √ | √ (Pré-enregistrements VOD uniquement) |
| VMAP 1.0 | VOD + En direct | √ | √ (Pré-enregistrements VOD uniquement) |
| Publicités MP4 | VOD + En direct | √ (provenant de CRS) | √ (provenant de CRS, pré-enregistrements uniquement) |

### Fonctionnalités Ad Insertion avancées (CSAI) {#advanced-ad-insertion-features-csai}

<table> 
 <tbody>
  <tr>
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Type de contenu</strong></td> 
   <td><strong>HLS</strong></td> 
   <td><strong>DASH</strong></td> 
  </tr>
  <tr>
   <td>Lecture de la carte avec publicités activées</td> 
   <td>VOD + En direct</td> 
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
   <td>VOD + En direct</td> 
   <td>√</td> 
   <td>√ (Pré-enregistrements VOD uniquement)</td> 
  </tr>
  <tr>
   <td>Paramètres personnalisés</td> 
   <td>VOD + En direct</td> 
   <td>√</td> 
   <td>√ (Pré-enregistrements VOD uniquement)</td> 
  </tr>
  <tr>
   <td>Comportements publicitaires personnalisés</td> 
   <td>VOD + En direct</td> 
   <td>√</td> 
   <td>√ (Pré-enregistrements VOD uniquement)</td> 
  </tr>
  <tr>
   <td>Balises publicitaires personnalisées</td> 
   <td>En direct</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Résolveurs de publicités personnalisés</td> 
   <td>VOD + En direct</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Résolveur de publicité personnalisée à roue libre</td> 
   <td>VOD</td> 
   <td>Non pris en charge</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Remplacement de publicité C3 </td> 
   <td>VOD + En direct</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Chargement différé des publicités</td> 
   <td>VOD</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>
    <ul> 
     <li>Prise en charge des marqueurs de discontinuité - SSAI (HLS) </li> 
     <li>Multi-périodes (DASH)</li> 
    </ul> </td> 
   <td>VOD + En direct</td> 
   <td>√ </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Publicités d’accompagnement, bannières publicitaires et publicités cliquables</td> 
   <td>VOD + En direct</td> 
   <td>√ </td> 
   <td>√ (Pré-enregistrements VOD uniquement)</td> 
  </tr>
  <tr>
   <td>VPAID 2.0</td> 
   <td>VOD + En direct</td> 
   <td>√ (JS) </td> 
   <td>√ (Pré-enregistrements VOD uniquement)</td> 
  </tr>
  <tr>
   <td>Sortie anticipée de publicité</td> 
   <td>En direct</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Création VOD + hiérarchisation en direct basée sur des règles</td> 
   <td>VOD + En direct</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Règles CRS </td> 
   <td>VOD + En direct</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
 </tbody>
</table>

## Fonctionnalités de protection du contenu {#content-protection-features}

| **Fonctionnalité** | **Type de contenu** | **HLS** | **DASH** |
|---|---|---|---|
| Chiffrement AES | VOD + En direct | √ | √ (VOD uniquement) |
| Exemple de chiffrement AES | VOD + En direct | √ |  |
| Flux Tokenized | VOD + En direct | √ |  |
| DRM | VOD + En direct | Primetime DRM uniquement (Future : Widevine) | Widevine uniquement |
| Lecture externe (RBOP) | VOD + En direct | Primetime DRM uniquement | Non pris en charge |
| Rotation de licence | VOD + En direct | Primetime DRM uniquement | Non pris en charge |
| Rotation des clés | VOD + En direct | Primetime DRM uniquement | Non pris en charge |

### Fonctions d’intégration {#integration-features}

| **Fonctionnalité** | **Type de contenu** | **HLS** | **DASH** |
|---|---|---|---|
| Intégration d’Adobe Analytics VHL | VOD + En direct | √ | √ |
| Facturation | VOD + En direct | √ | Non pris en charge |

## Fonctionnalités non prises en charge {#features-not-supported}

Cette version de TVSDK ne prend pas en charge :

* Abandon de publicités.
* Le mouvement lent dans les jeux de fiction.
* Effectuez une recherche et créez un aperçu avec du contenu MP4.
* Insertion de l&#39;annonce avec le contenu principal MP4.
* Rechercher quand une publicité est en cours de lecture
* Lecture des publicités avec support audio uniquement.

## Problèmes connus et limites {#known-issues-and-limitations}

Cette version de TVSDK présente les problèmes suivants :

* Le blocage VOD DRM LBA par auditude spécifique à l’appareil (Samsung Galaxy Tab 4) et le clic sur les publicités
* La publicité post-roll n’est pas lue pour un contenu spécifique.
* La définition de la légende de fermeture sur les langues CJK ne fonctionne pas.
* La vidéo peut sortir du mode de ruse automatiquement entre VOD et live.
* VHL : les appels de pulsation incorrects sont envoyés lorsque nous commençons un contenu à partir d’un décalage.
* Lorsque des publicités VPAID sont lues, des appels de pulsation VHL sont lus pour un événement.:type:la publicité de lecture est manquante.
* La publicité preroll est lue même si adBreakPolicy SKIP est sélectionné.
* Une fois que vous êtes entré dans le lecteur d’état complet, il revient à l’état de lecture avec SKIP adBreakPolicy pour les publicités preroll.

Sans vidéo, il n’y a pas de dimension de fenêtre d’affichage et sans dimension de fenêtre d’affichage, vous ne pouvez pas afficher de graphiques pour les sous-titres.

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://experienceleague.adobe.com/docs/primetime.html) page.
