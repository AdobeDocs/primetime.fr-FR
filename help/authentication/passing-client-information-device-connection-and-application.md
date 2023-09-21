---
title: Transmission des informations client (appareil, connexion et application)
description: Transmission des informations client (appareil, connexion et application)
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1681'
ht-degree: 0%

---

# Transmission des informations client (appareil, connexion et application) {#pass-client-info}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.


## Portée {#pass-client-info-scope}

Ce document agrège les détails et les livres de cookie pour transmettre des informations client (appareil, connexion et application) d’une application de programmeur aux API REST d’authentification Adobe Primetime ou aux SDK.

Les avantages de fournir des informations sur le client sont les suivants :

* La possibilité d’activer correctement l’authentification de base (adaptateur de bus hôte) dans le cas de certains types d’appareils et MVPD pouvant prendre en charge l’adaptateur de bus hôte.
* La possibilité d’appliquer correctement des TTL dans le cas de certains types d’appareils (par exemple, configurer des TTL plus longs pour les sessions d’authentification sur les appareils connectés à la télévision).
* La possibilité d’agréger correctement les mesures commerciales dans des rapports ventilés entre types d’appareils à l’aide du contrôle du service de droits (ESM).
* Débloque la possibilité d’appliquer correctement diverses règles de fonctionnement (par exemple, dégradation) sur des types d’appareils spécifiques.

## Présentation {#pass-client-info-overview}

Les informations du client sont les suivantes :

* **Appareil** informations sur les attributs matériels et logiciels de l’appareil à partir duquel l’utilisateur tente d’utiliser le contenu du programmeur.
* **Connexion** des informations sur les attributs de connexion de l’appareil à partir duquel l’utilisateur se connecte aux services d’authentification Adobe Primetime et/ou aux services de programmeur (par exemple, implémentations serveur à serveur).
* **Application** informations sur l’application enregistrée à partir de laquelle l’utilisateur tente d’utiliser le contenu du programmeur.

Les informations client sont un objet JSON créé avec des clés présentées dans le tableau suivant.

>[!NOTE]
>
>Les éléments suivants **keys** are **mandatory** à envoyer dans l’objet JSON d’informations client : **model**, **osName**.
>
>Les clés suivantes sont **Restriction** values : `primaryHardwareType`, `osName`, `osFamily`, `browserName`, `browserVendor`, `connectionSecure`.

