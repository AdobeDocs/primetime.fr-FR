---
description: Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour fournir un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces comme alternative à la solution intégrée d’Adobe.
title: Widevine DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Widevine DRM {#widevine-drm}

Vous pouvez utiliser les fonctionnalités du système DRM (Primetime Digital Rights Management) pour fournir un accès sécurisé à votre contenu vidéo. Vous pouvez également utiliser des solutions DRM tierces comme alternative à la solution intégrée d’Adobe.

Contactez votre représentant d’Adobe pour obtenir les informations les plus récentes sur la disponibilité de solutions DRM tierces.

<!--<a id="section_1385440013EF4A9AA45B6AC98919E662"></a>-->

Vous pouvez utiliser Android native Widevine DRM avec des flux CMAF HLS.

>[!NOTE]
>
> Le schéma de CTR CENC étendu nécessite Android version 4.4 minimum (API Niveau 19).
>
> Le schéma d’extension CBCS nécessite Android version 7.1 au minimum (API Niveau 25).

## Définition des détails du serveur de licences {#license-server-details}

Appelez ce qui suit `com.adobe.mediacore.drm.DRMManager` API avant de charger la ressource MediaPlayer :

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

Par exemple, lors de l’utilisation de contenu mis en package pour Expressplay DRM, utilisez le code suivant avant la lecture :

```java
DRMManager.setProtectionData(
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null);
```

## Fournir un rappel personnalisé {#custom-callback}

Appelez ce qui suit `com.adobe.mediacore.drm.DRMManager` API avant de charger la ressource MediaPlayer.

```java
public static void setMediaDrmCallback(
MediaDrmCallback callback)
```

### Arguments {#arguments-custom-callback}

* `callback` : mise en oeuvre personnalisée de MediaDrmCallback pour utiliser au lieu de la valeur par défaut `com.adobe.mediacore.drm.WidevineMediaDrmCallback`.

Pour plus d’informations, voir [Documentation de l’API Android TVSDK 3.11](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.11/index.html).

## Récupérer la zone PSSH de la ressource MediaPlayer actuellement chargée {#pssh-box-mediaplayer-resoource}

Appelez ce qui suit `com.adobe.mediacore.drm.DRMManager` API, de préférence dans une implémentation de rappel personnalisée.

```java
public static byte[] getPSSH()
```

L’API renvoie la zone d’en-tête spécifique au système de protection associée à la ressource multimédia Widevine chargée.

Une boîte valide est disponible pour une courte durée (entre la création de l&#39;instance DRM et le chargement des clés). `MediaDrmCallback callback executeKeyRequest()` peut l’utiliser pour personnaliser la récupération des clés de licence.

>[!NOTE]
>
> `getPSSH()` L’API est prise en charge avec une seule instance de lecteur uniquement. Plusieurs lecteurs ou la fonction Instant On doit s’initialiser en série pour recevoir la case appropriée.
