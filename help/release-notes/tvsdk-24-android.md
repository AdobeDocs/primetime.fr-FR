---
title: Notes de mise à jour de TVSDK 2.4.1 pour Android
seo-title: Notes de mise à jour de TVSDK 2.4.1 pour Android
description: Les Notes de mise à jour de TVSDK 2.4.1 pour Android décrivent les nouvelles fonctionnalités et les fonctionnalités prises en charge, ainsi que les problèmes et limitations connus de TVSDK Android 2.4.1.
seo-description: Les Notes de mise à jour de TVSDK 2.4.1 pour Android décrivent les nouvelles fonctionnalités et les fonctionnalités prises en charge, ainsi que les problèmes et limitations connus de TVSDK Android 2.4.1.
uuid: 929fc577-e851-4e03-9201-13280cc6137a
topic-tags: release-notes
products: SG_PRIMETIME
discoiquuid: a6dbcc4a-9e14-4452-9004-b39ed13fad6f
translation-type: tm+mt
source-git-commit: e644e8497e118e2d03e72bef727c4ce1455d68d6

---


# Notes de mise à jour de TVSDK 2.4.1 pour Android {#tvsdk-for-android-release-notes}

Les Notes de mise à jour de TVSDK 2.4.1 pour Android décrivent les nouvelles fonctionnalités et les fonctionnalités prises en charge, ainsi que les problèmes et limitations connus de TVSDK Android 2.4.1.

## TVSDK Android 2.4.1 {#tvsdk-android}

Adobe publie TVSDK 2.4.1 pour Android.