|   | Clé | Restricted | Description | Valeurs possibles |
|---|---|---|---|---|
|            | primaryHardwareType | # Oui | Type matériel principal de l’appareil. | # Les valeurs sont restreintes : Camera DataCollectionTerminal Desktop EmbeddedNetworkModule eReader GamesConsole GéolocationTracker Lunettes MediaPlayer MobilePhone paiementTerminal PluginModem SetTopBox TV Tablet WirelessHotspot Wristwatch Inconnu |
| #mandatory | model | Non | Nom du modèle de l’appareil. | par exemple iPhone, SM-G930V, Apple TV, etc. |
|            | version | Non | Version de l’appareil. | par exemple, 2.0.1, etc. |
|            | manufacturer | Non | Entreprise/organisation de fabrication de l’appareil. | Par exemple, Samsung, LG, ZTE, Huawei, Motorola, Apple, etc. |
|            | vendor | Non | Entreprise/organisation de vente de l’appareil. | par exemple Apple, Samsung, LG, Google, etc. |
| #mandatory | osName | # Oui | Nom du système d’exploitation du périphérique. | # Les valeurs sont restreintes : Android Chrome OS Linux Mac OS X OpenBSD Roku OS Windows iOS tvOS webOS |
|            | osFamily | Oui | Nom du groupe Système d’exploitation du périphérique. | # Les valeurs sont restreintes : Android BSD Linux PlayStation OS Roku OS Symbian Tizen Windows iOS macOS tvOS webOS |
|            | osVendor | Non | Fournisseur du système d’exploitation du périphérique. | Amazon Apple Google LG Microsoft Mozilla Nintendo Nokia Roku Samsung Projet Sony Tizen |
|            | osVersion | Non | Version du système d’exploitation du périphérique. | par exemple, 10.2, 9.0.1, etc. |
|            | browserName | # Oui | Nom du navigateur. | # Les valeurs sont restreintes : navigateur Android Chrome Edge Firefox Internet Explorer Opera Safari SeaMonkey Symbian Browser |
|            | browserVendor | # Oui | Entreprise/organisation de construction du navigateur. | # Les valeurs sont restreintes : Amazon Apple Google Microsoft Motorola Mozilla Netscape Nintendo Nokia Samsung Sony Ericsson |
|            | browserVersion | Non | Version du navigateur de l’appareil. | par exemple, 60.0.3112 |
|            | userAgent | Non | L’agent utilisateur de l’appareil. | Par exemple, Mozilla/5.0 (Macintosh ; Intel Mac OS X 10_12_3) AppleWebKit/602.4.8 (KHTML, comme Gecko) Version/10.0.3 Safari/602.4.8 |
|            | displayWidth | Non | Largeur d’écran physique de l’appareil. |                                                                                                                                                                                                                                                                                                                                                           |
|            | displayHeight | Non | Hauteur d’écran physique de l’appareil. |                                                                                                                                                                                                                                                                                                                                                           |
|            | displayPpi | Non | Densité physique des pixels de l’écran de l’appareil. | par exemple, 294 |
|            | diagonalScreenSize | Non | Dimension diagonale de l’écran physique de l’appareil en pouces. | par exemple, 5.5, 10.1 |
|            | connectionIp | Non | Adresse IP de l’appareil utilisée pour envoyer des requêtes HTTP. | par exemple, 8.8.4.4 |
|            | connectionPort | Non | Port de l’appareil utilisé pour envoyer des requêtes HTTP. | Par exemple, 53124 |
|            | connectionType | Non | Type de connexion réseau. | Par exemple, Wi-Fi, LAN, 3G, 4G, 5G |
|            | connectionSecure | # Oui | État de sécurité de la connexion réseau. | # Les valeurs sont restreintes : true - dans le cas d’un réseau sécurisé false - dans le cas d’une zone réactive publique |
|            | applicationId | Non | Identifiant unique de l’application. | Par exemple, CNN |

## Références API {#api-ref}

Cette section présente l’API chargée de gérer les informations sur les clients lors de l’utilisation des API REST d’authentification Adobe Primetime ou des SDK.

### API REST {#rest-api}

Les services d’authentification Adobe Primetime prennent en charge la réception des informations client de la manière suivante :

* Comme **header: &quot;X-Device-Info&quot;**
* Comme **Paramètre de requête : &quot;device_info&quot;**
* Comme **Paramètre post : &quot;device_info&quot;**

>[!IMPORTANT]
>
>Dans les trois scénarios, la charge utile de l’en-tête ou du paramètre doit être **Codé en Base64 et encodé en URL**.

**SDK**

#### SDK JavaScript {#js-sdk}

Le SDK JavaScript AccessEnabler crée par défaut un objet JSON d’informations client, qui sera transmis aux services d’authentification Adobe Primetime, sauf s’il est remplacé.

