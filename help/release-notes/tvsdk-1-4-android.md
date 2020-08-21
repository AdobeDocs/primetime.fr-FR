---
title: Notes de mise à jour de TVSDK 1.4 pour Android
seo-title: Notes de mise à jour de TVSDK 1.4 pour Android
description: Les Notes de mise à jour de TVSDK 1.4 pour Android décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus et les problèmes de périphérique dans TVSDK Android 1.4.
seo-description: Les Notes de mise à jour de TVSDK 1.4 pour Android décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus et les problèmes de périphérique dans TVSDK Android 1.4.
uuid: 8bd8ee42-7a1b-4c14-aad9-22804743e505
contentOwner: asgupta
products: SG_PRIMETIME
topic-tags: release-notes
discoiquuid: f1ebc1a8-185a-493a-9c00-a6102dffb128
translation-type: tm+mt
source-git-commit: 6da7d597503d98875735c54e9a794f8171ad408b
workflow-type: tm+mt
source-wordcount: '7830'
ht-degree: 0%

---


# Notes de mise à jour de TVSDK 1.4 pour Android {#tvsdk-for-android-release-notes}

Les Notes de mise à jour de TVSDK 1.4 pour Android décrivent ce qui est nouveau ou modifié, les problèmes résolus et connus et les problèmes de périphérique dans TVSDK Android 1.4.

## Nouvelles fonctionnalités {#new-features}

**Version 1.4.43**

**Chargement sécurisé des publicités via HTTPS**

adobe primetime offre une option permettant de demander un premier appel au serveur d’annonces avant la date limite et au serveur CRS via HTTPS.

**alwaysUseAudioOutputLatency(valeur booléenne) dans la classe MediaPlayer**

Lorsque ce paramètre est défini, utilisez la latence de sortie audio dans le calcul de l’horodatage audio.

Il accepte une valeur de paramètres booléens. Si sa valeur est `True`définie, le client utilise la latence de sortie audio dans le calcul de l’horodatage audio.

**Version 1.4.42**

**Insertion publicitaire partielle :**
Expérience TV consistant à se joindre au milieu d’une publicité sans déclencher le suivi de la publicité partiellement visionnée.
Exemple : L’utilisateur se joint au milieu (à 40 secondes) d’une coupure publicitaire de 90 secondes composée de trois publicités de 30 secondes. Ceci est 10 secondes après la seconde publicité pendant la coupure.
* La seconde publicité est lue pour la durée restante (20 s), suivie de la troisième publicité.
* Les suivis publicitaires pour la publicité partielle lue (deuxième publicité) ne sont pas déclenchés. Les suivis de la troisième publicité seulement sont déclenchés.

**Version 1.4.41**

Aucune nouvelle fonctionnalité.

**Version 1.4.40**

Aucune nouvelle fonctionnalité.

>[!NOTE]
>
>Vous n’aurez pas besoin des modifications d’API si vous utilisez une version antérieure à la version 1.4.39.

**Version 1.4.39**

* TVSDK est certifié avec VHL 2.0.1 et avec VHL 2.0.1 avec Nielsen.
* Android TVSDK est mis à jour afin d’envoyer des requêtes CRS du nouvel hôte Akamai `primetime-a.akamaihd.net`.
* La nouvelle configuration du nom d’hôte fournit une diffusion de ressources CRS via HTTP et HTTPS (SSL) à plus grande échelle.
* TVSDK prend en charge la version Android Oreo.
* Une nouvelle fonction est ajoutée à la `AdClientFactory` classe pour prendre en charge l&#39;enregistrement de plusieurs détecteurs d&#39;opportunités :

   ```
   public List<PlacementOpportunityDetector> createOpportunityDetectors(MediaPlayerItem item);
   ```

   Ceci doit renvoyer un tableau de PlacementOpportunityDetector. Vous pouvez désormais enregistrer plusieurs détecteurs d&#39;opportunités. Par exemple, pour la fonctionnalité de sortie anticipée d’une publicité, deux détecteurs d’opportunités étaient requis : un pour l’insertion d’une publicité et un autre pour la sortie anticipée de la publicité. Vous devez implémenter cette nouvelle fonction uniquement si vous avez mis en oeuvre votre propre AdvertisingFactory (et n’utilisez pas DefaultAdvertisingFactory). Pour obtenir le comportement existant, vous devez créer un seul Détecteur d&#39;opportunité, comme dans la fonction createOpportunityDetector() , le placer dans un tableau et le renvoyer :

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
>Vous n’aurez pas besoin des modifications d’API si vous utilisez une version antérieure à la version 1.4.39.

**Version 1.4.36**

Correction de bogues pour l’option Ignorer le contenu sous Android.

**Version 1.4.35**

* **Informations sur les publicités réseau**

   Les API TVSDK fournissent désormais des informations supplémentaires sur les réponses VAST tierces. L’identifiant de publicité, le système d’annonces et les extensions d’annonce VAST sont fournis dans la classe NetworkAdInfo accessible par le biais de la propriété networkAdInfo sur une ressource d’annonce. Ces informations peuvent être utilisées pour l’intégration à d’autres plates-formes d’analyses des publicités, telles que **Moat Analytics**.

**Version 1.4.31**

**Prise en charge multiCDN pour les annonces CRS**
* Par défaut, toutes les ressources transcodées sont hébergées sur le réseau de diffusion de contenu détenu par l’Adobe sur Akamai. Avec la dernière version, Adobe Creative Repackaging Service (CRS) permet de télécharger les éléments créatifs transcodés sur plusieurs réseaux de diffusion de contenu selon les spécifications du client.
* De nouvelles API sont ajoutées à TVSDK pour permettre la spécification de l’URL créative CRS finale lorsque l’URL par défaut n’est pas utilisée. Consultez la documentation pour savoir comment utiliser ces nouvelles API.

**La version 1.4.18 de** Primetime TVSDK Android prend désormais en charge les éléments créatifs JavaScript VPAID 2.0 pour permettre une expérience de publicité interactive enrichie en continu. Pour plus d’informations sur VPAID 2.0, voir Prise en charge [des annonces](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/vpaid-ads/android-3x-vpaid-ads.md)VPAID.

**Version 1.4.17**

AC-3 5.1 est uniquement pris en charge sur Amazon FireTV.

**Version 1.4.11**

