---
title: Notes de mise à jour de TVSDK 1.4 pour Android
description: Les notes de mise à jour de TVSDK 1.4 pour Android décrivent les nouveautés ou les modifications, les problèmes résolus et connus et les problèmes d’appareil dans TVSDK Android 1.4.
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '7802'
ht-degree: 0%

---

# Notes de mise à jour de TVSDK 1.4 pour Android {#tvsdk-for-android-release-notes}

Les notes de mise à jour de TVSDK 1.4 pour Android décrivent les nouveautés ou les modifications, les problèmes résolus et connus et les problèmes d’appareil dans TVSDK Android 1.4.

## Nouvelles fonctionnalités {#new-features}

**Version 1.4.43**

**Chargement sécurisé des publicités par HTTPS**

Adobe Primetime offre une option pour demander le premier appel au serveur de publicités primetime et CRS via HTTPS.

**alwaysUseAudioOutputLatency(valeur booléenne) dans la classe MediaPlayer**

Lorsque ce paramètre est défini, utilisez la latence de sortie audio dans le calcul de l’horodatage audio.

Il accepte un val de paramètres booléens. Si sa valeur est `True`, le client utilise la latence de sortie audio dans le calcul de l’horodatage audio.

**Version 1.4.42**

**Insertion de coupure publicitaire partielle :**
Expérience de type télévision consistant à se joindre au milieu d’une publicité sans déclencher le suivi pour la publicité visionnée partiellement.
Exemple : l’utilisateur se joint au milieu (à 40 secondes) d’une coupure publicitaire de 90 secondes composée de trois publicités de 30 secondes. Cette coupure intervient 10 secondes dans la seconde publicité.
* La deuxième publicité est lue pendant la durée restante (20 secondes), suivie de la troisième publicité.
* Les dispositifs de suivi des publicités pour la publicité partielle lue (deuxième publicité) ne sont pas déclenchés. Les dispositifs de suivi de la troisième publicité uniquement sont déclenchés.

**Version 1.4.41**

Aucune nouvelle fonctionnalité.

**Version 1.4.40**

Aucune nouvelle fonctionnalité.

>[!NOTE]
>
>Vous n’aurez pas besoin des modifications de l’API si vous utilisez une version antérieure à 1.4.39.

**Version 1.4.39**

* TVSDK est certifié avec VHL 2.0.1 et avec VHL 2.0.1 avec Nielsen.
* Android TVSDK est mis à jour pour envoyer des requêtes CRS à partir du nouvel hôte Akamai. `primetime-a.akamaihd.net`.
* La nouvelle configuration du nom d’hôte permet la diffusion de ressources CRS via HTTP et HTTPS (SSL) à plus grande échelle.
* TVSDK prend en charge la version Android Oreo.
* Une nouvelle fonction est ajoutée à la fonction `AdClientFactory` pour prendre en charge l’enregistrement de plusieurs détecteurs d’opportunités :

  ```
  public List<PlacementOpportunityDetector> createOpportunityDetectors(MediaPlayerItem item);
  ```

  Cela doit renvoyer un tableau de PlacementOpportunityDetector. Vous pouvez désormais enregistrer plusieurs détecteurs d’opportunités. Par exemple, pour la fonction de sortie anticipée de la publicité, deux détecteurs d’opportunités étaient nécessaires : l’un pour l’insertion de publicités et l’autre pour une sortie anticipée de la publicité. Vous devez implémenter cette nouvelle fonction uniquement si vous avez implémenté votre propre AdvertisingFactory (et n’utilisez pas DefaultAdvertisingfactory). Pour obtenir le comportement existant, vous devez créer un seul détecteur d’opportunités, comme dans la fonction createOpportunityDetector() , le placer dans un tableau et le renvoyer :

  ```
  public class MyAdvertisingFactory extends AdvertisingFactory {  
  …  
  @Override  
  public List&lt;PlacementOpportunityDetector&gt; createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {  
  List&lt;PlacementOpportunityDetector&gt; opportunityDetectors = new ArrayList&lt;PlacementOpportunityDetector&gt;();  
  opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));  
  return opportunityDetectors;  
  } }
  ```

>[!NOTE]
>
>Vous n’aurez pas besoin des modifications de l’API si vous utilisez une version antérieure à 1.4.39.

**Version 1.4.36**

Correction de bogue pour le saut de contenu sur Android.

**Version 1.4.35**

* **Informations sur la publicité réseau**

  Les API TVSDK fournissent désormais des informations supplémentaires sur les réponses VAST tierces. L’identifiant de publicité, le système d’annonces et les extensions d’annonce VAST sont fournis dans la classe NetworkAdInfo accessible par le biais de la propriété networkAdInfo sur une ressource d’annonce. Ces informations peuvent être utilisées pour l’intégration à d’autres plateformes Ad Analytics telles que **Analyses de cheminement**.

**Version 1.4.31**

**Prise en charge multi-réseau de diffusion de contenu pour les annonces CRS**
* Par défaut, toutes les ressources transcodées seront hébergées sur le réseau de diffusion de contenu détenu par l’Adobe sur Akamai. Avec la dernière version, Adobe Creative Repackaging Service (CRS) permet de charger les créatifs transcodés sur plusieurs CDN, comme spécifié par le client.
* De nouvelles API sont ajoutées à TVSDK pour permettre la spécification de l’URL créative CRS finale lorsque l’URL par défaut n’est pas utilisée. Reportez-vous à la documentation pour savoir comment utiliser ces nouvelles API.

**Version 1.4.18**
Primetime Android TVSDK prend désormais en charge les créatifs JavaScript VPAID 2.0 pour permettre une expérience publicitaire interactive riche en flux continu. Pour plus d’informations sur VPAID 2.0, voir [Prise en charge des publicités VPAID](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/vpaid-ads/android-3x-vpaid-ads.md).

**Version 1.4.17**

AC-3 5.1 est pris en charge uniquement sur Amazon FireTV.

**Version 1.4.11**