Le SDK JavaScript AccessEnabler prend en charge **remplacement uniquement** la clé &quot;applicationId&quot; de l’objet JSON d’informations client via l’objet [setRequestor](/help/authentication/javascript-sdk-api-reference.md#setrequestor(inRequestorID,endpoints,options))&#39;s *applicationId* paramètre options .

>[!CAUTION]
>
>La variable `applicationId` La valeur du paramètre doit être une valeur Chaîne en texte brut.
>Si l’application de programmation décide de transmettre l’applicationId, le reste des clés d’informations client sera toujours calculé par le SDK JavaScript AccessEnabler.

#### SDK iOS/tvOS {#ios-tvos-sdk}

Le SDK AccessEnabler iOS/tvOS crée par défaut un objet JSON d’informations client, qui sera transmis aux services d’authentification Adobe Primetime, sauf s’il est remplacé.

Le SDK AccessEnabler iOS/tvOS prend en charge **remplacer l’ensemble** objet JSON d’informations client via [setOptions](/help/authentication/iostvos-sdk-api-reference.md#setoptions)Paramètre device_info de .

>[!CAUTION]
>
>La variable *device_info* La valeur du paramètre doit être **Codé en Base64** *NSString* .
>
>Si l’application de programmation décide de transmettre la variable *device_info*, toutes les clés d’informations client calculées par le SDK AccessEnabler iOS/tvOS seront remplacées. Il est donc très important de calculer et de transmettre les valeurs pour autant de clés que possible. Pour plus d’informations sur l’implémentation, voir [Présentation](#pass-client-info-overview) et le [Manuel iOS/tvOS](#ios-tvos).

#### SDK Android/FireOS {#and-fire-os-sdk}

La variable `AccessEnabler` Le SDK Android/FireOS crée par défaut un objet JSON d’informations client, qui sera transmis aux services d’authentification Adobe Primetime, sauf s’il est remplacé.

La variable `AccessEnabler` Le SDK Android/FireOS prend en charge **remplacer l’ensemble** objet JSON d’informations client via [setOptions](/help/authentication/android-sdk-api-reference.md#setOptions)&#39;s/[setOptions](/help/authentication/amazon-fireos-native-client-api-reference.md#fire_setOption)&#39;s `device_info` .

>[!NOTE]
>
>La variable `device_info` La valeur du paramètre doit être **Codé en Base64** Valeur de chaîne.

>[!IMPORTANT]
>
>Si l’application de programmation décide de transmettre la variable `device_info`, puis toutes les clés d’informations client calculées par la variable `AccessEnabler` Le SDK Android/FireOS sera remplacé. Il est donc très important de calculer et de transmettre les valeurs pour autant de clés que possible. Pour plus d’informations sur l’implémentation, voir [Présentation](#pass-client-info-overview) et le [Android](#android) et [FireOS](#fire-tv) livre de cuisine.

## Cookbooks {#cookbooks}

Cette section présente un guide pas à pas pour créer l’objet JSON d’informations sur le client dans le cas de différents types d’appareils.

>[!IMPORTANT]
>
>Les clés marquées de  **!** sont obligatoires pour être envoyés.

### Android {#android}

Les informations sur l’appareil peuvent être construites comme suit :

|   | Clé | Source | Valeur (exemple) |
|---|---------------|-----------------------------|---------------|
| ! | model | Build.MODEL | GT-I9505 |
|   | vendor | Build.BRAND | samsung |
|   | manufacturer | Build.MANUFACTURER | samsung |
| ! | version | Build.DEVICE | jflte |
|   | displayWidth | DisplayMetrics.widthPixels | 600 |
|   | displayHeight | DisplayMetrics.heightPixels | 800 |
| ! | osName | codé en dur | Android |
| ! | osVersion | Build.VERSION.RELEASE | 5.0.1 |

Les informations de connexion peuvent être construites comme suit :

|   | Clé | Source | Valeur (exemple) |
|---|---|---|---|
| ! | connectionType | `<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>` `getSystemService(Context.CONNECTIVITY_SERVICE).getActiveNetworkInfo().getType()` | `"WIFI","BLUETOOTH","MOBILE","ETHERNET","VPN","DUMMY","MOBILE_DUN","WIMAX","notAccessible"` |
|   | connectionSecure |                                                                                                                                                           |                                                                                           |

Les informations de l’application peuvent être construites comme suit :

|   | Clé | Source | Valeur (exemple) |
|---|---------------|-----------|--------------|
|   | applicationId | codé en dur | CNN |

>[!IMPORTANT]
>
Les informations sur l’appareil, la connexion et l’application doivent être ajoutées au même objet JSON. Ensuite, l’objet obtenu doit être **Codé en Base64**. En outre, dans le cas des API REST d’authentification Adobe Primetime, la valeur doit être **encodé URL**.

**Exemple de code**

```JAVA
private JSONObject computeClientInformation() {
     String LOGGING_TAG = "DefineClass.class";
  
     JSONObject clientInformation = new JSONObject();

     String connectionType;

     try {
          ConnectivityManager cm = (ConnectivityManager) getContext().getSystemService(CONNECTIVITY_SERVICE);
          NetworkInfo activeNetwork = cm.getActiveNetworkInfo();

          if (activeNetwork != null && activeNetwork.isConnectedOrConnecting()) {
              switch (activeNetwork.getType()) {
                    case ConnectivityManager.TYPE_WIFI: {
                        connectionType = "WIFI";
                        break;
                    }
                    case ConnectivityManager.TYPE_BLUETOOTH: {
                        connectionType = "BLUETOOTH";
                        break;
                    }
                    case ConnectivityManager.TYPE_MOBILE: {
                        connectionType = "MOBILE";
                        break;
                    }
                    case ConnectivityManager.TYPE_ETHERNET: {
                        connectionType = "ETHERNET";
                        break;
                    }
                    case ConnectivityManager.TYPE_VPN: {
                        connectionType = "VPN";
                        break;
                    }
                    case ConnectivityManager.TYPE_DUMMY: {
                        connectionType = "DUMMY";
                        break;
                    }
                    case ConnectivityManager.TYPE_MOBILE_DUN: {
                        connectionType = "MOBILE_DUN";
                        break;
                    }
                    case ConnectivityManager.TYPE_WIMAX: {
                        connectionType = "WIMAX";
                        break;
                    }
                    default:
                       connectionType = ConnectivityManager.EXTRA_OTHER_NETWORK_INFO;
              }
          } else {
                connectionType = ConnectivityManager.EXTRA_NO_CONNECTIVITY;
          }
     } catch (Exception e) {
          connectionType = "notAccessible";
     }

     try {
          clientInformation.put("model",Build.MODEL);
          clientInformation.put("vendor", Build.BRAND);
          clientInformation.put("manufacturer",Build.MANUFACTURER);
          clientInformation.put("version",Build.DEVICE);
          clientInformation.put("osName","Android");
          clientInformation.put("osVersion",Build.VERSION.RELEASE);
          clientInformation.put("connectionType",connectionType);
          clientInformation.put("applicationId","CNN");
     } catch (JSONException e) {
          Log.e(LOGGING_TAG, e.getMessage());
     }

     return Base64.encodeToString(clientInformation.toString().getBytes(), Base64.NO_WRAP);
}
```

>[!NOTE]
>
**Ressources :**
* classe publique [build](https://developer.android.com/reference/android/os/Build.html){target=_blank} dans la documentation destinée aux développeurs Java.

### FireTV {#fire-tv}

Les informations sur l’appareil peuvent être construites comme suit :

|   | Clé | Source | Valeur (par ex.) |
|---|---------------|-----------------------------|--------------|
| ! | model | Build.MODEL | AFTM |
|   | vendor | Build.BRAND | Amazon |
|   | manufacturer | Build.MANUFACTURER | Amazon |
| ! | version | Build.DEVICE | montoya |
|   | displayWidth | DisplayMetrics.widthPixels |              |
|   | displayHeight | DisplayMetrics.heightPixels |              |
| ! | osName | codé en dur | Android |
| ! | osVersion | Build.VERSION.RELEASE | 5.1.1 |

Les informations de connexion peuvent être construites comme suit :

|   | Clé | Source | Valeur (exemple) |
|---|------------------|--------|---------------|
| ! | connectionType |        |               |
|   | connectionSecure |        |               |

Les informations de l’application peuvent être construites comme suit :

|   | Clé | Source | Valeur (exemple) |
|---|---------------|-----------|--------------|
|   | applicationId | codé en dur | CNN |

>[!IMPORTANT]
>
Les informations sur l’appareil, la connexion et l’application doivent être ajoutées au même objet JSON. Ensuite, l’objet obtenu doit être **Codé en Base64**. En outre, dans le cas des API REST d’authentification Adobe Primetime, la valeur doit être **encodé URL**.

>[!NOTE]
>
**Ressources :**
* classe publique [Build](https://developer.android.com/reference/android/os/Build.html){target=_blank} dans la documentation des développeurs Android.
* [Identification des appareils FireTV](https://developer.amazon.com/docs/fire-tv/identify-amazon-fire-tv-devices.html){target=_blank}

### iOS/tvOS {#ios-tvos}

Les informations sur l’appareil peuvent être construites comme suit :

|   | Clé | Source | Valeur (exemple) |
|---|---------------|------------------------|--------------|
| ! | model | uname.machine | iPhone |
|   | vendor | codé en dur | Apple |
|   | manufacturer | codé en dur | Apple |
| ! | version | uname.machine | 8,1 |
|   | displayWidth | UIScreen.mainScreen | 320 |
|   | displayHeight | UIScreen.mainScreen | 568 |
| ! | osName | UIDevice.systemName | iOS |
| ! | osVersion | UIDevice.systemVersion | 10.2 |

Les informations de connexion peuvent être construites comme suit :

|   | Clé | Source | Valeur (exemple) |
|---|------------------|-------------------------------------------|--------------|
| ! | connectionType | [currentReachabilityStatus] |              |
|   | connectionSecure |                                           |              |


Les informations de l’application peuvent être construites comme suit :

|   | Clé | Source | Valeur (exemple) |
|---|---------------|-----------|--------------|
|   | applicationId | codé en dur | CNN |

>[!IMPORTANT]
>
Les informations sur l’appareil, la connexion et l’application doivent être ajoutées au même objet JSON. Par la suite, l’objet obtenu doit être encodé en Base64. En outre, dans le cas des API REST d’authentification Adobe Primetime, la valeur doit être en codage URL.

**Exemple de code**

```C
+ (NSString *)computeClientInformation {        
        struct utsname u;
        uname(&u);

        NSString *hardware = [NSString stringWithCString:u.machine encoding:NSUTF8StringEncoding];

        UIDevice *device = [UIDevice currentDevice];

        NSString *deviceType;

        switch (UI_USER_INTERFACE_IDIOM()) {
            case UIUserInterfaceIdiomPhone:
                deviceType = @"MobilePhone";
                break;
            case UIUserInterfaceIdiomPad:
                deviceType = @"Tablet";
                break;
            case UIUserInterfaceIdiomTV:
                deviceType = @"TV";
                break;
            default:
                deviceType = @"Unknown";
        }

        CGRect screenRect = [[UIScreen mainScreen] bounds];
        NSNumber *screenWidth = @((float) screenRect.size.width);
        NSNumber *screenHeight = @((float) screenRect.size.height);

        Reachability *reachability = [Reachability reachabilityForInternetConnection];
        [reachability startNotifier];

        NetworkStatus status = [reachability currentReachabilityStatus];

        NSString *connectionType;

        if (status == NotReachable) {
            connectionType = @"notConnected";
        } else if (status == ReachableViaWiFi) {
            connectionType = @"WiFi";
        } else if (status == ReachableViaWWAN) {
            connectionType = @"cellular";
        }

        NSMutableDictionary *clientInformation = [@{
                @"type": deviceType,
                @"model": device.model,
                @"vendor": @"Apple",
                @"manufacturer": @"Apple",
                @"version": [hardware stringByReplacingOccurrencesOfString:device.model withString:@""],
                @"osName": device.systemName,
                @"osVersion": device.systemVersion,
                @"displayWidth": screenWidth,
                @"displayHeight": screenHeight,
                @"connectionType": connectionType,
                @"applicationId": @"CNN" 
        } mutableCopy];

        NSError *error;
        NSData *jsonData = [NSJSONSerialization dataWithJSONObject:clientInformation options:NSJSONWritingPrettyPrinted error:&error];
        NSString *base64Encoded = [jsonData base64EncodedStringWithOptions:0];

        return base64Encoded;
}
```

>[!NOTE]
>
**Ressources :**
* [UIDevice](https://developer.apple.com/documentation/uikit/uidevice#//apple_ref/occ/cl/UIDevice){target=_blank}
* [uname](https://man7.org/linux/man-pages/man2/uname.2.html){target=_blank}
* [À propos de la faisabilité](https://developer.apple.com/library/archive/samplecode/Reachability/Introduction/Intro.html){target=_blank}

### Roku {#roku}

Les informations sur l’appareil peuvent être construites comme suit :

| Clé | Source | Valeur (exemple) |                 |
|-----|---------------|--------------------------------------------|-----------------|
| ! | model | codé en dur | Roku |
|     | vendor | ifDeviceInfo.GetModelDetails().VendorName | &quot;Sharp&quot;, &quot;Roku&quot; |
|     | manufacturer | ifDeviceInfo.GetModelDetails().VendorName | &quot;Sharp&quot;, &quot;Roku&quot; |
| ! | version | ifDeviceInfo.GetModelDetails().ModelNumber | &quot;5303X&quot; |
|     | displayWidth | ifDeviceInfo.GetDisplaySize().w | 1920 |
|     | displayHeight | ifDeviceInfo.GetDisplaySize().h | 1080 |
| ! | osName | codé en dur | Roku |
| ! | osVersion | ifDeviceInfo.getVersion() |                 |

Les informations de connexion peuvent être construites comme suit :

|   | Clé | Source | Valeur (exemple) |
|---|---|---|---|
| ! | connectionType | ifDeviceInfo.GetConnectionType() | &quot;WifiConnection&quot;, &quot;WiredConnection&quot; |
|   | connectionSecure | codé en dur | true si la connexion est connectée |

Les informations de l’application peuvent être construites comme suit :

|   | Clé | Source | Valeur (exemple) |
|---|---------------|-----------|--------------|
|   | applicationId | codé en dur | CNN |

>[!IMPORTANT]
>
Les informations sur l’appareil, la connexion et l’application doivent être ajoutées au même objet JSON. Ensuite, l’objet obtenu doit être **Codé en Base64**. En outre, dans le cas des API REST d’authentification Adobe Primetime, la valeur doit être en codage URL.

>[!NOTE]
>
Pour plus d’informations, voir [ifDeviceInfo](https://developer.roku.com/docs/references/brightscript/interfaces/ifdeviceinfo.md)

### XBOX 1/360 {#xbox}

Les informations sur l’appareil peuvent être construites comme suit :

|   | Clé | Source | Valeur (exemple) |
|---|---|---|---|
| ! | model | EasClientDeviceInformation.SystemProductName |                 |
|   | vendor | codé en dur | Microsoft |
|   | manufacturer | codé en dur | Microsoft |
| ! | version | EasClientDeviceInformation.SystemHardwareVersion |                 |
|   | displayWidth | DisplayInformation.ScreenWidthInRawPixels | 1920 |
|   | displayHeight | DisplayInformation.ScreenHeightInRawPixels | 1080 |
| ! | osName | EasClientDeviceInformation.OperatingSystem |                 |
| ! | osVersion | EasClientDeviceInformation.SystemFirmwareVersion |                 |

Les informations de connexion peuvent être construites comme suit :

|   | Clé | Source | Exemple |
|---|---|---|---|
| ! | connectionType |                                                   |                   |
|   | connectionSecure | NetworkAuthenticationType | &quot;Aucun&quot;, &quot;Wpa&quot;, etc. |

Les informations de l’application peuvent être construites comme suit :

| Clé | Source | Valeur (exemple) |
|---|---|---|
| applicationId | codé en dur | CNN |

>[!IMPORTANT]
>
Les informations sur l’appareil, la connexion et l’application doivent être ajoutées au même objet JSON. Ensuite, l’objet obtenu doit être **Codé en Base64**. En outre, dans le cas des API REST d’authentification Adobe Primetime, la valeur doit être **encodé URL**.

**Ressources**

* [Classe EasClientDeviceInformation](https://docs.microsoft.com/en-us/uwp/api/windows.security.exchangeactivesyncprovisioning.easclientdeviceinformation?view=winrt-22000)
* [Classe DisplayInformation](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.display.displayinformation?view=winrt-22000)