* **Retrait de publicité, chaînage de publicités dans la logique de sélection des publicités (Zendesk #3103** Pour les publicités VAST (créatifs) avec la règle de secours activée, TVSDK traite une publicité avec un type MIME non valide comme une publicité vide et tente d’utiliser des publicités de secours à sa place. Vous pouvez configurer certains aspects du comportement de secours.

Pour plus d’informations, voir Reprise [publicitaire pour les annonces VAST et VMAP](../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-fallback/android-3x-ad-fallback.md).

* **Mise à jour de la bibliothèque Video Heartbeats Library (VHL) vers la version 1.5**
   * Capacité d’envoyer des métadonnées avec un début vidéo et/ou un début vidéo/publicitaire/chapitre en tant que données contextuelles
   * Moins de trafic réseau - Les pulsations sont moins nombreuses en moyenne et de taille plus petite

**Version 1.4.7**

* **Prise en** charge de l’individualisation sur sitePrise en charge des installations sur site de l’Adobe Individualization Server pour personnaliser la demande d’individualisation du client afin d’accéder à un autre point de terminaison.

**Version 1.4.6**

* **Exemple de chiffrement AES (nécessite la version 17.0.0.134 du Flash Player)**Exemple de chiffrement AES pris en charge.

**Version 1.4.2**

* **Mise à jour de la bibliothèque Video Heartbeats Library (VHL) vers la version 1.4.0.1**

   * ajouté la possibilité de regrouper différents cas d’utilisation des analyses, provenant d’autres kits SDK ou lecteurs, avec Adobe Analytics Video Essentials.
   * Le suivi des publicités a été optimisé en supprimant les méthodes trackAdBreakStart et trackAdBreakComplete. La coupure publicitaire est déduite des appels des méthodes trackAdStart et trackAdComplete.
   * La propriété playhead n’est plus nécessaire lors du suivi des publicités.

* **Intégration** du SDK NielsenLe SDK TVSDK prend désormais en charge l’envoi d’informations de suivi d’utilisateur au SDK Nielsen sans intégration personnalisée.

**Version 1.4.0**

* **Signalisation par coupure de courant avec remplacement** de contenu alternatif Dans le cadre de la mise à jour TVSDK 1.4, TVSDK prend également en charge la prise en charge et le retour des coupures régionales par rapport au contenu linéaire. TVSDK peut maintenant traiter deux fichiers manifestes en parallèle, principal et alternatif, pour surveiller les signaux d&#39;arrêt même lorsque la programmation alternative est présentée à la programmation originale.

* **Supprimez/Remplacez les publicités** C3 Maintenant, aucune préparation supplémentaire n’est nécessaire pour insérer dynamiquement de nouvelles publicités dans les ressources vidéo à la demande (VOD) qui sortent de la fenêtre C3. TVSDK fournit désormais une API permettant de supprimer des plages de contenu personnalisées et d’insérer dynamiquement de nouvelles publicités. Cette nouvelle fonctionnalité puissante est également utile dans les cas où du contenu en direct/linéaire est diffusé pendant la diffusion et est immédiatement retiré pour être utilisé comme contenu à la demande sans le temps nécessaire pour &quot;nettoyer&quot; la ressource.

* L&#39;interface PlaybackEventListener comporte une nouvelle méthode appelée onReplaceMediaPlayerItem, que vous pouvez utiliser pour écouter un nouveau événement, `ITEM_REPLACED`. Ce événement est distribué chaque fois qu’une instance MediaPlayeritem est remplacée sur MediaPlayer. L’application cliente qui implémente ce PlaybackEventListener doit implémenter ou remplacer cette nouvelle méthode.
* AdClientFactory a une nouvelle fonction ajoutée à la classe pour s&#39;inscrire à plusieurs détecteurs d&#39;opportunités :

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

## Modifications apportées à TVSDK pour la version 1.4 {#tvsdk-changes}

* L’interface PlaybackEventListener comporte une nouvelle méthode appelée onReplaceMediaPlayerItem, que vous pouvez utiliser pour écouter un nouveau événement, ITEM_REPLACED. Ce événement est distribué chaque fois qu’une instance MediaPlayeritem est remplacée sur MediaPlayer. L’application cliente qui implémente ce PlaybackEventListener doit implémenter ou remplacer cette nouvelle méthode.

* AdClientFactory a une nouvelle fonction ajoutée à la classe pour s&#39;inscrire à plusieurs détecteurs d&#39;opportunités :

```
public List`<PlacementOpportunityDetector>` createOpportunityDetectors(MediaPlayerItem item);
```

Par exemple, pour la fonctionnalité de sortie anticipée d’une publicité, vous avez besoin de deux détecteurs d’opportunités : l’un pour l’insertion d’une publicité et l’autre pour la sortie anticipée de la publicité.

Pour remplacer cette nouvelle fonction, créez un seul Détecteur d&#39;opportunité, puis placez-le dans un tableau et renvoyez :

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
>Les fonctionnalités suivantes **ne sont pas** prises en charge dans TVSDK :
>
>* Mouvement lent, sur n’importe quelle plate-forme ou version.
>* Jeu de ficelles en direct.


**Version 1.4.43**

TVSDK 1.4.43 a été certifié avec les périphériques Android dotés d’Android 6.0.1/ 7.0 et 8.1 (Oreo).

* **Version 1.4.23 :**

   * TVSDK 1.4.23 a été certifié pour les périphériques Android avec Android N.

* **Version 1.4.18 :**

   * Primetime a été certifié pour Amazon Fire TV.
   * VPAID 2.0 est pris en charge uniquement sur les appareils dotés d’Android 4.0 et versions ultérieures.

## Problèmes résolus dans la version 1.4 {#resolved-issues-in}

>[!NOTE]
>
>Tous les clients TVSDK qui utilisent CRS sont fortement encouragés à effectuer la mise à niveau vers TVSDK 1.4.39 ou version ultérieure sur iOS et Android. Cette mise à niveau remplace la mise en oeuvre de l’application existante. Après la mise à niveau, recherchez les demandes d’URL créatives CRS dans un outil proxy (Charles, par exemple) pour vérifier que la version du chemin d’accès reflète la version 3.1. Par exemple :
>
>`https://primetime-a.akamaihd.net/assets/3p/v3.1/222000/167/d77/ 167d775d00cbf7fd224b112sf5a4bc7d_0e34cd3ca5177fbc74d66d784bf3586d.m3u8`

**Version 1.4.43**

* Billet n° 27143 - Impossible de lire la piste audio 5.1 sur les périphériques FireTV

   * TVSDK est désormais capable de lire du son AC3 sur les appareils FireTV. La lecture est toujours en stéréo.

* Billet n° 33902 - Diffusion publicitaire sécurisée via HTTPS

   * adobe primetime offre une option permettant de demander un premier appel au serveur d’annonces avant la mise en service et au serveur CRS sur https.

* Billet n° 34493 - Délai audio Bluetooth

   * ajouté `alwaysUseAudioOutputLatency` dans la classe MediaPlayer qui, lorsqu’elle est définie, entraînera l’utilisation de la latence de sortie audio dans le calcul de l’horodatage audio.

* Billet n° 34949 - Nouvelle version de la bibliothèque Video Heartbeat (VHL) intégrée.

**Version 1.4.42 (1791)**

* Zendesk #33719 : Le débit adaptatif de FireTV 4k évolue lentement. Prise en charge Ajoutée d’ABR pour les périphériques FireTV 4K.
* Zendesk #33338 :  resetDRM efface toutes les données de l’application.  Traitement d’un cas supplémentaire lorsque des exceptions dans des threads non TVSDK entraînaient le remplissage des files d’attente d’opération TVSDK.

**Version 1.4.41 (1776)**

* Zendesk #33002 - Companion asset data from TVSDK on Fire TV. Mise en oeuvre d’une nouvelle classe AdBannerAsset qui renverra les données Companion sous la forme Liste &lt;AdBannerAsset> et AdAsset::id est désormais une chaîne plutôt que longue.
* Zendesk #32821 - Le lecteur Android Primetime se fige lorsqu’il rencontre un horodatage de présentation (PTS) pour WWE. Ce problème a été corrigé dans cette version.
* Zendesk #33572 - Crash du Début publicitaire VideoAnalyticsProvider. L’utilisation de la bonne combinaison de la version commune du SDK VHL+Nielsen de VideoHeartbeat.jar a résolu ce problème.
* Zendesk #33355 - Fire TV : Revenez à 15 secondes de publication. Aucun correctif du client et du côté TVSDK ne vérifie cette information à leur niveau de fin et tiers.

**Version 1.4.40 (1764)**

* Zendesk #33068 - Problème de synchronisation de lèvres en Amazon sur le nouvel appareil. Le problème de synchronisation des lèvres a été corrigé dans ces versions.
* Zendesk #32215 - Android TVSDK 1.4.38 Problèmes de sécurité `[Hotlist]`. Mise à jour vers les dernières versions d’OpenSSL-1.1.0 et de curl-7.5.1.
* Zendesk #32920 - Ecran vierge au sein d’une coupure publicitaire et sans fin de coupure publicitaire. Correction d’un problème en raison duquel un conteneur VPAID pouvait se retrouver dans un état figé et où les publicités Facebook VPAID renvoyaient souvent plusieurs blocs CDATA dans un \&amp;lt;AdParameters\&amp;gt ; Noeud VAST.

**Version 1.4.39 (1744)**

* Zendesk #28976 - La demande de licence prend plus d&#39;une seconde. Tandis que les appels de demande de licence DRM qui utilisent le POST sont en cours d&#39;exécution, Curl ajoute &quot;Attendez : En-tête &quot;100-continue&quot;. Suppression de l’en-tête &quot;Expect:&quot; dans TVSDK.
* Zendesk n° 27707 - environnements de l’ISAC qui ne respectent pas les marqueurs CUE IN pour un retour anticipé ou un retour au contenu. Fourniture d&#39;un soutien à plusieurs générateurs d&#39;opportunités.

**Version 1.4.38 (1722)**

* Zendesk n° 21590 - Performances vidéo et suivi dans les derniers Origines

Intégration et certification de VHL 2.0 dans TVSDK afin de réduire les obstacles dans la mise en oeuvre de VideoHeartbeatsLibrary en réduisant la complexité des API.

* Zendesk #29688 - Prise en charge des clients Android O Beta.

Prise en charge de TVSDK pour la nouvelle version bêta d’Android.

**Version 1.4.36 (1713)**

* Zendesk #27392 - Ignorer le contenu sur Android

Pour faciliter le déchiffrement, le TVSDK Android élargissait incorrectement la plage d’octets du contenu non iframe de 16 octets. L’élargissement est nécessaire pour les flux Iframe, mais pas pour les flux non iframe.

**Version 1.4.34 (1702)**

* Zendesk #27638 - Fuite dans l’objet INet cURL

L’objet INet cURL Posix fuyait tout en conservant le gestionnaire de partage et le cache DNS utilisé dans les connexions cURL.

Ce problème a été résolu en supprimant l’objet INet cURL Posix du déconstructeur INet.

**Version 1.4.33 (1694)**

* **Bibliothèque OpenSSL**

La bibliothèque OpenSSL a été mise à jour avec la version 1.0.2j d&#39;OpenSSL.

* Zendesk #21701 - Envoyez l’URL de création originale pour la demande CRS 1401 au lieu de l’URL normalisée.
Ce problème est résolu en envoyant les URL créatives d’origine.

* Zendesk #25023 - Lecture vidéo de longue durée : blocage vidéo, scintillements d&#39;écranCe problème a été résolu en définissant le nombre maximal de dimensions de format vidéo pour les périphériques décodeurs CenturyLink.

* Zendesk #27460 - Le nouveau compte Akamai ne peut pas gérer une demande de cdn POST.
Le code a été mis à jour afin que la demande `cdn.auditude.com` d’annonce soit GET et non POST.

* Zendesk #28245 - L’état de lecture n’est pas averti correctement lorsque l’application passe de l’arrière-plan au premier plan. Ce problème a été résolu en restaurant correctement l’état de lecture pour qu’il soit lu ou mis en pause lorsque l’application revient au premier plan.

**Version 1.4.32 (1682)**

* Zendesk #25779 - La vulnérabilité de sécurité détectée avec TVSDKAndroid 4.2 et versions antérieures présente une vulnérabilité de sécurité lorsque JavaScript est activé dans WebView. L’utilisation de WebView par TVSDK a été désactivée pour les périphériques exécutant OS 4.2 ou version ultérieure. Ceci désactive l’utilisation de publicités VPAID dans TVSDK sur ces périphériques.

* Zendesk #26890 - Problème dans l’état ÉCRAN (Activé/Désactivé) avec gestion de la référence. PlayerLorsque le moteur de vidéo d’Adobe (AVE) reprend à partir d’un état SUSPENDU, DefaultMediaPlayer ne met pas à jour son état. Par conséquent, DefaultMediaPlayer reste à l’état SUSPENDU même si l’AVE est à l’état LECTURE. Ce problème a été résolu en définissant l&#39;état DefaultMediaPlayer sur PLAYING lors de la réception d&#39;un état PLAY à partir de l&#39;AVE, même si l&#39;état actuel de DefaultMediaPlayer est SUSPENDU.

**Version 1.4.31 (1675)**

* Zendesk #21974 - Exceptions en raison d’objets nuls
   * AdIndex est rarement incrémenté lorsque la valeur est nulle. Cela peut être dû à des appels d’API incorrects reçus pour adBreak preroll. Correction des types de données pour éviter de telles exceptions

* Zendesk #24714 - Désactivez la journalisation superflue.
   * Mise à jour de TVSDK pour désactiver la journalisation superflue

* Zendesk #24488 - AV Sync issues on Fire TV
   * Correction en améliorant la gestion des threads de décodeur AV. En particulier, chaque fois que les files d’attente de cadres d’entrée ou de sortie sont modifiées, le thread de décodeur spécifique au type de contenu du cadre est exécuté.

* Zendesk #26551 - Réparer les défaillances du CRS
   * Lorsque la requête est HEAD (http head), il n’est pas nécessaire de lire le contenu car il est vide. Bien qu&#39;il soit possible de le lire, l&#39;ancien Android (4.0.x) se bloque pendant que nous appelons read() et les Android plus récents renvoient la valeur correcte (-1) lorsque nous appelons read(). En fonction de cela, le code a été remplacé par ne pas lire le contenu pour &quot;head&quot;.

* Exception de pointeur nul Zendesk #26696 lors de l’accès à TrickPlayManager
   * Correction en vérifiant si l&#39;objet TrickPlayManager n&#39;est pas nul avant de l&#39;utiliser.

**Version 1.4.30 (1659)**

* Zendesk #22675 La durée des ressources n’est pas mise à jour pour les flux en direct/linéairesCe problème a été résolu en fournissant une nouvelle API, assetDuration, dans PTVideoAnalyticsTrackingMetadata qui fournit la durée des ressources pour les flux en direct et linéaires.

* Zendesk #25853 Fuite de mémoire dans TVSDK lors du changement de canauxLe problème de fuite d’un tampon de lecture de fichier lorsque MediaPlayer est réinitialisé ou libéré lors du téléchargement d’un fichier a été résolu.

**Version 1.4.29 (1653)**

* Zendesk #21200 - Le lecteur ne récupère pas de l&#39;état suspendu lorsque l&#39;application était en arrière-planLorsque le lecteur était suspendu après que le commutateur de diffusion a été signalé, la résolution permet au lecteur d&#39;exécuter le commutateur de diffusion en continu lors de la restauration du lecteur à partir de l&#39;état de suspension, au lieu de restaurer la position précédente.

* Zendesk #23412 - Le lecteur est coincé avec une boîte noire si vous cliquez sur n’importe quelle publicité dans les 3 dernières années de la coupure publicitaire. Ce problème est le même que Zendesk #21200.

* Zendesk #23616 - La coupure publicitaire ignorée recherche trop loin dans le futurSelon le type d’insertion publicitaire (insertion/remplacement), TVSDK détermine si la durée de la publicité est utilisée dans le calcul pour déterminer le point de terminaison de la coupure publicitaire.

* Zendesk #25078 - Fuite de mémoire DRM TVSDK sur Android TV STBTLa fuite de mémoire pour l&#39;objet adaptateur DRM a été localisée et corrigée.

* Zendesk #25067 - Crash in VideoEngineTimelineCela se produit parce que les objets n&#39;ont pas été correctement nettoyés et que des événements ont été appelés après la destruction des objets. Le problème a été résolu en ajoutant des vérifications pour empêcher les exceptions nulles.

* Zendesk #25352 - Définir l’en-tête HTTP personnaliséCe problème a été résolu en ajoutant un nouvel en-tête personnalisé à la liste autorisée sur TVSDK.

* Zendesk #25617 - Le roulement PTS en flux continu en direct provoque la discontinuité du lecteur et un blocage de la mémoire. Ce problème a été résolu en ajoutant une gestion de roulement PTS dans FragmentedHTTPStreamer lorsqu’un roulement survient au milieu d’un segment.

**Version 1.4.28 (1637)**

* Zendesk #23618 - événements de coupure publicitaire déclenchés avant la consultation de la stratégie publicitaireCe problème a été résolu en ne déclenchant pas les événements AD_BREAK_DÉBUT et AD_DÉBUT lorsque la publicité est ignorée en raison de l’annulation de la publicité. Le événement AD_BREAK_SKIPPED est envoyé à la place.

**Version 1.4.27 (1631)**

* Zendesk #23174 - Problème de performances lors du redimensionnement de la vidéo. Ce problème a été résolu en fournissant une nouvelle API, MediaPlayerView.setSurfaceFixedSize, qui permet à TVSDK d’accéder à SurfaceHolder.setFixedSize() à partir de MediaPlayerView.

* Zendesk #24450 - TVSDK effectue des demandes de duplicata et d’annonceCe problème survenait lorsque le temps écoulé avait été converti en long et non en doublon, et que ce problème avait été corrigé.

**Version 1.4.26 (1627)**

* Zendesk #21436 - Mise à jour de la bibliothèque OpenSSL vers la version 1.0.2h Mise à jour de la bibliothèque OpenSSL vers OpenSSL version 1.0.2h
* Zendesk #23825 - Les cookies ne sont pas inclus dans les rappels Corrigés en fournissant la prise en charge des cookies android.

**Version 1.4.25 (1620)**

* Zendesk #22900 - La lecture du flux DRM Adobe Primetime en direct n’est pas en cours sur le lecteur de référence Android. Le problème d’allocation de mémoire a été résolu.
* Zendesk #23176 - L&#39;application se bloque lorsqu&#39;elle tente de lire des publicités VPAID. Le blocage s&#39;est produit car l&#39;application ne crée pas de vue publicitaire personnalisée pour générer une publicité VPAID. Ce problème a été résolu en ignorant les publicités VPAID dans la réponse du serveur d’annonces lorsqu’il n’existe aucune vue d’annonces personnalisée.

* Zendesk #23153 - SampleAES DRM Stream - Playback stalling in the TVSDK Reference PlayerCe problème est identique à Zendesk #22900.

**Version 1.4.24 (1612)**

* Zendesk #20784 - Analytics : Déclenchement du contenu terminé pour les transitions vidéo en directCe problème a été résolu en ajoutant une API (trackVideoComplete) afin de déclencher manuellement la fin du contenu lors d’une session de suivi vidéo en direct/linéaire.

* Blocage du journal du moteur vidéo Zendesk #21977 lors de l’opération placeAdBreak/acceptAd
   * Dans ce numéro, les bibliothèques suivantes ont été mises à jour :
      * Bibliothèque AdobeMobile vers la version 4.10.0
      * Bibliothèque VHL vers la version 1.5.6
      * Bibliothèque VHL-Nielsen à la version 1.6.7

Ce problème a été résolu en ajoutant une vérification nulle avant d&#39;ajouter des publicités à la liste publicitaire acceptée.

* Zendesk #22313 Le débit des STB avec chipset Amilogic ne va pas au-delà de 1.2MTCe problème a été résolu en préchargeant les fonctionnalités du codec média et en désactivant le commutateur transparent pour les chipsets Amilogic.

* Zendesk #19520 Exemple de fichier AES HLS ne jouant pas dans les lecteurs TVSDK Ce problème a été résolu en gérant plusieurs descripteurs PMT pour les flux Exemples de flux HLS chiffrés AES.

**Version 1.4.23 (1602)**

* Zendesk #18852 - Mise à jour de la logique de sélection créative en fonction des règles CRS. Ce problème a été résolu en ajoutant un fichier de configuration JSON afin de spécifier la priorité de sélection créative.

* Zendesk #20861 - Android NTsa version prend en charge Android N en supprimant la possibilité d’utiliser directement les bibliothèques natives de la plate-forme Android qui ne sont plus accessibles aux applications s’exécutant sur Android N.

* Zendesk #21018 - Android N crashMême résolution que ZD# 20861.

* Zendesk #21266 - VideoEngineAdapter se bloque sur une erreur Invalid_KeyL&#39;erreur Invalid_Key n&#39;inclut pas de description d&#39;AVE. L&#39;analyse du texte a donc abouti à NPE. Le problème a été résolu en ajoutant une vérification nulle pour la description pendant onError avant d&#39;analyser la description.

* Zendesk #22286 - La bibliothèque native alloue de la mémoire à la lecture de clés/fragments provoquant un blocageCe blocage qui s&#39;est produit sur Android lors de la tentative de chargement d&#39;un manifeste avec plusieurs clés simultanément a été corrigé.

**Version 1.4.22 (1581)**

* Zendesk #17236 - Heure de début de lecture non fiable pour les vidéos HLS avec DRMTl’heure de saut avec les flux LBA, où l’heure de début du segment audio ne correspond pas à l’heure de début du segment vidéo, a été corrigée.

* Zendesk #17680 - La lecture vidéo se fige sur la boîte Selevision Andredo. Le décodeur vidéo de cet appareil renvoie parfois un bond de temps de sortie important lors de la mise en file d&#39;attente d&#39;une image vidéo du tampon de sortie, et cet horodatage de sortie reste élevé. Ce problème a été résolu en renvoyant une erreur de profil *vidéo non prise en charge* qui ne force pas le lecteur à réessayer le même profil ou à choisir un autre profil.

* Zendesk #19074 - Gel vidéo pendant FFWD et REW trick playCe problème a été résolu en ajoutant un nouvel avertissement TRICKPLAY_ENDED_DUE_TO_ERROR pour avertir l&#39;application que le trickplay a été quitté et que la vidéo a été interrompue en raison d&#39;une erreur irrécupérable.

* Zendesk #19574 - TVSDK ne renvoie pas de données de réponse M3U8 pour le contenu DRM ou non DRMCe problème a été résolu de la manière suivante :

* Zendesk #19986 - Comportement OP rompu pour certains appareils comme Android TV
* ajouter une erreur FILE_NOT_FOUND à la condition.
* Lorsque l&#39;erreur provient d&#39;une erreur de *fichier introuvable* , séparez l&#39;URL et la réponse de la description de l&#39;erreur si la réponse est disponible.
L&#39;erreur logique qui a été introduite par la prise en charge de NVidia shield OP a été corrigée. Sur les périphériques de protection non NVidia, faites confiance aux indicateurs d&#39;affichage sécurisés même si le type d&#39;affichage est inconnu.

* Zendesk #20549 - Gestion des listes de lecture obsolètes. Ce problème a été résolu en réduisant l&#39;intervalle entre la mise à jour du manifeste en direct à la moitié de la durée prévue du segment, si la récupération précédente ne reçoit pas de nouveaux segments.

* Zendesk #20742 - L&#39;utilisation de la mémoire semble continuer à augmenter lors de la lecture de contenu en direct sur FireTV. Le blocage est causé par la table de référence d&#39;objet JNI qui a atteint la limite. Ce problème a été résolu en supprimant la référence à l’objet MediaFormat qui a été créé lors du redémarrage du décodeur.

* Zendesk #21125 - Retour d’une coupure publicitaire linéaire/en direct tôt (CSAI). ajouté une fonction permettant au lecteur de revenir au contenu principal pendant une coupure publicitaire si le lecteur enregistre la scission dans les signaux publicitaires en utilisant le scintillement dans le détecteur d&#39;opportunités.

* Zendesk #21334 - Valeur du délai d’expiration de la demande d’annonce TVSDK pour les demandes d’annonce tierces. Un paramètre adRequestTimeout a été ajouté à AdvertisingMetadata afin d’activer un délai d’attente global pour l’appel de publicité.

**Version 1.4.21 (1566)**

* Zendesk #17781 - L’encapsulation d’écran ADB ne fonctionne plus. Ce problème a été résolu en ajoutant l’API DefaultMediaPlayer.create(Context context, boolean secureSurface), qui permet la capture d’écran.
Pour autoriser les captures d’écran, transmettez false pour secureSurface.
Important : Nous vous recommandons vivement de ne pas activer cette fonction de capture d’écran dans un paramètre de production.

* Zendesk #19074 - Gel vidéo pendant la lecture de l&#39;astuce FFWD et REWLes problèmes suivants qui se sont produits lorsque l&#39;astuce Play pouvait se figer dans la lecture ont été résolus :

* Zendesk #19532 - La légende de fermeture semble irrecevable.
   * FHS début le trickplay, mais le premier segment d&#39;iframe n&#39;avait pas d&#39;image dedans.
   * Lors du téléchargement d’un segment iFrame, si FHS rencontre une condition d’erreur, il quitte le jeu vidéo et interrompt la lecture.
   * L’implémentation de MediaCodec en mode Android attend pour toujours la disponibilité de la file d’attente d’entrée pendant qu’on lui demandait de vider toutes les tampons d’entrée/sortie.
Ce problème a été résolu en inversant l’ordre des signaux WebVTT de sorte que plusieurs signaux qui se chevauchent semblent &quot;faire défiler&quot;.

* Zendesk #19574 - TVSDK ne renvoie pas de données de réponse M3U8 pour le contenu DRM ou non DRMAu premier chargement du fichier manifeste dans PTMediaPlayerItem.prepareToPlay, si le chargement échoue, TVSDK ne signale pas le corps de la réponse d’échec à l’application.
Ce problème a été résolu en permettant à TVSDK de signaler la réponse à l’échec comme une erreur à l’application.

* Zendesk #19701 - Blocage de la lecture avec SAP/DiscontinuitéLe blocage du lecteur lorsque le son et la vidéo ne sont pas alignés en cas de discontinuité a été résolu.

* Bogue #PTPLAY-11162 - La mise à jour de la bibliothèque OpenSSL vers la version 1.0.2f a été résolue.

**Version 1.4.20 (1546)**

* Zendesk #17384 - Demande de fonctionnalités : La prise en charge des métadonnées ID3 pour la lecture AAC La prise en charge des balises ID3 dans les médias AAC a été fournie dans le SDK TVSDK pour Android à partir de la version 1.4.20.

* Zendesk #18358 - Le lecteur se fige sur les interrupteurs de débit avec discontinuités désynchroniséesCe problème a été résolu en traitant correctement les boîtiers de raccordement ABR.

* Zendesk #19232 - L’application utilisant TVSDK 1.4.18 se comporte étrangement sur la version antérieure de Amazon OS 4Ce problème a été résolu en supprimant la création de vue Web masquée dans le processus d’initialisation du lecteur TVSDK afin d’éviter tout conflit avec les périphériques qui ne prennent pas en charge Android Webview.

* Zendesk #19585 - Lecture à mouvement lent lorsque la transition du débit adaptatif se produit.
Lors d’un changement d’ABR, si le nouveau profil présente une fréquence d’échantillonnage audio différente de celle du profil actuel, la lecture devient rapide ou lente. En effet, le présentateur vidéo n’est pas averti que le format audio a changé.
Ce problème a été résolu en s’assurant que l’indicateur de notification est défini au bon endroit.

* Zendesk #19683 - Lecture SAP DAI - Pas de son pendant quelques secondes.
Dans plusieurs cas de la logique TVSDK, lorsque l’horodatage de deux segments de rendu a été comparé, RENDITION_TIMEOUT_THRESHOLD était utilisé comme plage de valeurs acceptable, car l’horodatage ne peut pas toujours être comparé avec une différence de 0 ms. Si l’écart se trouve dans la plage de RENDITION_TIMEOUT_THRESHOLD, l’hypothèse est qu’il s’agit d’une correspondance.

Le paramètre RENDITION_TIMEOUT_THRESHOLD a été défini à 100 ms, mais il s&#39;est avéré insuffisant pour certains flux. Ce problème a été résolu en augmentant à 200 ms la valeur de RENDITION_TIMEOUT_THRESHOLD.

* Zendesk #19699 - TVSDK ne parvient pas à permuter entre les pistes de sous-titres VTT. Ce problème a été résolu en faisant le vidage du lecteur et en rechargeant le manifeste lorsqu’un suivi change et en corrigeant le problème de conversion de chaîne UTF8 qui affectait les noms de suivi de sous-titres WebVTT sur doublon-octet.

* Zendesk #19717 - Options CC problèmes d&#39;affichageCe problème a été résolu en gérant correctement la chaîne Unicode.

* Zendesk #19910 - Les balises TIT2 ID3 ne sont pas détectéesCe problème a été résolu en fournissant une prise en charge plus complète des codages de chaînes ID3 v2.4 et en prenant en charge ID3 v2.3.

* Zendesk #20135 - TVSDK déclenche plusieurs contenus onComplete pour le contenu VOD.
Ce problème a été résolu en ajoutant l’écouteur de événement post_roll_compelete au bon endroit, plutôt qu’à la casse complète du événement de modification d’état.

**Version 1.4.19 (1521)**

* Zendesk #4180 - TVSDK n&#39;applique pas HDCP.
   * Il s&#39;agit d&#39;un correctif partiel pour ce ticket et ne traite que le problème des périphériques de protection NVidia.
Vous devez utiliser l&#39;API de détection HDCP correctement implémentée dans le Bouclier Nvidia pour effectuer un suivi dynamique de l&#39;état HDCP.

* Zendesk #18358 - Le TVSDK gèle le commutateur de débit avec des discontinuités désynchronisées.
   * Ce problème a été résolu en ajoutant un nouvel avertissement pour détecter la discontinuité PTS et en obligeant la vérification PTS à rétablir la recherche du segment correct pour chaque commutateur ABR.
Pour corriger le blocage, l’appel à la méthode mediaPlayer.setCustomConfiguration doit inclure forcePTSCheckForABR comme argument.

* Zendesk #19038 - Pas de diffusion en direct sur Asus Zenpad 10.

   Ce problème a été résolu en préchargeant les informations du codec multimédia, de sorte que vous ne puissiez pas requête à la fonction au moment de l’exécution.

* Les problèmes suivants sont les mêmes que Zendesk #19038 :
   * Zendesk #19483 - Le TVSDK s&#39;effondre sur la plate-forme Intel.
   * Zendesk #19171 - Blocages sur Asus Memo Pad 7 avec Android 5.0.

**Version 1.4.18 (1503)**

* Zendesk #3324 - Le rapports publicitaire Primetime ne suit pas les coupures publicitaires lorsqu’il n’y a aucun média publicitaire dans un VMAP.
Lorsqu’une coupure publicitaire est vide, le début de coupure publicitaire et les événements de suivi complets n’étaient pas en cours d’épinglage. Ce problème a été résolu en envoyant des pings de début de coupures publicitaires lors de coupures publicitaires vides, telles que VMAP AdBreak, avec un noeud AdSource valide.

* Zendesk #18229 - SetCCVisiblity(VISIBLE) est ignoré après l’appel de MediaPlayer.reset(). Ce problème a été résolu en ajoutant setCCVisibility(Visibility.INVISIBLE); à la fonction reset() dans la classe MediaPlayer.

* Zendesk #18328 - Abandon du problème d&#39;image sur les périphériques 2e génération de Amazon Fire TV pour le contenu avec 60FPSTCe problème a été résolu en appliquant les images FPS codées pour la prise de décision du temps de veille et avec une logique de prédiction FPS mieux encodée.

**Version 1.4.17 (1472)**

* Zendesk #2231 - Erreur renvoyée en raison de la récupération du manifeste indisponible dans MediaPlayerNotificationCe problème a été résolu en incluant le corps de réponse du manifeste en cas d&#39;erreur d&#39;analyse.

* Zendesk #17703 - VideoEngineView n’empêche pas les captures d’écran lors de la lecture vidéo. La méthode setSecure est disponible depuis l’API 17, mais comme l’API 17 couvre les versions 4.2, 4.2.1 et 4.2.2, on ne sait pas lequel lancera une exception ou si elle est spécifique au périphérique. Ce problème a été résolu en plaçant VideoEngineView.setSecure dans la clause try catch.

* Zendesk #17919 - La recherche de contenu provoque une erreur de pulsationUne erreur de données d&#39;entrée non valide Une erreur de position se produisait suite à l&#39;appel de pulsation généré lors du démarrage de la recherche après la pré-diffusion. Ce problème a été résolu.

**1.4.16a** (1454a)

* Zendesk #18215 - Certains flux AES ne peuvent pas se charger.
Ce problème a été résolu en vérifiant la taille des métadonnées DRM du profil avant de charger la clé AES.

**Version 1.4.16 (1454)**

* Zendesk #3875 - Tab S Blocage pendant la lectureRétablissement de la dépendance d’OKHTTP sur Auditude pour CRS car TVSDK utilise désormais directement httpurlconnection au lieu de curl. Le problème a été résolu en supprimant les exceptions avant d’effectuer tout autre appel JNI.

* Zendesk #4487 - Suivi du Canal linéaire du contenu Le problème a été résolu en permettant la réinitialisation de l’outil de suivi de pulsation vidéo lors d’une session de lecture de flux linéaire.

* Zendesk #17919 - Android - content search génère une erreur de pulsationLe problème qui se produit lorsque la pulsation est à l’état d’erreur lorsqu’une recherche est effectuée dans un chapitre a été résolu.

* Zendesk #18053 - Adobe Primetime se bloque sur MarshmallowLe TVSDK se bloquait sur Android M OS lorsque la bibliothèque TVSDK utilisait du code néon qui convertissait les couleurs YUV -> RVB. Le problème a été résolu en mettant à jour les fonctions à l’origine de ce problème en utilisant la version non néon du code.

* Zendesk #18072 - Android M - Crash de l’applicationLors de la vérification de la prise en charge du profil et du niveau, un blocage survient lors de l’appel des API MediaCodecList et MediaCodecInfo. Le problème a été résolu en fournissant une solution temporaire en chargeant toutes les informations de codec à l’avance afin d’éviter d’appeler ces API uniquement lorsque des informations de codec sont nécessaires.

* Zendesk #18074 - Sous-titres arabes ne fonctionnant pas sur Nexus avec Android 6.0 Le problème a été résolu en fournissant la prise en charge de la carte de polices CTS pour Android.

**Mise à jour de la version 1.4.15 (1438)**

* Zendesk #17437 - Long délai dans le démarrage du contenu VOD avec certains flux AES.
Pour résoudre ce problème, si plusieurs clés sont répertoriées dans le manifeste, téléchargez toutes les clés AES en parallèle.

**Version 1.4.15 (1435)**

* Zendesk #4278 - Glitches sur Android set top box when Adaptive bitrate changes (ABR).
Le correctif consistait à ajouter la prise en charge du commutateur ABR transparent avec le dernier codec média Android.

* Zendesk #17063 - L’appel de mediaPlayer.reset() provoque une erreur de réinitialisation du moteur vidéo.
Le correctif consistait à inclure le MediaErrorCode d’origine de VideoEngineExceptions lors de la distribution d’ErrorEvents.

* Zendesk #17130 - Une pause brève mais perceptible quand on change le débit de transmission vu sur FireTV.
(Identique au n° 4278 ci-dessus) Le correctif consistait à ajouter la prise en charge du commutateur ABR transparent avec le dernier codec média Android.

* Zendesk #17666 - Autres marqueurs publicitaires, publicités inattendues ou sans publicité lors de la reprise de contenu.
Le correctif posait un problème lors de l’exécution de prepareToPlay sur du contenu vidéo à la demande (VOD), la recherche initiale s’exécute sur l’heure locale plutôt que sur l’heure virtuelle.

* Zendesk #17437 - Long délai dans le démarrage du contenu VOD avec certains flux AES.
Le correctif consistait à télécharger toutes les clés AES en parallèle lorsque plusieurs clés étaient répertoriées dans le manifeste.

* Zendesk #17851 - Android TV - Black Frame pendant ABRTLe correctif était de spécifier KEY_MAX_WIDTH et KEY_MAX_HEIGHT pour activer la lecture adaptative.

**Version 1.4.14 (1415)**

* Zendesk #3875 - Tab S Blocage pendant la lecture.
Un correctif supplémentaire était nécessaire pour empêcher le blocage.

* Zendesk #17245 - Le retour sur investissement sur Android TV ne fonctionne pas.
Correction d’un autre problème en raison duquel la lecture se bloque lorsque la reprise est activée et que la réponse VMAP comporte une coupure publicitaire vide.

**Version 1.4.14 (1412)**

* Zendesk #17245 - Le retour sur investissement sur Android TV ne fonctionne pas.
Suppression d’une restriction pour la désactivation du reconditionnement créatif sur les publicités de secours.

**Version 1.4.13 (1388)**

* Zendesk #3502 - Prise en charge du basculement sur incident basé sur le client HLS pendant une coupure publicitaireAutoriser le basculement sur incident au manifeste principal lors de la mise à jour d&#39;une erreur de profil en direct survient pendant la période de coupure publicitaire.

* Zendesk #3875 - Tab S Blocages pendant la lecturePour résoudre le conflit entre HttpUrlConnection et cURLm, utilisez une bibliothèque tierce.

* Zendesk #4450 - Problème lors de la définition de métadonnées personnalisées pour un emplacement unique dans un résolveur de contenuAjoutez un paramètre aux paramètres Opportunité.

**Version 1.4.12 (1388)**

* Zendesk #2751 - CSAI et CRS | Améliorer : Gérez les éléments dynamiques dans certaines URL de fichier multimédia.
Mise à jour de Creative Repackaging Service afin de gérer correctement les publicités avec des URL créatives dynamiques.

* Zendesk #3965 - Le retour à la lecture normale à partir d’un scénario de trickplay produit un bond en avant avant avant de commencer la lecture.
   * Le correctif inclut TVSDK renvoyant l’heure avant le changement de taux jusqu’à ce que toutes les variables soient mises à jour, au lieu d’essayer de calculer GetStreamTime.
   * Correction d’un blocage lors du changement de la vitesse de lecture des astuces à la fin du flux.
   * Correction du calcul de l&#39;heure actuelle lors de la lecture de l&#39;astuce.

* Zendesk #3978 - Le jeu de cartes à 8x et 16x gèle fréquemment.
   * Choisissez toujours le profil de lecture de l’astuce avec le débit binaire le plus bas pour éviter la mise en mémoire tampon constante.
   * Augmentez l&#39;intervalle d&#39;image de saut pour un taux de lecture de l&#39;astuce élevé.
   * Correction d’un problème en raison duquel la mémoire tampon continuait de s’étendre après avoir atteint sa cible pendant la lecture de l’astuce.

* Zendesk #3992 - Vitesses de jeu vidéo supplémentaires.
TrickPlay a été mis à jour pour accepter des taux supérieurs à 16x ; +/- 32, +/-64 et +/-128 sont désormais également autorisés.

* Zendesk n° 4007 - Interprétation de l’objet GEOB dans le cadre des métadonnées de la chronologie (Android et Web).
API setByteArray et getByteArray Ajoutées.

* PTPLAY-7301 - Instant On début at Random Access Point.
Instant On a été mis à jour pour permettre un point de départ non nul.

**Version 1.4.11 (1363)**

* Zendesk n°2076 - Fréquente bégustation lors de la lecture vidéo sur Motorola Xoom avec Android 4.0.3Ajoute des périphériques pour les empêcher de tenter de lire du contenu à profil élevé.

* Zendesk #2197 - `[Ads]` Suivi et erreurs répartition de OperationFailedEvent avec notification d&#39;avertissement.

* Zendesk #3304 - Macro VAST 3.0 `[ERRORCODE]` non renseignée
   * le code d’erreur 400 sera affiché si la publicité intégrée comporte un élément créatif incorrect.
   * `[ERRORCODE]` macro sera encodée dans l&#39;URL

**Version 1.4.10 (1354)**

* Zendesk #2941 - Les ressources en direct n’ont pas &quot;0&quot; dans la plage recherchéeAuparavant, il y avait un tampon de 3 segments lorsque vous recherchiez le début d’un flux en direct, il est maintenant possible de rechercher jusqu’au tout début d’un flux en direct (c’est-à-dire le début du premier segment).

* Zendesk #3169 - Mise à jour du lecteur de référence avec l’intégration Adobe AnalyticsLe lecteur de référence a été mis à jour avec la bibliothèque Adobe Analytics comme exemple d’implantation.
* Zendesk #3299 - Comportement inexplicable de jeux de ficelles
   * Correction d’un bogue en raison duquel le retour à l’état de lecture après l’arrêt de la lecture du tour pouvait prendre plusieurs secondes (parfois 25 secondes ou plus).
   * Correction d’un bogue en raison duquel l’appel d’une astuce était lancé une seconde fois sur le même support et pouvait provoquer le blocage du flux à l’heure actuelle.
* Zendesk #3433 - Android et Flash - Problèmes de sous-titres

GetLine pour WebVTT ne respectait pas la longueur ajustée &lt;CR>&lt;LF> d&#39;un paquet ; la dernière légende peut contenir des caractères de légendes précédentes.

* PTPLAY-6243 - Améliorer le lecteur de référence pour capturer les informations de débogage

Les exemples de lecteurs de référence Android ont été améliorés avec une option permettant d’activer les journaux de débogage et d’envoyer les résultats par courrier électronique. Cette option se trouve sous le menu Journal du lecteur de référence.

**Version 1.4.9 (1332)**

* Zendesk #2649 - La mémoire tampon terminée survient avant que la mémoire tampon initiale ne soit pleine.

Après une recherche, il est possible que le moteur de vidéo définisse l’état Lecture avant que le présentateur vidéo ne soit prêt à lire. Se produit lorsque l&#39;état de la mémoire tampon est élevé avant la recherche. Correction en avertissant le moteur vidéo de l&#39;état de mémoire tampon faible. L’état de mémoire tampon du moteur vidéo étant faible, l’appel de Play entraîne la modification de l’état de BUFFERING au lieu de PLAYING. La lecture reprend lorsque l’état devient LECTURE.

* Zendesk #2846 - Demande d&#39;amélioration : Permet de définir une chaîne d’agent utilisateur différente pour les appels effectués par la bibliothèque Auditude.

Une nouvelle API a été ajoutée pour définir l’agent utilisateur pour les appels liés à la publicité, auditudeSettings.setUserAgent(&quot;user/agent&quot;). Si aucun agent utilisateur n’est défini, la valeur par défaut est utilisée. Cela affecte uniquement l’agent utilisateur pour les appels liés à la publicité, l’agent utilisateur pour les appels de médias n’est pas modifié, qui est &quot;Adobe Primetime&quot;+&lt;agent utilisateur par défaut>.

**Version 1.4.8 (1324)**

* Zendesk #1218 - 106000.33 Erreur avec local ... Si le chargement du manifeste dans FragmentedHTTPStreamer::ThreadParseManifest() échoue, vérifiez si le domaine d&#39;URL est localhost et, dans l&#39;affirmative, remplacez le domaine par 127.0.0.1 et rappelez ThreadParseManifest.
* Zendesk #3072 - Passage automatique à des débits inférieurs. Modification du calcul de la longueur de la mémoire tampon pour ignorer la charge utile PTS zéro.
* Zendesk #3168 - Les sous-titres WebVTT ne s’affichaient que pour les 10 premières secondes.
* Zendesk #3193 - Demande d’API de modification de Profil dans TVSDK, PlaybackEventListener.onProfileChanged() a été ajoutée.

**Version 1.4.7 (1311)**

* Zendesk #2197 - Suivi des erreurs et des erreurs. Échec du chargement du manifeste de la notification Ajoutée pour l&#39;actif
* Zendesk #2575 - PSDK ignore la publicité personnalisée MARK en flux continu avant la vidéo.
* Zendesk #2719 - Win Death with auditude ads (Gagner la mort avec publicités d&#39;auditude), fixed beacon tracking (Correction du suivi des balises lorsqu&#39;elles sont redirigées vers l&#39;URL relative dans le module externe Auditude)
* Zendesk #2760 - Balise DISCONTINUITY ignorée en mode TrickPlay.
* Zendesk #2805 - Crash du lecteur au début de la lecture, même correction que Zendesk #2719
* Zendesk #2817 - Lecteur Android - Le lecteur est parfois suspendu et s’arrête de lire, corrigé en étendant la mise en mémoire tampon du décodage de 2,0 à 3,0 secondes.
* Zendesk #2839 - Adobe Primetime PSDK prend-il en charge les chipsets ARMv8 ?, a ajouté un correctif pour le blocage trouvé sur Galaxy S6.
* Zendesk #2885 - Auditude Blocage de la lecture, même correction que Zendesk #2719
* Zendesk #2895 - Echec constant de Live HLS après 10 minutes de lecture
* Zendesk #2925 - Commentaires concernant la version de développement Android (1.4.5), sur certains périphériques lorsque nous mettons le paquet en file d&#39;attente vers la file d&#39;attente d&#39;entrée, si le PTS est négatif, le décodeur passe dans un état bizarre où nous obtenons toujours un PTS de sortie négatif pour les paquets futurs. Le correctif définit le PTS d&#39;entrée sur zéro s&#39;il est négatif pour éviter ce problème.
* PTPLAY-4645 - Désactivez la prise en charge du chiffrement RC4 dans openssl. Il y a des exploits connus pour RC4. Cela signifie que si une tentative de connexion à un serveur prenant uniquement en charge RC4 est effectuée, elle échoue.

**Version 1.4.6 (1282)**

* Zendesk #2192 - Le débit n&#39;est pas toujours plus faible dans les mauvaises conditions réseau, corrigé en supprimant l&#39;implémentation rapide des commutateurs.
* Zendesk #2631 - Sous-titres arabes sur Android : Le texte sur plusieurs lignes apparaît coupé, corrigé en ajustant la taille de police des polices arabes.
* Zendesk #2844 - La mise en mémoire tampon de la note 4 et le temps de téléchargement des fragments ne sont pas exacts.

Ce problème a été corrigé en ajoutant une latence entre les téléchargements de segments de vidéo dans le calcul de la bande passante et en demandant à la logique de calcul du temps de téléchargement d’utiliser le temps de cycle de requête complet.

* Zendesk #2908 - Les sous-titres arabes ne fonctionnent pas sur Nexust 5, 6 et 7, corrigés en ajoutant 2 polices de substitution supplémentaires pour les scripts arabes.
* PTPLAY-4627 - Mettez à jour Nielson appsdk vers la version 1.2.3.7
* PTPLAY-5084 - Prise en charge du basculement de mise à jour du manifeste de Principal en direct

**Version 1.4.5 (1248)**

* Zendesk #1757 - Uniquement audio lu ou plantages du lecteur pour certains profils de débit vidéo, le blocage de Nexus 4 et Nexus 7 corrigé
* Zendesk #2072 - TimedMetadata pour AdEvent ne contient pas l’URL complète juste &quot;http&quot;
* Zendesk #2192 - Le débit ne diminue pas toujours dans les mauvaises conditions réseau
* Zendesk #2256 - Accès à la liste de lecture du Principal, mise à jour du PSDK pour distribuer des événements de métadonnées temporisées pour les balises abonnées sur la liste de lecture principale.
* Zendesk #2269 - Deux langues de sous-titres différentes apparaissent simultanément à l’écran avec WebVTT.
* Zendesk #2417 - Lecteur essayant de télécharger des sous-titres avant le début de lecture, WebVTT utilisait la variable de numéro de segment incorrecte pour la correspondance des numéros de segment. Le bogue ne s’affichait que pour les médias dont les indices de segmentation commençaient à zéro.
* Zendesk #2470 - PSDK ne revient pas de l&#39;état SUSPENDU lorsque le changement de débit survient après la suspension. Dans une situation particulière où la recherche intelligente est appelée par RestoreGPUResource (restaurer le lecteur à partir de l&#39;état de suspension) et que le commutateur de diffusion détecté avant cela, la recherche intelligente est incapable de se terminer et résulte en une mise en mémoire tampon constante.
* Zendesk #2451 - Sous-titrage &quot;bottom inset&quot;, ajout du paramètre &quot;bottomInset&quot; au code de sous-titrage
* Zendesk #2480 - Désactivation de l’optimisation de la redirection HTTP 302, prise en charge Ajoutée pour la définition de la propriété useRedirectUrl
* Zendesk #2486 - Balises tierces
* Zendesk #2547 - Sous-titres arabes : Le texte doit être aligné à droite justifié

**Version 1.4.4 (1195)**

* Zendesk #1158 - Échec de la lecture sur le validant Huawei (Y301A1)
* Zendesk #1709 - Taille de média incorrecte et vidéo étirée
* Zendesk #1757 - Lecture audio uniquement après le basculement de profil entre les flux avec des données spa/pps identiques
* Zendesk #2095 - État HTTP 307 (redirection) entraînant l’arrêt de la lecture par le lecteur d’Adobe.
* Zendesk #2126 - événement TimedMetaData manquant pour le dernier ADEVENT, les balises abonnées qui existent après le dernier segment n’ont pas été signalées au PSDK à partir d’AVE.
* Zendesk #2227 - Verrouillages dans VideoEngine nativeReset et nativePause
* Bogue #3921755 - Mise à jour de la bibliothèque OpenSSL vers la version 1.0.1L

**Version 1.4.3 (1173)**

* Zendesk #1591 - RENDITION_M3U8_ERROR
* Zendesk #1870 - Sous-titre fermé Activé et Désactivé
* PTPLAY-1818 - Rembobiner les taquets de lecture au lieu de revenir en arrière
* PTPLAY-2736 - Une légende WebVTT précédemment affichée s’affiche à l’écran lorsqu’un flux avec une légende WebVTT se termine à la lecture.
* PTPLAY-3773 - Une publicité preroll moyenne n’est pas lue lorsque la lecture de flux est lancée après la position de la publicité.

**Version 1.4.2**

* Zendesk n° 1561 - Prise en charge du basculement sur incident basé sur le client HLS en temps de primetime. Utilisera la date du programme pour répondre au basculement
* Zendesk #1590 - LoadInfo.MediaDuration a toujours la valeur 0 (non fixe pour audio uniquement)
* Zendesk #1626 - Fuite potentielle de mémoire dans le lecteur. Aucune fuite de mémoire réelle, problème lié à l&#39;enregistrement de l&#39;historique des notifications des 1 000 dernières notifications, ceci a été réduit à 100.
* Zendesk #2192 - Le débit ne diminue pas toujours dans les mauvaises conditions réseau

**Version 1.4.1 (1121)**

* Zendesk #1951 - Lockup in VideoEngine.nativeReset() on 4.0.x devices
* Zendesk n° 2064 - Crash natif SIGSEGV sur des périphériques Android basés sur l&#39;Intel
* Zendesk #2075 - Lockup in VideoEngine.nativeReleaseGPUResource on 4.0.x devicesRemarque : Cette version est ***requise*** pour la prise en charge d&#39;Android 5.0 (Lollipop)
* Zendesk #1513 - Prise en charge de Lollipop pour Android
* Zendesk #1709 - Taille de média incorrecte et vidéo étirée
* Zendesk #1871 - Les légendes WebVTT disparaissent parfois puis réapparaissent lors de l’affichage d’un flux en direct avec des légendes WebVTT.
* Zendesk #1996 - Aucun marqueur de chronologie n’est visible dans PSDK 1.4.0
* Zendesk #2046 - Crash avec PSDK 1.4.1.1113, correction d&#39;un blocage pour les flux en direct quand aucune publicité n&#39;est retournée par auditude
* Bogue #3769657 - Mise à jour de la version de curl à 7.38.0
* PTPLAY-1575 - Lorsque des débuts de lecture ABR avec diffusion en continu audio uniquement, puis basculent en flux audio/vidéo, la vidéo ne s’affiche jamais pendant que l’audio continue.
* PTPLAY-2499 - Mise à jour d&#39;OpenSSL vers la version 1.0.1j pour corriger les vulnérabilités récentes
* PTPLAY-2632 - La vidéo ne se rétablit pas après la fin de la publicité au milieu de la série sur Android Lollipop.
* PTPLAY-2678 - Stalls de vidéo pendant les tests de longévité en direct sur Android Lollipop

**Version 1.4.0**

* Zendesk #1024 - Fonction permettant de supprimer une publicité du flux via un manifeste
* Zendesk #1293 - Problème de sélection de la piste de légende fermée.
* Zendesk #1590 - LoadInfo.MediaDuration a toujours la valeur 0, mediaDuration affiche maintenant la valeur correcte.
* Zendesk #1629 - plantage du lecteur/de l’application à la fin de la lecture de la publicité sur Galaxy S4
* Zendesk #1674 - ClosedCaption Ne s’affiche pas, la légende 708 correcte s’affiche lorsque les codes ETX 0x03 sont manquants.
* PTPLAY-2157 - Les styles de sous-titrage par défaut ont été renvoyés par les utilisateurs, même si un style différent a été défini et vérifié visuellement sur le flux. Les propriétés de style Légende fermée indiquent désormais la valeur sur laquelle elles ont été définies.

## Problèmes connus dans la version 1.4 {#known-issues-in}

**Version 1.4.31**

* PTPLAY-16803 - La légende fermée ne fonctionne pas avec le contenu audio uniquement, car le système de sous-titrage a besoin de vidéo pour fonctionner. Sans vidéo, il n’y a pas de dimension de fenêtre d’affichage et sans dimension de fenêtre d’affichage, nous ne pouvons pas afficher de graphiques pour les légendes.
* PTPLAY-1634 - La même balise d’abonnement comporte différents horodatages dans différentes fenêtres dynamiques. Lorsque la fenêtre active se déplace, la même balise doit comporter les mêmes horodatages. Cependant, parfois, même les mêmes balises ont des horodatages différents.
* PTPLAY-3197 - Blocage avec le signal 11 erreur SIGSEGV sur le périphérique Acer Iconia après environ 1 heure de lecture continue
* PTPLAY-3310 - Avec un débit audio plus faible, le son devient bouché/stuttery sur Acer Iconia.
* PTPLAY-3355 - Blocage WIN sur Motorola Xoom avec 4.0.x après environ 1 heure de lecture continue.
* PTPLAY-3557 - Le rembobinage lors d’une coupure publicitaire entraîne la fin du flux
* PTPLAY-7079 - La fenêtre de lecture sur un client android ne fonctionne pas avec Secure Stop/Hard Stop.
* Bogue n° 3760144 - La résolution peut se décaler ou apparaître à l&#39;impulsion lorsque le flux est en pause sur certains appareils tels que Kindle Fire 7 et Samsung Galaxy Nexus. Uniquement observable sous contrôle rapproché
* Bogue #3761170 - La recherche de contenu local dans les publicités en direct ne peut pas effectuer de recherche dans le contenu de la publicité, il est préférable d’utiliser les APITime actuelles pour les flux en direct.
* Bogue #3763370 - Les flux dynamiques avec publicités présenteront parfois deux marqueurs publicitaires qui se rapprochent lorsqu’il ne devrait y en avoir qu’un seul. Ces marques publicitaires représentent la même publicité et une seule est lue
* Bogue #3763373 - Le marqueur d’annonce peut brièvement disparaître lors de la recherche au-delà d’une publicité dans les flux VOD. Le marqueur publicitaire est restauré et il n&#39;y a aucun autre effet négatif sur la chronologie
* Certains périphériques connaissent des problèmes de lecture. Voir Problèmes de périphérique [connus dans la version 1.4](https://helpx.adobe.com/primetime/release-notes/tvsdk-1-4-android.html#Knownissuesin14).
* Implémentation de référence - La lecture de la fiche n&#39;est pas implémentée dans l&#39;exemple d&#39;application
* Sur certains périphériques Android TV, une image noire peut être vue en raison d’une réinitialisation du décodeur aux points de transition suivants :
   * entrée et sortie du mode de tricotage
   * commutation entre des pistes audio à liaison tardive
   * d&#39;une publicité au contenu principal.

**Version 1.4.23**

* La légende fermée ne fonctionne pas avec le contenu audio uniquement, car le système de sous-titrage a besoin de vidéo pour fonctionner. Sans vidéo, il n’y a pas de dimension de fenêtre d’affichage et sans dimension de fenêtre d’affichage, vous ne pouvez pas afficher de graphiques pour les légendes.
* À partir de la version 1.4.23, TVSDK ne prendra pas en charge Gingerbread OS 2.3. En effet, TVSDK a utilisé les bibliothèques Android privées suivantes pour recueillir des informations matérielles sur les périphériques dotés de Gingerbread OS :

   * `libstagefright.so`
   * `libcutils.so`

Dans la version Android N, Google a supprimé l’accès à ces bibliothèques privées. Le système d&#39;exploitation Gingerbread représente actuellement moins de 1 % de la part de marché d&#39;Android OS dans le monde, de sorte qu&#39;après la version 1.4.23, le système d&#39;exploitation Gingerbread ne sera plus pris en charge par TVSDK.
Lorsque vous utilisez la version 1.4.23 (qui comprend la prise en charge d’Android N) ou ultérieure :
* Mettez à jour vos applications pour utiliser la version 11 de minSdkVersion.
* Si l’utilisateur final exécute OS 2.3, la version du SDK est inférieure à la version minSdkVersion de l’application. Le système interrompt l’installation ou la mise à niveau de l’application.
* Si votre utilisateur final exécute une version supérieure à OS 2.3, l’application sera correctement installée.

Si vous mettez à jour minSdkVersion :

* Si votre utilisateur final exécute OS 2.3, l’application est installée mais la lecture ne fonctionne pas.
Ceci s’applique à la fois à la mise à jour et à la nouvelle installation.
* Si votre utilisateur final exécute un système supérieur à OS 2.3, l’application est correctement installée et le contenu est lu correctement.

**Version 1.4.22**

* La sortie anticipée des publicités ne fonctionne pas avec certaines des publicités preroll moyennes lorsque les balises splice-out et splice-in sont trop proches les unes des autres.

**Version 1.4.2**

* Le rembobinage lors d’une coupure publicitaire entraîne l’achèvement du flux.

Le Lecteur Media envoie incorrectement MediaPlayerState.Complete pendant l’opération de rembobinage de la lecture de l’écran lorsqu’il atteint une limite publicitaire. Le lecteur doit ignorer ce événement lorsqu’il est en mode de lecture par astuces, sinon le SDK gère correctement l’état.

**Version 1.4.0 (1086)**

* PTPLAY-1634 - La même balise Abonné comporte différents horodatages dans différentes fenêtres dynamiques. Lorsque des fenêtres actives se déplacent, la même balise dans chacune d’elles doit comporter les mêmes horodatages. Cependant, parfois, même les mêmes balises ont des horodatages différents.
* PTPLAY-2541 - COMPONENT_CREATION_FAILURE est parfois visible après plusieurs commutateurs vers/depuis le courant alternatif lors de pannes d&#39;électricité.
* Bogue #3726865 - Si un flux LBA à débit multiple est début à partir d’un flux audio uniquement, la vidéo ne s’affichera pas si vous passez à un flux audio/vidéo. Le fait de démarrer à partir d’un flux audio/vidéo n’affichera pas ce problème et peut basculer entre les flux audio et audio/vidéo.
* Bogue n° 3760144 - La résolution peut se décaler ou apparaître à l&#39;impulsion lorsqu&#39;un flux est en pause sur certains appareils tels que Kindle Fire 7 et Samsung Galaxy Nexus. Uniquement observable sous contrôle rapproché
* Bogue #3761170 - searchToLocal en direct avec des publicités ne peut pas effectuer de recherche dans le contenu de la publicité ; il est préférable d’utiliser les API currentTime pour les flux en direct.
* Bogue #3763370 - Les flux dynamiques avec publicités présenteront parfois deux marqueurs publicitaires qui se rapprochent lorsqu’il ne devrait y en avoir qu’un seul. Ces marques publicitaires représentent la même publicité et une seule est lue
* Bogue #3763373 - Le marqueur d’annonce peut brièvement disparaître lors de la recherche au-delà d’une publicité dans les flux VOD. Le marqueur publicitaire est restauré et il n&#39;y a aucun autre effet négatif sur la chronologie
* Certains périphériques connaissent des problèmes de lecture. Pour plus d’informations, voir Problèmes de périphérique [connus dans la version 1.4](https://helpx.adobe.com/primetime/release-notes/tvsdk-1-4-android.html#Knownissuesin14).
* Implémentation des références - Trick play n&#39;est pas implémenté dans l&#39;exemple d&#39;application.

## Problèmes de périphérique connus dans la version 1.4 {#known-device-issues-in}

| Périphérique | Chipset | Problème | Cause | Solution |
|--- |--- |--- |--- |--- |
| Droid X | TI OMAP3 | Le délai d’ABR est attendu depuis le redémarrage du décodeur. |  |  |
| HTC Desire (différent de HTC Desire HD) | QSD8250 | Impossible de lire la vidéo. Renvoie une erreur VIDEO_PROFIL_NOT_SUPPORTED. | Le désir ne fournit pas un décodeur matériel approprié. Il donne le décodeur SW de Stagefright. | Redémarrez le périphérique. |
| HTC EVO 4G | QSD8650 | Aucun décodeur HW. | Qualcomm n&#39;a pas de décodeur HW. | Mise à niveau vers Android 4.x. |
| Kindle FireSystem version 6.0 | TI OMAP4 | Ne lit pas les flux HLS. La vidéo sur AIR ne fonctionne pas. |  | Mise à niveau vers la version 6.3 du système. |
| Kindle Fire HD | TI OMAP4 | Peut entrer dans un état où il ne peut pas lire la vidéo. Renvoie les erreurs VIDEO_PROFIL_NOT_SUPPORTED et UNRECOVERABLE_ERROR. | Le décodeur HW se retrouve dans un état irrécupérable lorsque l&#39;application n&#39;arrête pas complètement le décodeur HW, par exemple après un blocage. Se produit également sur les applications natives sur le périphérique. | Redémarrez le périphérique. |
| Kindle Fire HD 8.9 | Snapdragon 800 | AVE se bloque après plusieurs commutateurs ABR. |  |  |
| Motorola Atrix | Tegra2 | Problèmes de performances globaux avec AVE par rapport à AIR. Audio/vidéo hors synchronisation, la lecture vidéo se fige après 9 à 15 minutes de lecture. Blocs. | Peut-être lié à openGLES que nous activons sur AIR. En cours d&#39;enquête. |  |
| Nexus 7 (2e génération) | S4Pro APQ8064 (Qualcomm) | L&#39;appareil se bloque lorsqu&#39;un film est suspendu pendant plus de 30 minutes. | Problème de périphérique signalé à Google. | L’application doit expirer afin de ne pas autoriser un état de pause long. |
| Nexus S (GB) | Humming Bird | Impossible de lire une vidéo à l&#39;aide du décodeur HW. | Il n&#39;y a pas de décodeur HW basé sur Stagefright dans Nexus S, donc pour Android 2.3 nous utilisons un décodeur SW. | Effectuez la mise à niveau vers ICS. |
| Nexus S (ICS) | Humming Bird | Des vidéos scintillent parfois. | De mauvaises données peuvent entraîner un mauvais état du décodeur. | Redémarrez le périphérique. |
| Tablette NookAndroid OS : 2,3 | TI OMAP 4 | La vidéo ne fonctionne pas et l&#39;application est suspendue. | Stagefright entre dans un état instable après avoir exécuté l’application plusieurs fois. Les appels à mediaplayer::QueryCodecs sont suspendus. | Redémarrez le périphérique pour réinitialiser l’état. |
| Samsung Galaxy ACE | Qualcomm MSM7227 | Impossible d&#39;installer l&#39;application SampleMediaPlayer. | utilise ARM v6 au lieu du chipset ARM v7 le plus courant. FP/AIR ne prend pas en charge ce périphérique. |  |
| Samsung Galaxy ACE2Android OS : 2.3.6 | NovaThor U8500 | Impossible de lire la vidéo. | Ce chipset est un décodeur inconnu pour Android pre-ICS dans AVE. |  |
| Samsung Galaxy S2 (GT-I9100) | Exynos | Les performances vidéo ne sont pas à la hauteur pour ce périphérique. | Le décodeur HW renvoie des cadres décodés avec un PTS incorrect. Il semble que le décodeur utilise le temps de décodage plutôt que le temps de présentation. |  |
| Samsung Galaxy S2 GAndroid OS : 2.3.6 | TI OMAP4 | Blocage au démarrage de la vidéo. |  | Mise à niveau vers Android 2.3.7 ou 4.x. |
| Samsung Galaxy S3 (I747) | Qualcomm MSM8960 | Par intermittence, la vidéo se fige et seul le son est lu, puis ne répond plus. |  |  |
| Samsung Galaxy S3 I747M | SAMSUNG_M2ATT | La vidéo gèle. | Enquêter. |  |
| Samsung Galaxy Tab 1 v10.1 | Tegra 2 | La transition MBR peut prendre jusqu&#39;à trois secondes. | En tant que correctif pour les blocages MBR, nous redémarrons le décodeur pour chaque commutateur de flux, qui peut prendre jusqu’à trois secondes. |  |
| Samsung Galaxy Y |  | Impossible d&#39;installer l&#39;application SampleMediaPlayer. | utilise ARM v6 au lieu du chipset ARM v7 le plus courant. FP/AIR ne prend pas en charge ce périphérique. |  |
| Xoom | Tegra | Quelques images sont perdues pour le changement. Le décodeur n’est pas redémarré. | Limitation OMXAL. |  |

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète sur la page de formation et d’assistance [](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.