Pour utiliser cette version de TVSDK, assurez-vous que votre système répond aux exigences décrites dans la section Configuration requise [pour le](https://helpx.adobe.com/content/dam/help/en/primetime/programming-guides/psdk_android_2.5.pdf#page=6)système.

Vous trouverez ci-dessous la documentation :

・ Système d&#39;aide en ligne TVSDK 2.4 pour l&#39;aide Android

・ [Javadocs TVSDK 2.4 pour l’API Java Android](https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/index.html)

Les Javadocs sont l’autorité suprême, car ils sont automatiquement générés directement à partir du code source TVSDK.

・ Documentation de l’API [C++ TVSDK 2.4 pour l’API C++ Android](https://help.adobe.com/en_US/primetime/api/psdk/cpp_2.4/namespaces.html)

Chaque classe Java possède une classe C++ correspondante, et la documentation C++ contient plus d&#39;explications que les Javadocs. Consultez donc la documentation C++ pour en savoir plus sur l&#39;API Java.

・ Guide de migration (Guide[de migration de](../migration-guides/tvsdk-14-25-android.md)TVSDK 2.4 pour Android)

Ce guide explique ce que vous devez modifier pour migrer une application basée sur TVSDK 1.4 vers une application basée sur TVSDK 2.4.

## Nouvelles fonctionnalités {#new-features}

TVSDK 2.4.1 pour Android offre de nombreuses améliorations de performances par rapport aux versions antérieures. Il offre une expérience de visualisation de haute qualité.

Cette version comprend toutes les fonctionnalités des versions 2.4 et 2.4.1 et aucune fonctionnalité n’est obsolète.

Voici les principales nouvelles fonctionnalités de la version 2.4.1 :

* Fonctionnalités HLS version 4

   * **Lecture** vidéo (lecture, pause, recherche) avec contrôle du lecteur pour les flux en direct, linéaires et VOD.
   * **Sous-titrage fermé.** TVSDK peut afficher des légendes fermées 608/708 avec une sélection de polices, tailles de police, couleurs et arrière-plan. Il peut également prendre en charge les vidéos avec des légendes cumulées et passer d’un suivi de langue à l’autre si elles sont disponibles.
   * **Le mode** de lecture de la vidéo prend en charge l’avance rapide et le rembobinage pour les flux HLS qui utilisent les i-Frames. Toutes les commandes de lecture vidéo fonctionnent sur le contenu. Le mouvement lent (avant) est disponible pour le mode de lecture vidéo externe avec des taux compris entre 0 et 1.
   * **Le débit adaptatif (ABR)** permet au lecteur de sélectionner dynamiquement l’une des versions multiples du même flux de contenu à lire, en fonction du réseau et d’autres conditions. Vous pouvez définir des paramètres de manière dynamique ou dans le fichier manifeste afin de les sélectionner parmi des stratégies de sélection agressives, modérées et conservatrices.
   * **Les plages** d’octets permettent à un seul fichier TS de contenir plusieurs segments TS.
   * **Les autres rendus** audio permettent au lecteur de basculer entre les pistes audio disponibles.
   * **Prise en charge d’ID3.** TVSDK peut lire des flux audio et vidéo HLS contenant des métadonnées audio ID3, telles que le nom de l’artiste, le titre et l’album.
   * **Basculement. **TVSDK utilise des stratégies pour poursuivre la lecture ininterrompue, en dépit des échecs des serveurs hôtes, des fichiers de liste de lecture et des segments.
   * **Transmission audio multicanal (DD+).** TVSDK peut transmettre des données audio Dolby Digital Plus (E-AC3) au matériel de prise en charge.

* Fonctionnalités de protection du contenu

   * **DRM pour HLS.** Toutes les API de lecture vidéo fonctionnent avec du contenu vidéo chiffré protégé par Adobe Access. Les fonctionnalités DRM suivantes sont prises en charge :

      * Rotation des licences
      * Rotation clé
      * Mise en cache des licences
      * Temps de la stratégie
      * rotation IV

* **Lecture AES 128.** TVSDK peut lire le contenu HLS standard de chiffrement avancé (AES) avec une taille de clé de 128 bits.
* **Le protocole PHLS (Protected HLS)** fournit un ensemble limité de stratégies DRM prédéfinies, un sous-ensemble de ce qu&#39;Adobe Access fournit, pour permettre la gestion DRM légère par rapport au protocole HLS pour les flux en direct et VOD.

* Fonctionnalités de publicité/de remplacement de contenu et de monétisation

   * **Suivi des publicités insérées côté serveur.** TVSDK peut effectuer le suivi des publicités insérées par le service d’insertion publicitaire Adobe Cloud. Il prend en charge les annonces linéaires aux formats VAST2, VAST3 et VMAP pour les flux VOD et les flux vivants/linéaires.
   * **Balises HLS personnalisées.** TVSDK utilise sa `MediaPlayerConfig` classe pour activer la notification de l’application du lecteur lorsque des balises HLS personnalisées apparaissent dans le flux.
   * **Insertion publicitaire côté client.** La bibliothèque d’insertion d’annonces Auditude fonctionne avec les serveurs Adobe Auditude pour résoudre les publicités en vue de les insérer dynamiquement dans du contenu en direct, linéaire et VOD, aux positions preroll, mid-roll ou post-roll.
   * **Résolveurs d’annonces personnalisés.** Les `ContentResolver, OpportunityGenerator,` et `MediaPlayerClientFactory` interfaces vous permettent de mettre en oeuvre un résolveur de publicités/de contenu alternatif personnalisé et d’enregistrer un détecteur d’opportunités personnalisé pour travailler avec TVSDK. Les `TestAdResolver` classes et `AuditudeResolver` fournissent des exemples C++ d’implémentation d’un résolveur de contenu. Vous trouverez un exemple JavaScript à `samples/jspsdk/testapp/psdk.js`.
   * **Comportement cohérent des publicités.** Utilisez l’ `AdPolicySelector` interface pour permettre un comportement cohérent dans tous les lecteurs pour des opérations telles que la recherche et le jeu vidéo lorsque des publicités sont présentes dans le contenu. Si vous n’implémentez pas les vôtres, TVSDK utilise `DefaultAdPolicySelector`.
   * **Supprimez/remplacez des publicités C3.** Utilisez l’API TVSDK appropriée pour supprimer des plages de contenu personnalisées et insérer dynamiquement de nouvelles publicités sans préparation supplémentaire. C&#39;est pratique lorsque du contenu en direct/linéaire est diffusé, puis immédiatement disponible à la demande sans nettoyage.

Voici les principales nouvelles fonctionnalités de la version 2.4 :

* **Instantané pour VOD et en direct** Lorsque vous activez l’instantané, TVSDK initialise et met en mémoire tampon le média avant les débuts de lecture. Comme vous pouvez lancer plusieurs `MediaPlayerItemLoader` instances simultanément en arrière-plan, vous pouvez mettre en mémoire tampon plusieurs flux. Lorsqu’un utilisateur modifie le canal et que le flux est correctement mis en mémoire tampon, la lecture sur le nouveau canal s’effectue immédiatement. TVSDK 2.4 prend également en charge Instant On pour les flux en direct. Les flux en direct sont remis en mémoire tampon lorsque la fenêtre active se déplace.

* **Améliorations des performances **La nouvelle architecture TVSDK 2.4 apporte diverses améliorations aux performances :

   * **Sous-segmentation** : TVSDK réduit davantage la taille de chaque fragment pour permettre la lecture début dès que possible.
   * **Téléchargements** d’annonces parallèles : TVSDK prérécupère les publicités en parallèle à la lecture du contenu avant d’atteindre les coupures publicitaires, ce qui permet une lecture transparente des publicités et du contenu.
   * **Résolution** des publicités différée - Avec cette fonctionnalité, nous n&#39;attendons pas la résolution des publicités non preroll avant de commencer la lecture, ce qui réduit le temps de démarrage. Les API telles que la recherche et le jeu vidéo ne sont toujours pas autorisées tant que toutes les publicités ne sont pas résolues.

* **Lecture du contenu MP4**

Cette version de TVSDK prend en charge la lecture de MP4 en tant que contenu principal.

* **Connexions réseau persistantes**

TVSDK conserve un ensemble de connexions réseau réutilisables, de sorte qu’il n’est pas nécessaire de créer et de détruire une connexion réseau pour chaque demande de réseau.

* **Protection de la sortie basée sur la résolution**

Cette fonctionnalité établit un lien entre les restrictions de lecture et des résolutions spécifiques, offrant ainsi des commandes DRM plus fines.

* **Lecture avec débit binaire adaptatif (ABR)**

Cette fonctionnalité permet à TVSDK de basculer entre les flux iFrame en mode de lecture par astuces. Vous pouvez utiliser des profils autres qu’iFrame pour jouer à des vitesses de lecture inférieures.

* **Lissage du jeu**

Ces améliorations améliorent l’expérience des utilisateurs :

・ Sélection adaptative du débit binaire et de la fréquence d’images lors de la lecture de l’astuce, en fonction de la bande passante et du profil de mémoire tampon

・ Utilisez le flux principal plutôt que le flux IDR pour obtenir une lecture rapide jusqu&#39;à 30 i/s.

* **Logique ABR améliorée**

La nouvelle logique ABR est basée sur la longueur de la mémoire tampon, le taux de changement de la longueur de la mémoire tampon et la bande passante mesurée. Ainsi, l&#39;ABR choisit le débit approprié lorsque la bande passante fluctue et optimise le nombre de fois où le commutateur de débit se produit réellement en surveillant le débit auquel la longueur de la mémoire tampon change.

* **Facturation**

TVSDK collecte automatiquement des mesures, en conformité avec le contrat de vente du client, afin de générer des rapports d’utilisation périodiques requis pour la facturation. Sur chaque événement de début de diffusion en continu, TVSDK utilise l’API d’insertion de données d’Adobe Analytics pour envoyer des mesures de facturation telles que le type de contenu, les indicateurs activés pour l’insertion de publicités et les indicateurs activés pour l’insertion de données drm - en fonction de la durée du flux facturable - à la suite de rapports détenue par Adobe Analytics Primetime. Cela n’interfère pas avec les suites de rapports Adobe Analytics ou les appels au serveur du client, ni ne les inclut. Sur demande, ce rapport sur l&#39;utilisation de la facturation est envoyé périodiquement aux clients. Il s&#39;agit de la première phase de la fonction de facturation qui ne prend en charge que la facturation d&#39;utilisation. Il peut être configuré en fonction du contrat de vente à l’aide des API décrites dans la documentation.

## Fonctionnalités prises en charge {#supported-features}

TVSDK for Android 2.4 prend en charge un certain nombre de fonctionnalités que vous pouvez mettre en oeuvre pour ajouter des fonctionnalités à vos applications vidéo.

>[!NOTE]
>
>Dans les tableaux de la matrice des fonctionnalités ci-dessous, un √ signifie que la fonctionnalité est prise en charge dans la version actuelle.

### Fonctionnalités de lecture principales {#core-playback-features}

| **Fonction** | **Type de contenu** | **HLS** | **DASH** |
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
| Notifications de la qualité de service et du lecteur | VOD + Live | √ | √ (VOD uniquement) |
| Prise en charge des en-têtes de cookie | VOD + Live | √ | √ (VOD uniquement) |
| Prise en charge des en-têtes personnalisés | VOD + Live | Non pris en charge | Non pris en charge |
| Définir les paramètres de contrôle de la mémoire tampon | VOD + Live | √ | √ (VOD uniquement) |
| Définition des contrôles de débit binaire adaptatif | VOD + Live | √ | √ (VOD uniquement) |
| Balises de manifeste personnalisées (HLS) / Flux de Événement (DASH) | VOD + Live | √ | √ (VOD uniquement) |
| Audio lié en retard | VOD + Live | √ | √ (VOD uniquement) |
| 302 Redirection | VOD + Live | √ | √ (VOD uniquement) |

### Fonctionnalités de lecture avancées {#advanced-playback-features}

<table> 
 <tbody>
  <tr>
   <td><strong>Fonction</strong></td> 
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
   <td>Lecture de la bande </td> 
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
   <td>Analyse ID3 (HLS) / Métadonnées temporisées (DASH)</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Coupures </td> 
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
   <td>302 Attractif de redirection</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√ (VOD uniquement)</td> 
  </tr>
  <tr>
   <td>Défilement des miniatures (Iframe et JPEG)</td> 
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

### Fonctionnalités d’insertion d’annonce principale (CSAI) {#core-ad-insertion-features-csai}

| **Fonction** | **Type de contenu** | **HLS** | **DASH** |
|---|---|---|---|
| Lecture générale, publicités activées | VOD + Live | √ | √ (VOD Pre-rolls uniquement) |
| Contenu FER avec publicités activées | VOD | √ | Non pris en charge |
| Comportements publicitaires par défaut | VOD + Live | √ | √ (VOD Pre-rolls uniquement) |
| VAST 2.0/3.0 | VOD + Live | √ | √ (VOD Pre-rolls uniquement) |
| VMAP 1.0 | VOD + Live | √ | √ (VOD Pre-rolls uniquement) |
| Publicités MP4 | VOD + Live | √ (provenant de CRS) | √ (provenant de CRS, pré-rouleaux uniquement) |

### Fonctionnalités avancées d’insertion d’annonce (CSAI) {#advanced-ad-insertion-features-csai}

<table> 
 <tbody>
  <tr>
   <td><strong>Fonction</strong></td> 
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
   <td>√ (VOD Pre-rolls uniquement)</td> 
  </tr>
  <tr>
   <td>Paramètres personnalisés</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√ (VOD Pre-rolls uniquement)</td> 
  </tr>
  <tr>
   <td>Comportements publicitaires personnalisés</td> 
   <td>VOD + Live</td> 
   <td>√</td> 
   <td>√ (VOD Pre-rolls uniquement)</td> 
  </tr>
  <tr>
   <td>Balises publicitaires personnalisées</td> 
   <td>Live</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Résolveurs d’annonces personnalisés</td> 
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
   <td>C3 Remplacement de publicité </td> 
   <td>VOD + Live</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>Chargement publicitaire différé</td> 
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
   <td>√ (VOD Pre-rolls uniquement)</td> 
  </tr>
  <tr>
   <td>VPAID 2.0</td> 
   <td>VOD + Live</td> 
   <td>√ (JS) </td> 
   <td>√ (VOD Pre-rolls uniquement)</td> 
  </tr>
  <tr>
   <td>Sortie de publicité anticipée</td> 
   <td>Live</td> 
   <td>√ </td> 
   <td>Non pris en charge</td> 
  </tr>
  <tr>
   <td>VOD créatif basé sur des règles + hiérarchisation en direct</td> 
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

| **Fonction** | **Type de contenu** | **HLS** | **DASH** |
|---|---|---|---|
| Chiffrement AES | VOD + Live | √ | √ (VOD uniquement) |
| Exemple de chiffrement AES | VOD + Live | √ |  |
| Flux jetés | VOD + Live | √ |  |
| DRM | VOD + Live | Primetime DRM uniquement (Futur : Widevine) | Équipement uniquement |
| Lecture externe (RBOP) | VOD + Live | DRM Primetime uniquement | Non pris en charge |
| Rotation de licence | VOD + Live | DRM Primetime uniquement | Non pris en charge |
| Rotation clé | VOD + Live | DRM Primetime uniquement | Non pris en charge |

### Fonctionnalités d’intégration {#integration-features}

| **Fonction** | **Type de contenu** | **HLS** | **DASH** |
|---|---|---|---|
| Intégration d’Adobe Analytics VHL | VOD + Live | √ | √ |
| Facturation | VOD + Live | √ | Non pris en charge |

## Fonctions non prises en charge {#features-not-supported}

Cette version de TVSDK ne prend pas en charge :

* Abandon de publicité.
* Le mouvement lent dans le jeu de la ruse.
* Recherchez et jouez avec du contenu MP4.
* Insertion d’une publicité avec le contenu principal MP4.
* Recherchez quand une publicité est en cours de lecture.
* Lecture des publicités avec des supports audio uniquement.

## Problèmes et limites connus {#known-issues-and-limitations}

Cette version de TVSDK présente les problèmes suivants :

* Un périphérique spécifique (Samsung Galaxy Tab 4) bloque VOD DRM LBA avec auditude et clique sur les publicités
* La publicité post-roll n’est pas lue pour un contenu spécifique.
* La définition de la légende de fermeture en langues CJK ne fonctionne pas.
* La vidéo peut sortir du mode tour automatiquement entre VOD et live.
* VHL - des appels de pulsation incorrects sont envoyés lorsque nous début un contenu à partir d’un décalage.
* Lorsque des publicités VPAID sont lues, les appels de pulsation VHL pour événement:type:play sont manquants.
* La publicité preroll est lue même si adBreakPolicy SKIP est sélectionné.
* Une fois que vous êtes entré dans le lecteur d’état complet, vous revenez à l’état Lecture avec SKIP adBreakPolicy pour les publicités post-roll.

Sans vidéo, il n’y a pas de dimension de fenêtre d’affichage et sans dimension de fenêtre d’affichage, vous ne pouvez pas afficher de graphiques pour les légendes.

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.