* **Secours de la publicité, formation de Daisy dans la logique de sélection des publicités (Zendesk #3103** Pour les publicités VAST (créatives) avec la règle de secours activée, TVSDK traite une publicité avec un type MIME non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.

Pour plus d’informations, voir [Reprise de publicité pour les publicités VAST et VMAP](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-fallback/android-3x-ad-fallback.md).

* **Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.5**
   * Possibilité d’envoyer des métadonnées avec le démarrage de la vidéo et/ou vidéo/ad/chapitre en tant que données contextuelles
   * Moins de trafic réseau : les pulsations sont moins nombreuses en moyenne et de taille inférieure.

**Version 1.4.7**

* **Prise en charge de l’individualisation sur site** Prise en charge des installations on-premise du serveur d’individualisation Adobe pour personnaliser la demande d’individualisation du client afin d’accéder à un autre point de terminaison.

**Version 1.4.6**

* **Exemple de chiffrement AES (nécessite la version 17.0.0.134 du Flash Player) **Le chiffrement AES par exemple est désormais pris en charge.

**Version 1.4.2**

* **Mise à jour de la bibliothèque Video Heartbeats (VHL) vers la version 1.4.0.1**

   * Ajout de la possibilité de regrouper différents cas d’utilisation d’analyse, à partir d’autres SDK ou lecteurs, avec les composants vidéo essentiels d’Adobe Analytics.
   * Le suivi des publicités a été optimisé en supprimant les méthodes trackAdBreakStart et trackAdBreakComplete . La coupure publicitaire est déduite des appels des méthodes trackAdStart et trackAdComplete .
   * La propriété playhead n’est plus nécessaire lors du suivi des publicités.

* **Intégration du SDK Nielsen** TVSDK prend désormais en charge l’envoi d’informations de suivi utilisateur au SDK Nielsen sans intégration personnalisée.

**Version 1.4.0**

* **Signalisation par blackout avec remplacement de contenu alternatif** Dans le cadre de la mise à jour de la version 1.4 de TVSDK, TVSDK prend également en charge l’entrée et le retour de pannes régionales de contenu linéaire. TVSDK peut désormais traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d’interruption même lorsque des programmes alternatifs sont affichés à la place de la programmation d’origine.

* **Supprimer/Remplacer des publicités C3** Désormais, aucun travail de préparation supplémentaire n’est nécessaire pour insérer dynamiquement de nouvelles publicités dans les ressources vidéo à la demande (VOD) qui sortent de la fenêtre C3. TVSDK fournit désormais une API pour supprimer des plages de contenu personnalisées et insérer dynamiquement de nouvelles publicités. Cette nouvelle fonctionnalité puissante est également utile dans les cas où le contenu en direct/linéaire est diffusé pendant la diffusion et est immédiatement retiré pour être utilisé comme contenu à la demande sans temps approprié pour &quot;nettoyer&quot; la ressource.

* L’interface PlaybackEventListener comporte une nouvelle méthode appelée onReplaceMediaPlayerItem, que vous pouvez utiliser pour écouter un nouvel événement, `ITEM_REPLACED`. Cet événement est distribué chaque fois qu’une instance MediaPlayeritem est remplacée sur MediaPlayer. L’application cliente implémentant ce PlaybackEventListener doit implémenter ou remplacer cette nouvelle méthode.
* AdClientFactory comporte une nouvelle fonction ajoutée à la classe pour s’enregistrer pour plusieurs détecteurs d’opportunités :

  ```
  public List&lt;PlacementOpportunityDetector&gt; createOpportunityDetectors(MediaPlayerItem item);
  
  For example for early ad exit feature, you need two Opportunity Detectors - one for ad insertion and another for  early  exit from  `ad`.
  
  To override this new function create a single Opportunity Detector, and put into an array and return:
  
  @Override
  
  public List&lt;PlacementOpportunityDetector&gt; createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {
  
  List&lt;PlacementOpportunityDetector&gt; opportunityDetectors = new ArrayList&lt;PlacementOpportunityDetector&gt;();
  
  opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));
  
  return opportunityDetectors;
  }
  
  }
  ```

## Modifications de TVSDK pour la version 1.4 {#tvsdk-changes}

* L’interface PlaybackEventListener comporte une nouvelle méthode appelée onReplaceMediaPlayerItem, que vous pouvez utiliser pour écouter un nouvel événement, Item_REPLACED. Cet événement est distribué chaque fois qu’une instance MediaPlayeritem est remplacée sur MediaPlayer. L’application cliente implémentant ce PlaybackEventListener doit implémenter ou remplacer cette nouvelle méthode.

* AdClientFactory comporte une nouvelle fonction ajoutée à la classe pour s’enregistrer pour plusieurs détecteurs d’opportunités :

```
public List`<PlacementOpportunityDetector>` createOpportunityDetectors(MediaPlayerItem item);
```

Par exemple, pour la fonctionnalité de sortie anticipée de publicité, vous avez besoin de deux détecteurs d’opportunités : l’un pour l’insertion de publicités et l’autre pour une sortie anticipée de la publicité.

Pour remplacer cette nouvelle fonction, créez un seul détecteur d’opportunités, placez-le dans un tableau et renvoyez :

```
@Override

public List`<PlacementOpportunityDetector>` createOpportunityDetectors(MediaPlayerItem mediaPlayerItem) {

List`<PlacementOpportunityDetector>` opportunityDetectors = new ArrayList`<PlacementOpportunityDetector>`();

opportunityDetectors.add(createOpportunityDetector(mediaPlayerItem));

return opportunityDetectors;

}

}
```

## Certification et prise en charge des périphériques dans la version 1.4 {#device-certification-and-support-in}

>[!NOTE]
>
>Les fonctionnalités suivantes sont disponibles : **not** pris en charge dans TVSDK :
>
>* Déplacement lent, sur n’importe quelle plateforme ou version.
>* Jouer aux tours en direct.

**Version 1.4.43**

TVSDK 1.4.43 a été certifié avec les périphériques Android possédant Android 6.0.1/7.0 et 8.1 (Oreo).

* **Version 1.4.23 :**

   * TVSDK 1.4.23 a été certifié pour les appareils Android avec Android N.

* **Version 1.4.18 :**

   * Primetime a été certifié pour Amazon Fire TV.
   * VPAID 2.0 n’est pris en charge que sur les appareils dotés d’Android 4.0 et versions ultérieures.

## Problèmes résolus dans 1.4 {#resolved-issues-in}

>[!NOTE]
>
>Tous les clients TVSDK qui utilisent CRS sont fortement encouragés à effectuer la mise à niveau vers TVSDK 1.4.39 ou la version la plus récente sur iOS et Android. Cette mise à niveau est une version complémentaire de la mise en oeuvre de l’application existante. Après la mise à niveau, recherchez les demandes d’URL de création CRS dans un outil de proxy (Charles, par exemple) pour vérifier que la version du chemin d’accès reflète la version 3.1. Par exemple :
>
>`https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8`

**Version 1.4.43**

* Ticket #27143 - Impossible de lire la piste audio 5.1 sur les appareils FireTV

   * TVSDK peut désormais lire du son AC3 sur les appareils FireTV. La lecture est toujours en stéréo.

* Ticket #33902 - Diffusion sécurisée des publicités via HTTPS

   * Adobe Primetime offre une option pour demander le premier appel au serveur de publicités en temps réel et à CRS sur https.

* Ticket #34493 - Délai audio Bluetooth

   * Ajout `alwaysUseAudioOutputLatency` dans la classe MediaPlayer qui, lorsqu’elle est définie, entraîne l’utilisation de la latence de sortie audio dans le calcul de l’horodatage audio.

* Ticket #34949 - Nouvelle version de la bibliothèque Video Heartbeat (VHL) intégrée.

**Version 1.4.42 (1791)**

* Zendesk #33719 : FireTV 4k Le débit adaptatif évolue lentement. Ajout de la prise en charge d’ABR pour les appareils FireTV 4K.
* Zendesk #33338 : resetDRM efface toutes les données de l’application.  Traitement de la casse supplémentaire lorsque des exceptions dans des threads non TVSDK provoquaient le remplissage des files d’attente d’opération TVSDK.

**Version 1.4.41 (1776)**

* Zendesk #33002 - Companion asset data from TVSDK sur Fire TV. Mise en oeuvre d’une nouvelle classe AdBannerAsset qui renverra les données d’accompagnement sous forme de liste &lt;adbannerasset> et AdAsset::id est désormais une chaîne au lieu d’une chaîne longue.
* Zendesk #32821 - Le lecteur Android Primetime se fige lorsqu’il rencontre l’horodatage de présentation (PTS) pour la guerre. Ce problème a été corrigé dans cette version.
* Zendesk #33572 - Blocage de démarrage de la publicité VideoAnalyticsProvider. L’utilisation de la bonne combinaison de la version du SDK commun VHL+Nielsen de VideoHeartbeat.jar a résolu ce problème.
* Zendesk #33355 - Fire TV : Retour à 15 secondes numéro. Aucun correctif du côté TVSDK et du client ne le vérifie à leur niveau de fin et tiers.

**Version 1.4.40 (1764)**

* Zendesk #33068 - Problème de synchronisation en forme Amazon sur le nouvel appareil. Le problème de synchronisation des lèvres a été corrigé dans cette version.
* Zendesk #32215 - Problèmes de sécurité d’Android TVSDK 1.4.38 `[Hotlist]`. Mise à jour vers les dernières versions d’OpenSSL-1.1.0 et de curl-7.55.1.
* Zendesk #32920 : écran vierge dans une coupure publicitaire et fin de la coupure publicitaire. Correction d’un problème en raison duquel un conteneur VPAID pouvait se trouver dans un état vide et entraînait le renvoi fréquent de plusieurs blocs CDATA dans un seul noeud \&amp;lt;AdParameters\&amp;gt; VAST.

**Version 1.4.39 (1744)**

* Zendesk #28976 - La demande de licence dure plus d&#39;une seconde. Tandis que les appels de demande de licence DRM utilisant POST sont en cours d’exécution, Curl ajoute un en-tête supplémentaire &quot;Expect: 100-continue&quot;. Suppression de l’en-tête &quot;Expect:&quot; dans TVSDK .
* Zendesk #27707 - Les environnements CSAI ne respectent pas les CUE DANS les marqueurs pour un retour ou un retour au contenu anticipé. Prise en charge de plusieurs générateurs d’opportunités.

**Version 1.4.38 (1722)**

* Zendesk #21590 - Performance vidéo et suivi dans les derniers builds d’origine

Intégration et certification de VHL 2.0 dans TVSDK pour réduire la barrière de mise en oeuvre de VideoHeartbeatsLibrary en réduisant la complexité des API.

* Zendesk #29688 - Prise en charge des clients Android O Beta.

Prise en charge de TVSDK pour la nouvelle version bêta d’Android.

**Version 1.4.36 (1713)**

* Zendesk #27392 - Saut de contenu sur Android

Pour s’adapter au décryptage, le TVSDK Android élargissait incorrectement la plage d’octets du contenu non iframe de 16 octets. L’élargissement est nécessaire pour les flux Iframe, mais pas pour les flux non iframe.

**Version 1.4.34 (1702)**

* Zendesk #27638 - Fuite dans l’objet cURL INet

L’objet Posix cURL inet fuyait tout en conservant le gestionnaire de partage et le cache DNS utilisé dans les connexions cURL.

Ce problème a été résolu en supprimant l’objet Posix cURL INet du déconstructeur INet .

**Version 1.4.33 (1694)**

* **Bibliothèque OpenSSL**

La bibliothèque OpenSSL a été mise à jour avec la version 1.0.2j d’OpenSSL.

* Zendesk #21701 - Envoyez l’URL de création d’origine pour la demande CRS 1401 au lieu de l’URL normalisée.
Ce problème est résolu en envoyant les URL de création d’origine.

* Zendesk #25023 - Lecture vidéo de longue durée : gel de la vidéo, scintillement de l’écran Ce problème a été résolu en définissant le nombre maximal de dimensions de format vidéo pour les périphériques de la boîte de dialogue CenturyLink.

* Zendesk #27460 - Le nouveau compte Akamai ne peut pas gérer une demande de réseau de diffusion de contenu de POST.
Le code a été mis à jour pour que la variable `cdn.auditude.com` demande d’annonce à GET au lieu de POST.

* Zendesk #28245 - L’état de lecture n’est pas averti correctement lorsque l’application passe d’arrière-plan au premier plan. Ce problème a été résolu en restaurant correctement l’état de lecture à lire ou à suspendre lorsque l’application revient au premier plan.

**Version 1.4.32 (1682)**

* Zendesk #25779 - La vulnérabilité de sécurité détectée avec TVSDK Android 4.2 et versions antérieures présente une vulnérabilité de sécurité lorsque JavaScript est activé dans une vue WebView. L’utilisation de WebView par TVSDK a été désactivée pour les appareils exécutant OS 4.2 ou version inférieure. Cela désactive l’utilisation des publicités VPAID dans TVSDK sur ces périphériques.

* Zendesk #26890 - Problème dans l’état ÉCRAN (ON/OFF) lors de la gestion de la référence. Lecteur Lorsque le moteur vidéo d’Adobe (AVE) reprend à partir d’un état SUSPENDU, DefaultMediaPlayer ne met pas à jour son état. Par conséquent, DefaultMediaPlayer reste à l’état SUSPENDU même si l’AVE est à l’état LECTURE. Ce problème a été résolu en définissant l’état DefaultMediaPlayer sur LECTURE lors de la réception d’un état LECTURE à partir de l’AVE, même si l’état actuel de DefaultMediaPlayer est SUSPENDU.

**Version 1.4.31 (1675)**

* Zendesk #21974 - Exceptions dues à des objets nuls
   * AdIndex est rarement incrémenté lorsque la valeur est nulle. Cela peut être dû à des appels d’API incorrects reçus pour adBreak preroll. Correction des types de données pour éviter de telles exceptions.

* Zendesk #24714 - Désactivez la journalisation superflue
   * Mise à jour du TVSDK pour désactiver la journalisation superflue

* Zendesk #24488 - Problèmes de synchronisation A/V sur Fire TV
   * Corrigé en améliorant la gestion des threads de décodage A/V. Plus précisément, lorsque les files d’attente d’entrée ou de sortie sont modifiées, le thread de décodage spécifique au type de contenu du cadre est exécuté.

* Zendesk #26551 - Réparer les échecs CRS
   * Lorsque la requête est HEAD (en-tête http), il n’est pas nécessaire de lire le contenu, car il est vide. Bien qu’il soit possible de le lire, l’ancien Android (4.0.x) se bloque pendant que nous appelons read() et la valeur correcte renvoyée par Android plus récente (-1) lors de l’appel read(). En fonction de cela, le code a été remplacé par ne pas lire le contenu pour &quot;head&quot;.

* Zendesk #26696 Null Pointer Exception lors de l’accès à TrickPlayManager
   * Corrigé en vérifiant si l’objet TrickPlayManager n’est pas nul avant de l’utiliser.

**Version 1.4.30 (1659)**

* Zendesk #22675 La durée des ressources n’est pas mise à jour pour les flux en direct/linéaire Ce problème a été résolu en fournissant une nouvelle API, assetDuration, dans PTVideoAnalyticsTrackingMetadata qui fournit la durée des ressources pour les flux en direct et linéaire.

* Zendesk #25853 Fuite de mémoire dans TVSDK lors du changement de canaux Le problème de fuite de mémoire tampon de lecture de fichier lorsqu’un lecteur multimédia est réinitialisé ou publié lors du téléchargement d’un fichier a été résolu.

**Version 1.4.29 (1653)**

* Zendesk #21200 - Le lecteur ne récupère pas de l’état suspendu lorsque l’application était en arrière-plan. Lorsque le lecteur a été suspendu après que le commutateur de diffusion a été signalé, la résolution permet au lecteur d’exécuter le commutateur de diffusion lors de la restauration du lecteur à partir de l’état de suspension, au lieu de restaurer la position précédente.

* Zendesk #23412 - Le lecteur est bloqué avec une boîte noire si vous cliquez sur n’importe quelle publicité dans les 3 derniers jours de la coupure publicitaire. Ce problème est le même que Zendesk #21200.

* Zendesk #23616 - La coupure publicitaire ignorée recherche trop loin dans le futur Selon le type d’insertion de publicité (insertion/remplacement), TVSDK détermine si la durée de publicité est utilisée dans le calcul pour déterminer le point de fin de coupure publicitaire.

* Zendesk #25078 - Fuite de mémoire TVSDK DRM sur Android TV STB La fuite de mémoire pour l’objet adaptateur DRM a été localisée et corrigée.

* Zendesk #25067 - Blocage dans VideoEngineTimeline Cela se produit parce que les objets n’ont pas été nettoyés correctement et que des événements ont été appelés après la destruction des objets. Le problème a été résolu en ajoutant des vérifications pour empêcher les exceptions nulles.

* Zendesk #25352 - Set custom HTTP header Ce problème a été résolu en ajoutant un nouvel en-tête personnalisé à la liste autorisée sur TVSDK.

* Zendesk #25617 - Rollover PTS de diffusion en direct provoquant une discontinuité du lecteur et un blocage de la mémoire Ce problème a été résolu en ajoutant une gestion de survol PTS dans FragmentedHTTPStreamer lorsqu’un survol se produit au milieu d’un segment.

**Version 1.4.28 (1637)**

* Zendesk #23618 - Événements de coupure publicitaire déclenchés avant la consultation de la politique publicitaire Ce problème a été résolu en ne déclenchant pas les événements AD_BREAK_START et AD_START lorsque la publicité est sautée en raison de adFordon. L’événement AD_BREAK_SKIPPED est envoyé à la place.

**Version 1.4.27 (1631)**

* Zendesk #23174 - Problème de performance lors du redimensionnement de la vidéo Ce problème a été résolu en fournissant une nouvelle API, MediaPlayerView.setSurfaceFixedSize, qui permet à TVSDK d’accéder à SurfaceHolder.setFixedSize() à partir de MediaPlayerView.

* Zendesk #24450 - TVSDK effectue des requêtes de publicité en double Ce problème se produisait lorsque le temps écoulé était converti en long et non pas en double, et ce problème a été corrigé.

**Version 1.4.26 (1627)**

* Zendesk #21436 - Mise à jour de la bibliothèque OpenSSL vers la version 1.0.2h Mise à jour de la bibliothèque OpenSSL vers OpenSSL version 1.0.2h
* Zendesk #23825 - Les cookies ne sont pas inclus dans les rappels corrigés en fournissant la prise en charge des cookies android.

**Version 1.4.25 (1620)**

* Zendesk #22900 - Live Adobe Primetime DRM stream n’est pas lu sur le lecteur de référence Android Le problème d’allocation de mémoire a été corrigé.
* Zendesk #23176 - L’application se bloque lorsqu’elle tente de lire des publicités VPAID Le blocage s’est produit car l’application ne crée pas d’affichage d’annonce personnalisé pour effectuer le rendu d’une publicité VPAID. Ce problème a été résolu en ignorant les publicités VPAID dans la réponse du serveur d’annonces lorsqu’il n’y a pas d’affichage d’annonces personnalisé.

* Zendesk #23153 - SampleAES DRM Stream - Playback stalling dans le lecteur de référence TVSDK Ce problème est identique à Zendesk #22900.

**Version 1.4.24 (1612)**

* Zendesk #20784 - Analytics : Déclenchement du contenu terminé pour les transitions vidéo en direct Ce problème a été résolu en ajoutant une API (trackVideoComplete) pour déclencher manuellement la fin du contenu lors d’une session de suivi vidéo en direct/linéaire.

* Zendesk #21977 Blocage de VideoEngineTimeline lors de l’opération placeAdBreak/acceptAd
   * Dans ce numéro, les bibliothèques suivantes ont été mises à jour :
      * Bibliothèque AdobeMobile vers la version 4.10.0
      * Bibliothèque VHL vers la version 1.5.6
      * Bibliothèque VHL-Nielsen vers la version 1.6.7

Ce problème a été résolu en ajoutant une vérification nulle avant d’ajouter des publicités à la liste des publicités acceptées.

* Zendesk #22313 Le débit pour les STB avec le jeu de puces Amilogic ne va pas au-delà de 1.2M Ce problème a été résolu en préchargeant les fonctionnalités du codec multimédia et en désactivant le commutateur transparent pour les chipset Amilogic.

* Zendesk #19520 Exemple de ressource AES HLS non lu dans les lecteurs TVSDK Ce problème a été résolu en gérant plusieurs descripteurs PMT pour les diffusions HLS chiffrées Sample AES.

**Version 1.4.23 (1602)**

* Zendesk #18852 - Mise à jour de la logique de sélection créative en fonction des règles CRS Ce problème a été résolu en ajoutant un fichier de configuration JSON pour spécifier la priorité de sélection créative.

* Zendesk #20861 - Android N Cette version prend en charge Android N en supprimant la possibilité d’utiliser directement les bibliothèques natives de la plateforme Android qui ne sont plus accessibles aux applications s’exécutant sur Android N.

* Zendesk #21018 - Blocage Android N Même résolution que ZD# 20861.

* Zendesk #21266 - VideoEngineAdapter se bloque sur une erreur Invalid_Key L’erreur Invalid_Key n’inclut pas de description de AVE. L’analyse du texte a donc abouti à NPE. Le problème a été résolu en ajoutant une vérification null pour la description pendant onError avant d’analyser la description.

* Zendesk #22286 - La bibliothèque native alloue la clé/le fragment de lecture de mémoire provoquant un blocage Ce blocage qui s’est produit sur Android lors de la tentative de chargement d’un manifeste avec plusieurs clés simultanément a été corrigé.

**Version 1.4.22 (1581)**

* Zendesk #17236 - Heure de début de lecture non fiable pour les vidéos HLS avec DRM Le saut de temps avec les flux LBA, où l’heure de début du segment audio ne correspond pas à l’heure de début du segment vidéo, a été corrigé.

* Zendesk #17680 - La lecture vidéo se bloque sur la boîte Selevision Andredo Le décodeur vidéo de cet appareil renvoie parfois un saut de temps de sortie important lors de la suppression de l’image vidéo du tampon de sortie, et cet horodatage de sortie reste élevé. Ce problème a été résolu en renvoyant une *profil vidéo non pris en charge* qui ne force pas le lecteur à réessayer le même profil ou à choisir un autre profil.

* Zendesk #19074 - gel des vidéos pendant FFWD et REW trick play Ce problème a été résolu en ajoutant un nouvel avertissement TRICKPLAY_ENDED_DUE_TO_ERROR pour informer l’application que le trickplay a été quitté et que la vidéo a été mise en pause en raison d’une erreur irrécupérable.

* Zendesk #19574 - TVSDK ne renvoie pas de données de réponse M3U8 pour le contenu DRM ou non DRM Ce problème a été résolu de la manière suivante :

* Zendesk #19986 - Comportement OP rompu pour certains appareils comme Android TV
* Ajout d’une erreur FILE_NOT_FOUND à la condition.
* Lorsque l’erreur provient d’une *fichier introuvable* en séparant l’URL et la réponse de la description de l’erreur si la réponse est disponible.
L’erreur logique introduite par la prise en charge d’OP par le bouclier NVidia a été corrigée. Sur les périphériques de protection non NVidia, faites confiance aux indicateurs sécurisés de l’affichage même lorsque le type d’affichage est inconnu.

* Zendesk #20549 - Manipulation de listes de lecture périmées. Ce problème a été résolu en réduisant l’intervalle entre la mise à jour du manifeste en direct à la moitié de la durée attendue du segment, si la récupération précédente ne reçoit pas de nouveaux segments.

* Zendesk #20742 - L’utilisation de la mémoire semble continuer à augmenter lors de la lecture de contenu en direct sur FireTV. Le blocage est dû à la table de référence d’objet JNI qui a atteint la limite. Ce problème a été résolu en supprimant la référence à l’objet MediaFormat créé lors du redémarrage du décodeur.

* Zendesk #21125 - Revenez de la coupure publicitaire linéaire/en direct tôt (CSAI). Ajout d’une fonctionnalité qui permet au lecteur de revenir au contenu principal au cours d’une coupure publicitaire si le lecteur enregistre la scission dans les signaux publicitaires à l’aide du détecteur d’opportunités scission.

* Zendesk #21334 - valeur du délai d’expiration de la demande d’annonce TVSDK pour la demande d’annonce tierce. Un paramètre adRequestTimeout a été ajouté à AdvertisingMetadata afin d’activer un délai d’expiration global pour l’appel de publicité.

**Version 1.4.21 (1566)**

* Zendesk #17781 - L’encapsulation d’écran ADB ne fonctionne plus Ce problème a été résolu en ajoutant l’API DefaultMediaPlayer.create(Context context, booléen secureSurface), qui permet la capture d’écran.
Pour autoriser les captures d’écran, transmettez false pour secureSurface.
Important : Nous vous recommandons vivement de ne pas activer cette fonction de capture d’écran dans un paramètre de production.

* Zendesk #19074 - Gel vidéo pendant FFWD et lecture de la astuce REW Les problèmes suivants qui se produisaient lorsque la lecture de l’astuce pouvait se figer ont été résolus :

* Zendesk #19532 - Le sous-titrage codé apparaît dans l&#39;ordre.
   * FHS commence l’exécution par flux, mais le premier segment d’iframe n’avait pas d’image dedans.
   * Lors du téléchargement d’un segment iFrame, si le FHS atteint une condition d’erreur, il quitte le flux de production et met la lecture en pause.
   * L’implémentation de MediaCodec attend indéfiniment la disponibilité de la file d’attente d’entrée lorsqu’il a été demandé de vider toutes les tampons d’entrée/sortie.
Ce problème a été résolu en inversant l’ordre des signaux WebVTT, de sorte que plusieurs signaux qui se chevauchent semblent &quot;faire défiler vers le haut&quot;.

* Zendesk #19574 - TVSDK ne renvoie pas de données de réponse M3U8 pour le contenu DRM ou non DRM Dans le chargement initial du fichier manifeste dans PTMediaPlayerItem.prepareToPlay, si le chargement échoue, TVSDK ne signale pas le corps de la réponse d’échec à l’application.
Ce problème a été résolu en permettant à TVSDK de signaler la réponse à l’échec comme une erreur à l’application.

* Zendesk #19701 - Blocage de la lecture avec SAP/Discontinuité Le blocage du lecteur lorsque le contenu audio et vidéo n’est pas aligné en cas de discontinuité a été résolu.

* Bogue #PTPLAY-11162 - La mise à jour de la bibliothèque OpenSSL vers la version 1.0.2f a été résolue.

**Version 1.4.20 (1546)**

* Zendesk #17384 - Feature Request : la prise en charge des métadonnées ID3 pour la prise en charge de la lecture AAC pour les balises ID3 dans les médias AAC a été fournie dans le TVSDK pour Android à partir de la version 1.4.20.

* Zendesk #18358 - Le lecteur gèle le commutateur à débit binaire avec des discontinuités désynchronisées Ce problème a été résolu en gérant les cas de périphérie de raccordement ABR de manière appropriée.

* Zendesk #19232 - L’application utilisant TVSDK 1.4.18 se comporte étrangement sur la version 4 antérieure d’Amazon OS. Ce problème a été résolu en supprimant la création d’affichage web masquée dans le processus d’initialisation du lecteur TVSDK afin d’éviter tout conflit avec les appareils qui ne prennent pas en charge Android Webview.

* Zendesk #19585 - Lecture à mouvement lent lorsque la transition de débit adaptatif se produit.
Lors d’un commutateur ABR, si le nouveau profil a un débit d’échantillonnage audio différent du profil actuel, la lecture devient rapide ou lente. En effet, le présentateur vidéo n’est pas informé de la modification du format audio.
Ce problème a été résolu en s’assurant que l’indicateur notify est défini au bon endroit.

* Zendesk #19683 - SAP DAI playback - Pas de son pendant quelques secondes.
Dans plusieurs cas de la logique TVSDK, lorsque l’horodatage de deux segments de rendu a été comparé, RENDITION_TIMEOUT_THRESHOLD a été utilisé comme plage de valeurs acceptable, car l’horodatage ne peut pas toujours être mis en correspondance avec une différence de 0 ms. Si l’écart se trouve dans la plage de RENDITION_TIMEOUT_THRESHOLD, l’hypothèse est qu’il s’agit d’une correspondance.

Le paramètre RENDITION_TIMEOUT_THRESHOLD a été défini sur 100 ms, mais il s’est avéré insuffisant pour certains flux. Ce problème a été résolu en augmentant à 200 ms la valeur de RENDITION_TIMEOUT_THRESHOLD .

* Zendesk #19699 - Le TVSDK ne parvient pas à basculer entre les suivis de sous-titres VTT Ce problème a été résolu en faisant le vidage du lecteur et en rechargeant le manifeste lorsqu’un suivi change et en corrigeant le problème de conversion de chaîne UTF8 qui affectait les noms de suivi de sous-titres WebVTT sur deux octets.

* Zendesk #19717 - Option CC Problème d’affichage Ce problème a été résolu en gérant correctement la chaîne Unicode.

* Zendesk #19910 - Balises TIT2 ID3 non détectées Ce problème a été résolu en fournissant une prise en charge plus complète des encodages de chaîne ID3 v2.4 et de la prise en charge de l’ID3 v2.3.

* Zendesk #20135 - TVSDK déclenche plusieurs onComplete pour le contenu VOD.
Ce problème a été résolu en ajoutant l’écouteur d’événement post_roll_COMPelete au bon endroit, au lieu de la casse complète de l’événement de changement d’état.

**Version 1.4.19 (1521)**

* Zendesk #4180 - TVSDK n’applique pas HDCP.
   * Il s’agit d’une solution partielle pour ce ticket et ne traite que le problème des périphériques de protection NVidia.
Vous devez utiliser l’API de détection HDCP correctement mise en oeuvre dans le Bouclier Nvidia pour effectuer un suivi dynamique de l’état HDCP.

* Zendesk #18358 - TVSDK gèle le changement de débit avec des discontinuités désynchronisées.
   * Ce problème a été résolu en ajoutant un nouvel avertissement pour détecter la discontinuité du PTS et en obligeant la vérification PTS à rétablir la recherche du segment correct pour chaque commutateur ABR.
Pour résoudre le blocage, l’appel de la méthode mediaPlayer.setCustomConfiguration doit inclure forcePTSCchakForABR comme argument.

* Zendesk #19038 - Pas de diffusion en direct sur Asus Zenpad 10.

  Ce problème a été résolu en préchargeant les informations du codec multimédia, de sorte que vous ne puissiez pas interroger la fonction au moment de l’exécution.

* Les problèmes suivants sont les mêmes que Zendesk #19038 :
   * Zendesk #19483 - Le TVSDK se bloque sur la plate-forme Intel.
   * Zendesk #19171 - Blocages sur Asus Memo Pad 7 avec Android 5.0.

**Version 1.4.18 (1503)**

* Zendesk #3324 - La création de rapports de publicités Primetime ne permet pas de suivre les coupures publicitaires lorsqu’il n’y a aucun média publicitaire dans un VMAP.
Lorsqu’une coupure publicitaire est vide, les événements de début et de fin de coupure publicitaire n’étaient pas en cours de ping. Ce problème a été résolu en envoyant des pings de démarrage de coupure publicitaire pour les coupures publicitaires vides, comme VMAP AdBreak, avec un noeud AdSource valide.

* Zendesk #18229 - SetCCVisiblity(VISIBLE) est ignoré après l’appel de MediaPlayer.reset() Ce problème a été résolu en ajoutant setCCVisibility(Visibility.INVISIBLE); à la fonction reset() dans la classe MediaPlayer.

* Zendesk #18328 - Problème d’image perdue sur les appareils Amazon Fire TV 2e génération pour le contenu avec 60 i/s Ce problème a été résolu en appliquant les i/s codées pour la prise de décision du temps de sommeil et avec une logique de prédiction FPS mieux codée.

**Version 1.4.17 (1472)**

* Zendesk #2231 - Erreur retournée lors de la récupération du manifeste indisponible dans MediaPlayerNotification Ce problème a été résolu en incluant le corps de réponse du manifeste en cas d’erreur d’analyse.

* Zendesk #17703 - VideoEngineView n’empêche pas les captures d’écran lors de la lecture vidéo La méthode setSecure est disponible depuis l’API 17, mais comme l’API 17 couvre les versions 4.2, 4.2.1 et 4.2.2, il n’est pas connu lequel générera une exception ou si l’appareil est spécifique. Ce problème a été résolu en plaçant VideoEngineView.setSecure dans la clause try catch.

* Zendesk #17919 - La recherche de contenu provoque une erreur de pulsation Une erreur de position des données d’entrée non valide se produisait suite à l’appel de pulsation généré lors du démarrage de la recherche après le preroll. Ce problème a été résolu.

**1.4.16a** (1454a)

* Zendesk #18215 - Certains flux AES ne peuvent pas se charger.
Ce problème a été résolu en vérifiant la taille des métadonnées DRM du profil avant de charger la clé AES.

**Version 1.4.16 (1454)**

* Zendesk #3875 - Tab S Blocages pendant la lecture Révélant la dépendance d’OKHTTP sur l’Auditude pour CRS car TVSDK utilise désormais directement httpurlconnection au lieu de curl. Le problème a été résolu en effaçant les exceptions avant d’effectuer tout autre appel JNI.

* Zendesk #4487 - Tracking du canal linéaire du contenu Le problème a été résolu en permettant la réinitialisation de l’outil de suivi de pulsation vidéo lors d’une session de lecture de flux linéaire.

* Zendesk #17919 - Android - La recherche de contenu provoque une erreur de pulsation Le problème lorsque la pulsation est dans un état d’erreur lorsqu’une recherche dans un chapitre est résolue.

* Zendesk #18053 - Adobe Primetime se bloque sur Marshmallow Le TVSDK se bloquait sur Android M OS lorsque la bibliothèque TVSDK utilisait du code neon qui convertissait les couleurs du RGB YUV. Le problème a été résolu en mettant à jour les fonctions à l’origine de ce problème à l’aide de la version non néon du code.

* Zendesk #18072 - Android M - Panne d’application Lors de la vérification de la prise en charge du profil et du niveau, un blocage se produit lors de l’appel des API MediaCodecList et MediaCodecInfo . Le problème a été résolu en fournissant une solution temporaire en chargeant toutes les informations de codec à l’avance afin d’éviter d’appeler ces API uniquement lorsque des informations de codec sont nécessaires.

* Zendesk #18074 - Les sous-titres en arabe ne fonctionnent pas sur Nexus avec Android 6.0 Le problème a été résolu en fournissant la prise en charge de la carte des polices CTS pour Android.

**Mise à jour de la version 1.4.15 (1438)**

* Zendesk #17437 - Longue durée au démarrage du contenu VOD avec certains flux AES.
Pour résoudre ce problème, si plusieurs clés sont répertoriées dans le manifeste, téléchargez toutes les clés AES en parallèle.

**Version 1.4.15 (1435)**

* Zendesk #4278 : s’étend sur les décodeurs des paramètres Android lors des changements de débit adaptatif (ABR).
Le correctif consistait à ajouter la prise en charge d’un commutateur ABR transparent avec le dernier codec multimédia Android.

* Zendesk #17063 - L’appel de mediaPlayer.reset() entraîne une erreur de réinitialisation du moteur vidéo.
Le correctif consistait à inclure le MediaErrorCode d’origine de VideoEngineExceptions lors de la distribution d’ErrorEvents.

* Zendesk #17130 - Une pause brève mais perceptible lors d&#39;un changement de débit vu sur FireTV.
(Identique à #4278 ci-dessus) Le correctif consistait à ajouter la prise en charge d’un commutateur ABR transparent avec le dernier codec multimédia Android.

* Zendesk #17666 - Autres marqueurs publicitaires, inattendus ou aucune publicité lors de la reprise de contenu.
Le correctif était un problème lors de l’exécution de prepareToPlay sur le contenu vidéo à la demande (VOD), la recherche initiale s’effectue sur l’heure locale au lieu de l’heure virtuelle.

* Zendesk #17437 - Longue durée au démarrage du contenu VOD avec certains flux AES.
Le correctif consistait à télécharger toutes les clés AES en parallèle lorsque plusieurs clés étaient répertoriées dans le manifeste.

* Zendesk #17851 - Android TV - Black Frame during ABR Le correctif consistait à spécifier KEY_MAX_WIDTH et KEY_MAX_HEIGHT pour activer la lecture adaptative.

**Version 1.4.14 (1415)**

* Zendesk #3875 - Tab S Blocages pendant la lecture.
Un correctif supplémentaire était nécessaire pour empêcher le blocage.

* Zendesk #17245 - Les secours sur Android TV ne fonctionnent pas.
Correction d’un autre problème en raison duquel la lecture se bloque lorsque la reprise est activée et que la réponse VMAP comporte une coupure publicitaire vide.

**Version 1.4.14 (1412)**

* Zendesk #17245 - Les secours sur Android TV ne fonctionnent pas.
Suppression d’une restriction pour la désactivation du reconditionnement créatif sur les annonces de secours.

**Version 1.4.13 (1388)**

* Zendesk #3502 - Prise en charge du basculement HLS basé sur le client lors d’une coupure publicitaire Autoriser le basculement vers le manifeste principal lors de la mise à jour de l’erreur de profil en direct survient pendant la période de coupure publicitaire.

* Zendesk #3875 - Blocages S de l’onglet pendant la lecture Pour résoudre le conflit entre HttpUrlConnection et cURLm, utilisez une bibliothèque tierce.

* Zendesk #4450 : problème de définition des métadonnées personnalisées pour un emplacement unique dans un résolveur de contenu Ajoutez un paramètre aux paramètres d’opportunité .

**Version 1.4.12 (1388)**

* Zendesk #2751 - CSAI et CRS | Améliorer : gérez les éléments dynamiques dans certaines URL de fichier multimédia.
Mise à jour de Creative Repackaging Service pour gérer correctement les annonces avec des URL de création dynamiques.

* Zendesk #3965 - Revenir à la lecture normale à partir de l’exécution à l’aide d’un trickplay entraîne un saut en avant avant avant de commencer la lecture.
   * Le correctif inclut TVSDK renvoyant le temps avant le changement de taux jusqu’à ce que toutes les variables soient mises à jour, au lieu d’essayer de calculer GetStreamTime.
   * Correction d’un blocage lors du changement de la vitesse de lecture des astuces près de la fin du flux.
   * Correction du calcul de l’heure actuelle lors de la lecture de l’astuce.

* Zendesk #3978 - Le trickplay 8x et 16x gèle fréquemment.
   * Sélectionnez toujours le profil de lecture de l’astuce avec le débit le plus faible pour éviter une mise en mémoire tampon constante.
   * Augmentez l’intervalle d’image de saut pour un taux de lecture de l’astuce élevé.
   * Correction d’un problème en raison duquel la mémoire tampon continue de croître après avoir atteint sa longueur cible lors de la lecture de l’astuce.

* Zendesk #3992 - Vitesses supplémentaires de Trickplay.
La fonction TrickPlay a été mise à jour afin d’accepter des taux supérieurs à 16x ; +/- 32, +/-64 et +/-128 sont désormais également autorisés.

* Zendesk #4007 - Interprétation de l’objet GEOB dans les métadonnées de la chronologie (Android et web).
Ajout de l’API setByteArray et getByteArray.

* PTPLAY-7301 - Démarrage instantané au point d’accès aléatoire.
Instant On a été mis à jour pour permettre un point de départ non nul.

**Version 1.4.11 (1363)**

* Zendesk #2076 - Souvent bloquée lors de la lecture vidéo sur Motorola Xoom avec Android 4.0.3 Ajout de périphériques à la liste autorisée pour empêcher qu’ils n’essaient de lire du contenu de profil élevé.

* Zendesk #2197 - `[Ads]` Le suivi des erreurs de publicité envoie OperationFailedEvent avec une notification d’avertissement.

* Zendesk #3304 - VAST 3.0 `[ERRORCODE]` macro non renseignée
   * le code d’erreur 400 sera révélé si la publicité intégrée comporte un contenu créatif incorrect.
   * `[ERRORCODE]` La macro sera encodée en URL

**Version 1.4.10 (1354)**

* Zendesk #2941 - Les ressources en direct n’ont pas &quot;0&quot; dans la plage pouvant faire l’objet d’une recherche Auparavant, il existait un tampon de segment 3 lors de la recherche au début d’un flux en direct. Il est désormais possible de rechercher jusqu’au tout début d’un flux en direct (c’est-à-dire le début du premier segment).

* Zendesk #3169 - Mise à jour du lecteur de référence avec l’intégration d’Adobe Analytics : le lecteur de référence a été mis à jour avec la bibliothèque Adobe Analytics comme exemple d’implantation.
* Zendesk #3299 - Comportement inexplicable de jeux de fiction
   * Correction d’un bogue en raison duquel le retour à l’état de lecture après l’arrêt de la lecture du tour pouvait prendre plusieurs secondes (parfois 25 secondes ou plus).
   * Correction d’un bogue en raison duquel l’appel d’une astuce était relu une seconde fois sur le même média, ce qui entraînait le gel du flux à l’heure actuelle.
* Zendesk #3433 - Android et Flash - Problèmes avec les sous-titres

GetLine pour WebVTT ne respectait pas un &lt;cr>&lt;lf> longueur ajustée d’un paquet ; la dernière légende peut contenir des caractères des légendes précédentes.

* PTPLAY-6243 - Amélioration du lecteur de référence pour capturer les informations de débogage

Les exemples de lecteurs de référence Android ont été améliorés avec une option permettant d’activer les journaux de débogage et d’envoyer les résultats par courriel. Cette option se trouve sous le menu Journal dans le lecteur de référence.

**Version 1.4.9 (1332)**

* Zendesk #2649 - La fin de la mémoire tampon survient avant que la mémoire tampon initiale ne soit pleine

Après une recherche, cas où le moteur vidéo définit l’état sur LECTURE avant que le présentateur vidéo ne soit prêt à être lu. Se produit lorsque l’état de mémoire tampon est élevé avant la recherche. Correction en avertissant le moteur vidéo de l’état de mémoire tampon faible. Avec le moteur vidéo dont l’état de mémoire tampon est faible, l’appel de Play entraîne la modification de l’état à la mise en MÉMOIRE TAMPON au lieu de LECTURE. La lecture reprend lorsque l’état devient LECTURE.

* Zendesk #2846 - Demande d’amélioration : permet de définir différentes chaînes agent-utilisateur pour les appels effectués par la bibliothèque Auditude.

Une nouvelle API a été ajoutée pour définir l’agent utilisateur pour les appels liés aux publicités, auditudeSettings.setUserAgent(&quot;user/agent&quot;). Si aucun agent utilisateur n’est défini, la valeur par défaut est utilisée. Cela affecte uniquement l’agent utilisateur pour les appels liés aux publicités. L’agent utilisateur pour les appels médias reste inchangé, c’est-à-dire &quot;Adobe Primetime&quot;+.&lt;default useragent=&quot;&quot;>.

**Version 1.4.8 (1324)**

* Zendesk #1218 - 106000.33 Erreur avec local ... Si le chargement du manifeste dans FragmentedHTTPStreamer::ThreadParseManifest() échoue, vérifiez si le domaine d’URL est localhost et, dans l’affirmative, remplacez le domaine par 127.0.0.1 et rappelez ThreadParseManifest.
* Zendesk #3072 - Passage automatique à des débits inférieurs. Modification du calcul de la longueur de la mémoire tampon afin d’ignorer la charge utile PTS zéro.
* Zendesk #3168 - Les sous-titres WebVTT ne s’affichent que pour les 10 premières secondes.
* Zendesk #3193 - La demande d’une API de changement de profil dans TVSDK, PlaybackEventListener.onProfileChanged() a été ajoutée.

**Version 1.4.7 (1311)**

* Zendesk #2197 - Tracking des erreurs de publicité. Ajout d’une notification pour l’échec du chargement du manifeste
* Zendesk #2575 - PSDK ignore la publicité MARK personnalisée en continu avant la vidéo
* Zendesk #2719 - Win Death with auditude ads (Gagner la mort avec publicités audacieuses), fixed beacon tracking (suivi fixe des balises lorsqu’elle est redirigée vers l’URL relative dans le module externe auditude)
* Zendesk #2760 - balise DISCONTINUITY ignorée pendant le mode TrickPlay
* Zendesk #2805 - Joueur en panne au début de la lecture, même correction que Zendesk #2719
* Zendesk #2817 - Lecteur Android - Le lecteur se bloque et arrête parfois la lecture, corrigé en étendant les tampons de décodage de 2.0 à 3.0 secondes.
* Zendesk #2839 - Adobe Primetime PSDK prend-il en charge les chipsets ARMv8 ?, ajout d&#39;un correctif pour le blocage trouvé sur Galaxy S6.
* Zendesk #2885 - Auditude Lecture de blocage, même correction que Zendesk #2719
* Zendesk #2895 - Échec de Live HLS systématiquement après 10 minutes de lecture
* Zendesk #2925 - Commentaires concernant le build de développement Android (1.4.5), sur certains appareils lorsque nous mettons le paquet en file d’attente dans la file d’attente d’entrée, si le PTS est négatif, le décodeur passe dans un état bizarre où nous obtenons toujours un PTS de sortie négatif pour les paquets futurs. Le correctif définit le PTS d’entrée sur zéro s’il est négatif pour éviter ce problème.
* PTPLAY-4645 - Désactivez la prise en charge du chiffrement RC4 dans openssl. Il existe des exploits connus pour RC4. En d’autres termes, si une tentative de connexion à un serveur prenant uniquement en charge RC4 est effectuée, elle échoue.

**Version 1.4.6 (1282)**

* Zendesk #2192 - Le débit ne diminue pas toujours dans de mauvaises conditions réseau, corrigées par la suppression de l’implémentation de commutation rapide.
* Zendesk #2631 - Sous-titres en arabe sur Android : le texte sur plusieurs lignes apparaît coupé, corrigé par l’ajustement de la taille des polices pour les polices arabes.
* Zendesk #2844 - La mise en mémoire tampon sur la note 4 et le temps de téléchargement des fragments ne sont pas précis.

Ce problème a été corrigé en ajoutant une latence entre les téléchargements de segments vidéo dans le calcul de la bande passante et en configurant la logique de calcul du temps de téléchargement pour utiliser le temps de cycle de requête complet.

* Zendesk #2908 - Les sous-titres arabes ne fonctionnent pas sur les 5, 6 et 7 novembre, corrigés par l’ajout de 2 polices de remplacement supplémentaires pour les scripts arabes.
* PTPLAY-4627 - Mise à jour de l’appsdk Nielson vers la version 1.2.3.7
* PTPLAY-5084 - Prise en charge du basculement de mise à jour du manifeste de Principal en direct

**Version 1.4.5 (1248)**

* Zendesk #1757 - Seul le contenu audio lu ou les blocages du lecteur pour un profil de débit vidéo, le blocage de Nexus 4 et Nexus 7 a été corrigé.
* Zendesk #2072 - TimedMetadata pour AdEvent ne contient pas d’URL complète simplement &quot;http&quot;
* Zendesk #2192 - Le débit n&#39;est pas toujours plus faible dans de mauvaises conditions de réseau
* Zendesk #2256 - Accès à la liste de lecture des Principal, mise à jour du PSDK pour distribuer des événements timedMetadata pour les balises inscrites sur la liste de lecture principale.
* Zendesk #2269 - Deux langues de sous-titres différentes apparaissent à l’écran en même temps que WebVTT.
* Zendesk #2417 - Lecteur tentant de télécharger des sous-titres avant le début de la lecture, WebVTT utilisait une variable de numéro de segment incorrecte pour la correspondance de numéro de segment. Le bogue s’affichait uniquement pour les médias dont les index de segment commençaient à zéro.
* Zendesk #2470 - PSDK ne revient pas de l’état SUSPENDU lorsque le changement de débit se produit après la suspension. Dans une situation spéciale, lorsque la recherche dynamique est appelée par RestoreGPUResource (restaurer le lecteur à partir de l’état de suspension) et que le commutateur de diffusion est détecté avant, la recherche dynamique ne peut pas se terminer et entraîne une mise en mémoire tampon constante.
* Zendesk #2451 - Sous-titrage codé &#39;bottom inset&#39;, ajout du paramètre &#39;bottomInset&#39; au code de sous-titrage
* Zendesk #2480 - désactivation de l’optimisation de la redirection HTTP 302, prise en charge supplémentaire pour la définition de la propriété useRedirectUrl
* Zendesk #2486 - Balises tierces
* Zendesk #2547 - Sous-titres en arabe : le texte doit être aligné à droite

**Version 1.4.4 (1195)**

* Zendesk #1158 - Échec de la lecture sur Huawei Valiant (Y301A1)
* Zendesk #1709 - Taille de média incorrecte et vidéo étirée
* Zendesk #1757 - Lecture audio uniquement après le changement de profil entre les diffusions avec des données spa/pps identiques
* Zendesk #2095 - État HTTP 307 (redirection) entraînant l’arrêt de la lecture par le lecteur Adobe
* Zendesk #2126 - Absence de l’événement TimedMetaData pour le dernier ADEVENT, les balises abonnées qui existent après le dernier segment n’ont pas été signalées au PSDK à partir d’AVE.
* Zendesk #2227 - Verrouillages dans VideoEngine nativeReset et nativePause
* Bogue #3921755 - Mise à jour de la bibliothèque OpenSSL vers la version 1.0.1L

**Version 1.4.3 (1173)**

* Zendesk #1591 - RENDITION_M3U8_ERROR
* Zendesk #1870 - Sous-titrage codé Activé/Désactivé
* PTPLAY-1818 - Rétablissez les taquets de lecture au niveau de la publicité au lieu de revenir au-delà.
* PTPLAY-2736 - Une légende WebVTT précédemment affichée s’affiche à l’écran lorsqu’un flux avec une légende WebVTT se termine en lecture.
* PTPLAY-3773 - Une publicité mid-roll n’est pas lue lorsque la lecture de flux est lancée après la position de la publicité.

**Version 1.4.2**

* Zendesk #1561 - Prise en charge du basculement client HLS en prime time. Utilisera la date et l’heure du programme pour résoudre le basculement
* Zendesk #1590 - LoadInfo.MediaDuration est toujours 0 (non fixe pour audio uniquement)
* Zendesk #1626 - Fuite de mémoire potentielle dans le lecteur. Pas de fuite de mémoire réelle, le problème était lié à l’enregistrement de l’historique des notifications des 1 000 dernières notifications. Ce problème a été réduit à 100.
* Zendesk #2192 - Le débit n&#39;est pas toujours plus faible dans de mauvaises conditions de réseau

**Version 1.4.1 (1121)**

* Zendesk #1951 - Verrouillage dans VideoEngine.nativeReset() sur les appareils 4.0.x
* Zendesk #2064 - Native Crash SIGSEGV sur des appareils Android spécifiques basés sur un intel
* Zendesk #2075 - Lockup in VideoEngine.nativeReleaseGPUResource sur les appareils 4.0.x Remarque : Cette version est &#42;&#42;&#42;required&#42;&#42;&#42; pour la prise en charge d’Android 5.0 (Lollipop)
* Zendesk #1513 - Prise en charge d’Android Lollipop
* Zendesk #1709 - Taille de média incorrecte et vidéo étirée
* Zendesk #1871 - Les sous-titres WebVTT disparaissent parfois puis réapparaissent lors de l’affichage d’un flux en direct avec des sous-titres WebVTT.
* Zendesk #1996 - Aucun marqueur de chronologie n’est visible dans PSDK 1.4.0
* Zendesk #2046 - Blocage avec PSDK 1.4.1.1113, blocage corrigé pour les diffusions en direct lorsqu’aucune publicité n’est renvoyée par auditude
* Bogue #3769657 - Mise à jour de la version de curl vers 7.38.0
* PTPLAY-1575 - Lorsque la lecture ABR commence avec un flux audio uniquement, puis passe à la diffusion audio/vidéo, la vidéo ne s’affiche jamais pendant que la lecture audio se poursuit.
* PTPLAY-2499 - Mise à jour d’OpenSSL vers la version 1.0.1j pour répondre aux vulnérabilités récentes
* PTPLAY-2632 - La vidéo ne se rétablit pas après la fin de la publicité mid-roll sur Android Lollipop.
* PTPLAY-2678 - Blocages vidéo pendant les tests de longévité en direct sur Android Lollipop

**Version 1.4.0**

* Zendesk #1024 - Fonctionnalité de suppression de la publicité du flux via le manifeste
* Zendesk #1293 - Problème de sélection du suivi des sous-titres codés.
* Zendesk #1590 - LoadInfo.MediaDuration est toujours 0, mediaDuration affiche désormais la valeur correcte.
* Zendesk #1629 : le lecteur/l’application se bloque à la fin de la lecture de la publicité sur Galaxy S4
* Zendesk #1674 - ClosedCaption Non affiché, la légende 708 correcte s’affiche lorsque les codes ETX 0x03 sont manquants.
* PTPLAY-2157 - Les styles de sous-titrage codé par défaut étaient renvoyés par les accesseurs, même si des styles différents avaient été définis et vérifiés visuellement sur le flux. Les propriétés de style Sous-titrage codé affichent désormais la valeur sur laquelle elles ont été définies.

## Problèmes connus dans la version 1.4 {#known-issues-in}

**Version 1.4.31**

* PTPLAY-16803 - Le sous-titrage codé ne fonctionne pas avec le contenu audio uniquement, car le système de sous-titrage a besoin de vidéo pour fonctionner. Sans vidéo, il n’y a pas de dimension de fenêtre d’affichage et sans dimension de fenêtre d’affichage, nous ne pouvons pas afficher de graphiques pour les sous-titres.
* PTPLAY-1634 - La même balise d’abonnement comporte différents horodatages dans différentes fenêtres en direct. Lorsque la fenêtre active se déplace, la même balise doit avoir les mêmes horodatages. Cependant, il arrive parfois que les mêmes balises aient des horodatages différents.
* PTPLAY-3197 - Blocage avec le signal 11 SIGSEGV sur l’appareil Acer Iconia après environ 1 heure de lecture continue
* PTPLAY-3310 - Avec un débit audio plus faible, le son devient bouché/bouché sur Acer Iconia.
* PTPLAY-3355 - Blocage de la MORT WIN sur Motorola Xoom avec 4.0.x après environ 1 heure de lecture continue.
* PTPLAY-3557 - Le redécoupage lors d’une coupure publicitaire entraîne la fin du flux.
* PTPLAY-7079 - La fenêtre de lecture sur le client Android ne fonctionne pas avec Arrêt/Arrêt sécurisé
* Bogue #3760144 - La résolution peut se déplacer ou sembler prendre du pouls lorsque la diffusion est mise en pause sur certains appareils tels que Kindle Fire 7 et Samsung Galaxy Nexus. Uniquement observable sous contrôle serré
* Bogue #3761170 - searchToLocal en direct avec des publicités ne peut pas effectuer de recherche en amont dans le contenu publicitaire, il est préférable d’utiliser les API currentTime pour les diffusions en direct.
* Bogue #3763370 - Les diffusions en direct avec des publicités affichent parfois deux marqueurs de publicité qui se rapprochent lorsqu’il ne doit y en avoir qu’un seul. Ces marqueurs publicitaires représentent la même publicité, et un seul affichera
* Bogue #3763373 - Le marqueur de publicité peut brièvement disparaître lors de la recherche au-delà d’une publicité dans les flux VOD. Le marqueur de publicité est restauré et aucun autre effet négatif n’est affecté sur la chronologie.
* Certains périphériques ont des problèmes de lecture connus. Voir [Problèmes de périphérique connus dans la version 1.4](https://helpx.adobe.com/primetime/release-notes/tvsdk-1-4-android.html#Knownissuesin14).
* Implémentation de référence : la lecture de marque n’est pas implémentée dans l’exemple d’application.
* Sur certains appareils Android TV, une image noire est visible en raison d’une réinitialisation du décodeur aux points de transition suivants :
   * en mode tricplay et en dehors
   * basculement entre des pistes audio à liaison différée
   * d&#39;une publicité au contenu principal.

**Version 1.4.23**

* Le sous-titrage codé ne fonctionne pas avec le contenu audio uniquement, car le système de sous-titrage a besoin d’une vidéo pour fonctionner. Sans vidéo, il n’y a pas de dimension de fenêtre d’affichage et sans dimension de fenêtre d’affichage, vous ne pouvez pas afficher de graphiques pour les sous-titres.
* À compter de la version 1.4.23, TVSDK ne prendra plus en charge Gingerbread OS 2.3. Cela est dû au fait que TVSDK a utilisé les bibliothèques Android privées suivantes pour collecter des informations matérielles sur les appareils avec Gingerbread OS :

   * `libstagefright.so`
   * `libcutils.so`

Dans la version Android N, Google a supprimé l’accès à ces bibliothèques privées. Le système d’exploitation Gingerbread représente actuellement moins de 1 % de la part de marché d’Android OS dans le monde, de sorte qu’après la version 1.4.23, le système d’exploitation Gingerbread ne sera plus pris en charge par TVSDK.
Lorsque vous utilisez la version 1.4.23 (qui inclut la prise en charge d’Android N) ou une version ultérieure :
* Mettez à jour vos applications pour utiliser la version 11 de minSdkVersion.
* Si votre utilisateur final exécute OS 2.3, la version du SDK est inférieure à la version minSdkVersion de l’application. Le système interrompt l’installation ou la mise à niveau de l’application.
* Si votre utilisateur final exécute une version supérieure à OS 2.3, l’application sera installée correctement.

Si vous mettez à jour minSdkVersion :

* Si votre utilisateur final exécute OS 2.3, l’application est installée, mais la lecture ne fonctionne pas.
Cela s’applique à la mise à jour et à la nouvelle installation.
* Si votre utilisateur final exécute un système supérieur à OS 2.3, l’application est installée correctement et le contenu est lu correctement.

**Version 1.4.22**

* La sortie anticipée des publicités ne fonctionne pas avec certaines des publicités mid-roll lorsque les balises s’éloignent trop les unes des autres.

**Version 1.4.2**

* Le retour en arrière lors d’une coupure publicitaire entraîne la fin du flux.

Le lecteur multimédia envoie de manière incorrecte MediaPlayerState.Complete lors de l’opération de rembobinage de lecture lorsqu’il atteint la limite de la publicité. Le lecteur doit ignorer cet événement lorsqu’il est en mode de lecture de l’astuce, sinon le SDK gère correctement l’état.

**Version 1.4.0 (1086)**

* PTPLAY-1634 - La même balise Abonnée comporte différents horodatages dans différentes fenêtres actives. Lorsque des fenêtres actives se déplacent, la même balise dans chacune d’elles doit avoir les mêmes horodatages. Cependant, parfois, même les mêmes balises ont des horodatages différents.
* PTPLAY-2541 - COMPONENT_CREATION_FAILURE est parfois détecté après plusieurs pannes de courant vers/depuis le flux alternatif.
* Bogue #3726865 - Si un flux LBA à débit multiple commence à partir d’un flux audio uniquement, la vidéo ne s’affichera pas si vous passez à un flux audio/vidéo. Le démarrage à partir d’un flux audio/vidéo n’affiche pas ce problème et peut passer d’une diffusion audio/vidéo à une diffusion audio/vidéo.
* Bogue #3760144 - La résolution peut se déplacer ou sembler prendre du pouls lorsqu’un flux est mis en pause sur certains appareils tels que Kindle Fire 7 et Samsung Galaxy Nexus. Uniquement observable sous contrôle serré
* Bogue #3761170 - searchToLocal en direct avec des publicités ne peut pas effectuer de recherche en amont dans le contenu publicitaire ; il est préférable d’utiliser les API currentTime pour les diffusions en direct.
* Bogue #3763370 - Les diffusions en direct avec des publicités affichent parfois deux marqueurs de publicité qui se rapprochent lorsqu’il ne doit y en avoir qu’un seul. Ces marqueurs publicitaires représentent la même publicité, et un seul affichera
* Bogue #3763373 - Le marqueur de publicité peut brièvement disparaître lors de la recherche au-delà d’une publicité dans les flux VOD. Le marqueur de publicité est restauré et aucun autre effet négatif n’est affecté sur la chronologie.
* Certains périphériques ont des problèmes de lecture connus. Pour plus d’informations, voir [Problèmes de périphérique connus dans la version 1.4](https://helpx.adobe.com/primetime/release-notes/tvsdk-1-4-android.html#Knownissuesin14).
* Implémentation de référence : la lecture de l’aperçu n’est pas implémentée dans l’exemple d’application.

## Problèmes de périphérique connus dans la version 1.4 {#known-device-issues-in}

| Appareil | Chipset | Problème | Cause | Solution |
|--- |--- |--- |--- |--- |
| Droid X | TI OMAP3 | Le délai ABR est attendu depuis le redémarrage du décodeur. |  |  |
| HTC Desire (différent de HTC Desire HD) | QSD8250 | Impossible de lire la vidéo. Renvoie l’erreur VIDEO_PROFILE_NOT_SUPPORTED . | Le désir ne fournit pas de décodeur de guerre du matériel approprié. Il donne le décodeur SW de Stagefright. | Redémarrez le périphérique. |
| HTC EVO 4G | QSD8650 | Aucun décodeur HW. | Qualcomm n’a pas de décodeur HW. | Mise à niveau vers Android 4.x. |
| Kindle FireSystem version 6.0 | TI OMAP4 | Ne lit pas les flux HLS. La vidéo sur AIR ne fonctionne pas. |  | Mise à niveau vers la version 6.3 du système. |
| Kindle Fire HD | TI OMAP4 | Peut entrer dans un état où il ne peut pas lire de vidéo. Renvoie les erreurs VIDEO_PROFILE_NOT_SUPPORTED et UNRECOVERABLE_ERROR . | Le décodeur HW se retrouve dans un état irrécupérable lorsque l’application n’arrête pas entièrement le décodeur HW, par exemple après avoir rencontré un blocage. Se produit également sur les applications natives de l’appareil. | Redémarrez l’appareil. |
| Kindle Fire HD 8.9 | Snapdragon 800 | AVE se bloque après plusieurs commutateurs ABR. |  |  |
| Motorola | Tegra2 | Problèmes de performances généraux avec AVE par opposition à AIR. L’audio/la vidéo est hors synchronisation, la lecture vidéo se fige après lecture entre 9 et 15 minutes. Blocages. | Peut-être lié à openGLES que nous activons sur AIR. En cours d&#39;enquête. |  |
| Nexus 7 (2e génération) | S4Pro APQ8064 (Qualcomm) | L’appareil se bloque lorsqu’un film est mis en pause pendant plus de 30 minutes. | Problème de périphérique signalé à Google. | L’application doit expirer afin de ne pas autoriser un état de pause long. |
| Nexus S (GB) | Humming Bird | Impossible de lire une vidéo à l’aide du décodeur HW. | Il n’existe pas de décodeur HW basé sur Stagefright dans Nexus S. Pour Android 2.3, nous utilisons donc un décodeur SW. | Effectuez la mise à niveau vers ICS. |
| Nexus S (ICS) | Humming Bird | La vidéo scintille parfois. | Des données incorrectes peuvent entraîner un mauvais état du décodeur. | Redémarrez l’appareil. |
| Tablette Nook Android OS : 2.3 | TI OMAP 4 | La vidéo ne se joue pas et l’application se bloque. | Le Stagefright entre dans un état instable après avoir exécuté l’application plusieurs fois. Appels à mediaplayer::QueryCodecs sont suspendus. | Redémarrez l’appareil pour réinitialiser l’état. |
| Samsung Galaxy ACE | Qualcomm MSM7227 | Impossible d’installer l’application SampleMediaPlayer. | Utilise ARM v6 au lieu du jeu de puces ARM v7 le plus courant. FP/AIR ne prend pas en charge cet appareil. |  |
| Samsung Galaxy ACE2Android OS : 2.3.6 | NovaThor U8500 | Impossible de lire la vidéo. | Ce jeu de puces est un décodeur inconnu pour Android pre-ICS dans AVE. |  |
| Samsung Galaxy S2 (GT-I9100) | Exynos | Les performances vidéo ne sont pas à la hauteur pour cet appareil. | Le décodeur HW renvoie des cadres décodés avec le mauvais système de traitement de texte (PTS). Il semble que le décodeur utilise le temps de décodage plutôt que le temps de présentation. |  |
| Samsung Galaxy S2 GAndroid OS : 2.3.6 | TI OMAP4 | Blocages lors du démarrage de la vidéo. |  | Mise à niveau vers Android 2.3.7 ou 4.x. |
| Samsung Galaxy S3 (I747) | Qualcomm MSM8960 | Par intermittence, la vidéo se bloque et seul le son est lu, puis ne répond plus. |  |  |
| Samsung Galaxy S3 I747M | SAMSUNG_M2ATT | La vidéo gèle. | Enquêter. |  |
| Samsung Galaxy Tab 1 v10.1 | Tegra 2 | La transition MBR peut prendre jusqu’à trois secondes. | Comme correctif pour les blocages MBR, nous redémarrons le décodeur pour chaque commutateur de diffusion, qui peut prendre jusqu’à trois secondes. |  |
| Samsung Galaxy Y |  | Impossible d’installer l’application SampleMediaPlayer. | Utilise ARM v6 au lieu du jeu de puces ARM v7 le plus courant. FP/AIR ne prend pas en charge cet appareil. |  |
| Xoom | Tegra | Quelques images sont perdues pour le changement. Le décodeur n’est pas redémarré. | Limitation OMXALE. |  |

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://helpx.adobe.com/support/primetime.html) page.
