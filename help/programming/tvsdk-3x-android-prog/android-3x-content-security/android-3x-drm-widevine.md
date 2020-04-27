---
description: Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour assurer un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces en remplacement de la solution intégrée d’Adobe.
seo-description: Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour assurer un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces en remplacement de la solution intégrée d’Adobe.
seo-title: DRM Widevine
title: DRM Widevine
uuid: 3a5fd786-4319-4e92-83b6-0f5328df6a44
translation-type: tm+mt
source-git-commit: ddcdf38fb7a77b7609a21bbdf6b32188b917e22c

---


# DRM Widevine {#widevine-drm}

Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour assurer un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces en remplacement de la solution intégrée d’Adobe.

Contactez votre représentant Adobe pour obtenir les informations les plus récentes sur la disponibilité de solutions DRM tierces.

<!--<a id="section_1385440013EF4A9AA45B6AC98919E662"></a>-->

Vous pouvez utiliser le DRM Windows natif Android avec les flux CMAF HLS.

>[!NOTE]
>
> Le schéma CTR de la CENC Widevine requiert une version minimale d&#39;Android 4.4 (API Niveau 19).
>
> Widevine CBCS Scheme requiert une version minimale d&#39;Android 7.1 (API Niveau 25).

## Définition des détails du serveur de licences {#license-server-details}

Appelez l’ `com.adobe.mediacore.drm.DRMManager` API suivante avant de charger la ressource MediaPlayer :

```java
public static void setProtectionData(
String drm,
String licenseServerURL,
Map<String, String> requestProperties)
```

### Arguments {#arguments-license-server}

* `drm` - `"com.widevine.alpha"` pour Widevine.

* `licenseServerURL` - URL du serveur de licences Widevine qui reçoit les demandes de licence.

* `requestProperties` - Contient des en-têtes supplémentaires à inclure dans la demande de licence sortante.

Par exemple, lors de l’utilisation de contenu compressé pour Expressplay DRM, utilisez le code suivant avant de lire :

```java
DRMManager.setProtectionData(
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null);
```

## Fournir un rappel personnalisé {#custom-callback}

Appelez l’ `com.adobe.mediacore.drm.DRMManager` API suivante avant de charger la ressource MediaPlayer.

```java
public static void setMediaDrmCallback(
MediaDrmCallback callback)
```

### Arguments {#arguments-custom-callback}

* `callback` - implémentation personnalisée de MediaDrmCallback à utiliser à la place de la valeur par défaut `com.adobe.mediacore.drm.WidevineMediaDrmCallback`.

Pour plus d’informations, voir Référence de l’API 3.11.

## Récupérer la zone PSSH de la ressource MediaPlayer actuellement chargée {#pssh-box-mediaplayer-resoource}

Appelez l’ `com.adobe.mediacore.drm.DRMManager` API suivante, de préférence dans l’implémentation de rappel personnalisée.

```java
public static byte[] getPSSH()
```

L&#39;API renvoie la zone d&#39;en-tête spécifique au système de protection associée à la ressource média Widevine chargée.

Une zone valide est disponible pour une courte durée (entre la création d’instances DRM et le chargement de clés). `MediaDrmCallback callback executeKeyRequest()` peut l’utiliser pour personnaliser la récupération des clés de licence.

>[!NOTE]
>
> `getPSSH()` L’API est uniquement prise en charge avec l’instance de lecteur unique. Plusieurs lecteurs ou la fonction Instant on doit s’initialiser en série pour recevoir la case appropriée.
