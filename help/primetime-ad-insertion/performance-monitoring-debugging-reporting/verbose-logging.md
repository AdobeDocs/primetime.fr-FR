---
title: Journalisation détaillée
description: null
translation-type: tm+mt
source-git-commit: d5e948992d7c59e80b530c8f4619adbffc3c03d8
workflow-type: tm+mt
source-wordcount: '2155'
ht-degree: 0%

---


# Journalisation détaillée {#verbose-logging}

## Descriptions du événement ptdebug/logging {#ptdebug-logging-events}

Lors de l&#39;ouverture de la journalisation du débogage d&#39;une session de serveur de manifeste, vous pouvez ajouter le paramètre `ptdebug` à l&#39;URL de demande afin de spécifier les options suivantes pour les informations que le serveur de manifeste renvoie dans les en-têtes HTTP :

* `ptdebug=true`
Tous les enregistrements, à l&#39;exception de TRACE_HTTP_HEADER et la plupart des données d&#39;appel/réponse des enregistrements TRACE_AD_CALL.

* `ptdebug=AdCall`
Seul le type TRACE_AD_ (par exemple, TRACE_AD_CALL) enregistre.

* `ptdebug=Header`
Seuls les enregistrements TRACE_HTTP_HEADER sont enregistrés.

## Formats des enregistrements de journal {#log-record-formats}

Chaque enregistrement de journal comporte un type et un ensemble de champs, dont certains peuvent être facultatifs. Les champs de tous les enregistrements jusqu&#39;au type d&#39;enregistrement sont identiques. Ils fournissent un horodatage et des informations sur la session. Le type d’enregistrement identifie le type de événement en cours de journalisation et les champs suivants fournissent des informations sur le événement consigné.

La structure d&#39;un enregistrement de journal est la suivante :

`datetime request_id session_id zone_id record_type other fields`.

| Champ | Type | Description |
|---|---|---|
| datetime | string | Horodatage |
| request_id | string | ID de demande utilisé par le serveur de manifeste (horodatage Unix) |
| session_id | string | ID de session utilisé par le serveur de manifeste |
| zone_id | integer | Zone |
| record_type | string | Type de événement en cours de journalisation |
| autres champs | varie | Dépend du type de événement |

Les enregistrements de ce type enregistrent les résultats des requêtes HTTP. Les champs au-delà de `TRACE_REQUEST_INFO` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| statut | string | Code d’état HTTP renvoyé |
| request_method | string | Méthode HTTP (GET ou POST) |
| request_uri | string | URI de requête HTTP (sans hôte) |
| request_length | integer | Longueur de la requête (octets) |
| response_length | integer | Longueur de la réponse (octets) |
| delta | integer | Temps (millisecondes) nécessaire au traitement de la demande |
| module_type | string | Variante, Diffusion en continu ou VOD |
| remote_address_aud_client_ip | string | **†** |
| remote_address_x_fwd_for_hdr_key | string | **†** |
| remote_host_port | string | **†** |

**** Les trois derniers champs sont facultatifs.

**Exemple**

```shell
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### TRACE_HTTP_HEADER enregistrements {#trace-http-header-records}

Les enregistrements de ce type consignent les en-têtes HTTP échangés lors des appels HTTP entre le serveur de manifeste et le client, le serveur d’annonces ou le serveur de contenu. Les champs situés au-delà de TRACE_HTTP_HEADER s’affichent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| request_type | string | Type de demande (MAIN ou UNKNOWN) |
| request_response | string | En-tête de réponse (requête ou réponse) |
| header_name | string | Nom de l’en-tête HTTP |
| header_value | string | Valeur d’en-tête HTTP codée en base 64 |

>[!NOTE]
>
>Les champs `request_type` et `header_value` sont facultatifs.

**Exemple**

```shell
2015-03-25T06:10:00.927Z 1427263800573 6495aa. . . 189938 TRACE_MISC Requesting: /cnn/tvecnn/stream4/stream_Layer.m3u8
2015-03-25T06:10:00.927Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN REQUEST Cookie aGRu. . .
2015-03-25T06:10:00.928Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN REQUEST User-Agent TW96aW. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Server bmd4X2. . .
2015-03-25T06:10:01.063Z  1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Content-Type YXBwb. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Last-Modified V2VkL. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE ETag IjIyY2. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Vary QWNjZXB. . .
2015-03-25T06:10:01.063Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Cache-Control bWF4LW. . .
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Expires V2VkL. . .
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Date V2VkLCA. . .
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Age MQ==
2015-03-25T06:10:01.064Z 1427263800573 6495aa. . . 189938 TRACE_HTTP_HEADER UNKNOWN RESPONSE Via MS4xIH. . .
```

### TRACE_AD_CALL enregistrements {#tracing-ad-call-records}

Les enregistrements de ce type consignent les résultats des demandes d&#39;annonce du serveur de manifeste. Les champs au-delà de `TRACE_AD_CALL` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| statut | string | Code d’état HTTP renvoyé |
| request_duration | integer | Temps (millisecondes) entre la requête et la réponse |
| ad_server_requête_url | string | URL de l’appel publicitaire, y compris les paramètres de requête |
| ad_system_id | string | Système publicitaire, à partir de la réponse du serveur publicitaire (Auditude si elle n’est pas spécifiée) |
| avail_id | string | ID de la valeur, à partir du repère publicitaire dans le fichier manifeste de contenu (S/O pour VOD) |
| avail_duration | nombre | Durée (secondes) de la valeur, à partir du repère publicitaire dans le fichier manifeste de contenu (S/O pour VOD) |
| ad_server_response | string | Réponse codée en base 64 du serveur d’annonces |

Exemple :

```shell
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### TRACE_AD_INSERT, TRACE_AD_RESOLVE et TRACE_AD_REDIRECT enregistrements {#trace-ad-insert-resolve-redirect}

Les enregistrements de ce type consignent les résultats des demandes d&#39;annonce indiquées par le type d&#39;enregistrement. Les champs situés au-delà du type d’enregistrement s’affichent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| statut | string | Code d’état HTTP renvoyé. |
| avail_id | string | Identifiant de la valeur, à partir de l’indice publicitaire dans le fichier de manifeste de contenu (en direct) ou du serveur de manifeste (VOD). |
| ad_type | string | Type de publicité (DIRECT ou REDIRECT). |
| ad_duration | integer | Durée (secondes) de la publicité, d’après la réponse du serveur publicitaire. |
| ad_content_url | string | URL du fichier manifeste de la publicité, à partir de la réponse du serveur de publicité. |
| **†** ad_content_url_real | string | URL du fichier manifeste de l’annonce insérée. Vide pour TRACE_AD_REDIRECT. |
| ad_system_id | string | Système publicitaire, à partir de la réponse du serveur publicitaire (Auditude si elle n’est pas spécifiée). |
| ad_id | string | ID de la publicité, à partir de la réponse du serveur d’annonces. |
| creative_id | string | ID du créatif, à partir du noeud publicitaire, de la réponse du serveur publicitaire. |
| **†** ad_call_id | string | Non utilisé. Réservé pour une utilisation ultérieure. |
| delta | integer | Temps (millisecondes) pris par ce événement. |
| **†** divers | string | Raison pour laquelle la publicité a été ignorée. |

**†** `ad_content_url_actual`Les  `ad_call_id`champs et  `misc` les champs sont facultatifs.

>[!NOTE]
>
>Pour `TRACE_AD_RESOLVE` et `TRACE_AD_INSERT`, l’URL du champ `ad_content_url_actual` correspond à la publicité transcodée si elle est disponible. Sinon, le champ est vide pour `TRACE_AD_RESOLVE` ou identique à `ad_content_url` pour `TRACE_AD_INSERT`.

Exemple :

```shell
2015-03-18T22:25:36.229-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.230-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.562-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.563-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
```

<!-- ### TRACE_TRACKING_URL records {#trace-tracking-url-records}

Records of this type log the results of manifest server ad requests. Fields beyond `TRACE_TRACKING_URL` appear in the order shown in the table, separated by tabs.

| Field | Type | Description |
|---|---|---|
| pts | number | Program timestamp. Time within video to call the URL. |
| ad_system | string | Ad system (auditude or freewheel) |
| url | string | URL pinged |
| status | string | HTTP status returned from the ping |

```shell
2015-06-04T23:24:42.000-0700 1426742736208 3086f5cd . . . 12345 TRACE_TRACKING_URL 0.000000 ExampleSystem https://localhost/index.php?stream:test#8.1433485415; sid:3086f5cd . . .;pts:0 200
```

-->

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE enregistrements {#trace-transcoding-no-media-to-transcode}

Les enregistrements de ce type consignent un élément publicitaire manquant. Le seul champ au-delà de `TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE` apparaît dans le tableau.

| Champ | Type | Description |
|---|---|---|
| ad_id | string | ID d’annonce complète (FQ_AD_ID : Q_AD_ID\[;Q_AD_ID\[;Q_AD_ID...\] \] Q_AD_ID : PROTOCOLE:AD_SYSTEM:AD_ID\[:CREATIVE_ID\[:MEDIA_ID\] \] PROTOCOLE : AUDITUDE, VAST) |

Les enregistrements de ce type consignent les résultats des demandes de transcodage que le serveur de manifeste envoie à CRS. Les champs au-delà de `TRACE_TRANSCODING_REQUESTED` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| ad_id | string | ID publicitaire complet |
| ad_manifest_url | string | URL du fichier manifeste de la publicité, à partir de la réponse du serveur d’annonces |
| creative_type | string | Type de support |
| indicateurs | string | ID3 indique si la demande de transcodage inclut une demande d’ajout d’une balise ID3. |
| cible_duration | string | Durée de cible (en secondes) de l’élément créatif transcodé |

Les enregistrements de ce type indiquent une demande de suivi côté serveur. Les champs au-delà de `TRACE_TRACKING_REQUEST` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| tracking_url_count | integer | Nombre d’URL de suivi |
| début | flotter | Début du fragment PTS (secondes avec une précision de milliseconde) |
| end | flotter | Heure de fin du fragment PTS (secondes avec une précision de milliseconde) |

Les enregistrements de ce type fournissent une URL de suivi pour le suivi côté serveur. Les champs au-delà de `TRACE_TRACKING_REQUEST_URL` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| timestamp | flotter | Durée (en secondes, avec précision 0,001) de la session de lecture jusqu’à l’exécution d’un test ping sur l’URL de suivi. |
| ad_system | string | Système publicitaire (par exemple, auditude) |
| url | string | URL vers ping |

Les enregistrements de ce type de journal demandent que le serveur manifeste crée des légendes `WEBVTT`. Les champs au-delà de `TRACE_WEBVTT_REQUEST` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| statut | string | Code d’état HTTP renvoyé |
| vtt_uri | string | URL de la demande |
| début | flotter | Temps début fractionné (secondes avec précision de milliseconde) |
| end | flotter | Temps de fin fractionné (secondes avec précision de milliseconde) |

Enregistrements de ce type de réponses au journal que le serveur de manifeste envoie aux clients dans `answer` aux demandes de légendes `WEBVTT`. Les champs au-delà de `TRACE_WEBVTT_RESPONSE` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| statut | string | Code d’état HTTP renvoyé |
| réponse | string | Réponse codée en base 64 envoyée au client |

Enregistrements de ce type de réponses au journal des demandes que le serveur manifeste fait pour des légendes `WEBVTT`. Les champs au-delà de `TRACE_WEBVTT_SOURCE` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| statut | string | Code d’état HTTP renvoyé |
| source | string | Contenu VTT d’origine codé en base 64 |

Les enregistrements de ce type permettent au serveur de manifeste de consigner les événements et les informations non planifiées lors de l&#39;assimilation de publicités. Le champ situé au-delà de `TRACE_MISC` est constitué d&#39;une chaîne de message. Les messages qui peuvent s’afficher sont les suivants :

* La publicité a ignoré : AdPlacement \[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . . .m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1\]
* AdPlacement adManifestURL= adManifestURL, durationSeconds= secondes, ignore= ignore, redirectAd= redirectAd, priority= priority
* L’emplacement de la publicité a renvoyé la valeur null.
* La publicité a été assemblée avec succès.
* Échec de l&#39;appel de publicité : message d’erreur.
* Ajouter User-Agent à récupérer le manifeste brut : user-agent.
* Ajouter un cookie pour récupérer le manifeste brut : #
* Message d&#39;erreur d&#39;URL requis incorrect. (Échec de l&#39;analyse de l&#39;URL de variante)
* URL appelée : URL renvoyée : code de réponse. (URL active)
* URL appelée : Code de retour d’URL : code de réponse. (URL VOD)
* Conflit détecté lors de la résolution des publicités : l&#39;un ou l&#39;autre des débuts - milieu ou milieu de la gamme est compris dans les modèles pré-rouleau ou pré-rouleau contenus dans le milieu de la gamme (VOD).
* Exception non gérée détectée générée par le gestionnaire pour URI : URL de requête.
* Génération du manifeste de variante terminée. (Variant)
* Génération du manifeste de variante terminée.
* Exception lors de la gestion de la redirection VAST *redirect URL *error: message d’erreur.
* Échec de la récupération de la liste de lecture de la publicité pour l&#39;URL du manifeste de la publicité.
* Échec de la génération du manifeste ciblé. (HLSManifestResolver)
* Échec de l&#39;analyse de la première réponse d&#39;appel publicitaire : message d’erreur.
* Échec du traitement de la *GET|POST *demande de chemin d&#39;accès : URL de requête. (Live/VOD)
* Échec du traitement de la demande de manifeste en direct : URL de requête. (En direct)
* Impossible de renvoyer un manifeste de variante : message d’erreur.
* Échec de la validation de l&#39;identifiant de groupe : ID de groupe.
* Récupération du manifeste brut : URL du contenu. (En direct)
* Après la redirection VAST : URL de redirection.
* Disponibilités vides trouvées. (VOD)
* *nombre* publicités trouvées. (VOD)
* Demande HTTP reçue. (Tout premier message)
* La publicité est ignorée car la différence entre la durée de réponse de la publicité (*durée de réponse de la publicité *s) et la durée de la publicité réelle (*durée réelle *s) est supérieure à la limite. (HLSManifestResolver)
* Valeur qui n’a fourni aucune valeur d’ID ignorée. (GroupAdResolver.java)
* La valeur de temps fournie n&#39;est pas valide : *time *pour availId = ID de la valeur.
* La valeur de durée fournie par la valeur de durée non valide a été ignorée : *duration *for availId = ID de la valeur.
* Initialisez une nouvelle session. (Variant)
* Méthode HTTP non valide. Ça doit être un GET. (VOD)
* Méthode HTTP non valide. La demande de suivi doit être un GET. (En direct)
* Message d&#39;erreur d&#39;URL demandé non valide. (Variant)
* Groupe non valide. (HLSManifestResolver)
* Demande non valide. La légende n&#39;est pas une demande de suivi valide. (VOD)
* Demande non valide. La demande de légende doit être effectuée après l’établissement de la session. (VOD)
* Demande non valide. La demande de suivi doit être effectuée après l&#39;établissement de la session. (VOD)
* Instance de serveur non valide pour l&#39;ID de groupe de surcharge : ID de groupe. (En direct)
* Limite des redirections VAST atteinte - nombre.
* Appel publicitaire : URL d’appel de publicité.
* Aucun manifeste trouvé pour : URL du contenu. (En direct)
* Aucune valeur correspondante n&#39;a été trouvée pour l&#39;ID de la valeur : ID de la valeur. (HLSManifestResolver)
* Session de lecture introuvable. (HLSManifestResolver)
* Traitement de la demande VOD pour l’URL de contenu manifeste.
* Traitement de la variante.
* Traitement de la demande de sous-titrage pour l’URL du contenu manifeste.
* Traitement de la demande de suivi. (VOD)
* Rediriger la réponse publicitaire vide. (VASTStAX)
* Demande : URL.
* Renvoi d’une réponse d’erreur pour la demande de GET, car aucune session de lecture n’a été trouvée. (VOD)
* Renvoi d’une réponse d’erreur pour la demande de GET en raison d’une erreur de serveur interne.
* Renvoi d’une réponse d’erreur pour la demande de GET spécifiant une ressource non valide : ID de demande d’annonce. (VOD)
* Renvoi d&#39;une réponse d&#39;erreur pour la demande de GET spécifiant un ID de groupe non valide ou vide : ID de groupe. (VOD)
* Renvoi d&#39;une réponse d&#39;erreur pour la demande de GET spécifiant une valeur de position de suivi non valide. (VOD)
* Renvoi d’une réponse d’erreur pour une requête de GET avec une syntaxe non valide - URL de requête. (Live/VOD)
* Renvoi d’une réponse d’erreur pour la requête avec une méthode HTTP non prise en charge : GET|POST. (Live/VOD)
* Renvoi du manifeste à partir du cache. (VOD)
* Le serveur est surchargé. Continuer sans la demande de raccordement d’annonces. (Variant)
* Début générant le manifeste ciblé. (HLSManifestResolver)
* Début générant un manifeste de variante à partir de : URL du contenu. (Variant)
* Début d’assemblage de publicités dans le manifeste. (Volontaire VODHLSR)
* Tentative d’assemblage de la publicité à `HH:MM:SS` : AdPlacement \[adManifestURL= et URL du manifeste, durationSeconds= secondes, ignore=, redirectAd= publicité de redirection, priority= priority.\] \(HLSManifestResolver\)
* Impossible d&#39;obtenir les publicités en raison d&#39;une chronologie incorrecte. Le contenu a été renvoyé sans publicité. (VOD)
* Impossible d&#39;obtenir les publicités - a renvoyé le contenu sans publicité. (VOD)
* Impossible d&#39;obtenir la requête publicitaire et aucune URL de contenu n&#39;a été fournie. (VOD)
* URL valide reçue. (VOD/Variant)
* Variante M3U8 introuvable. (Variant)

### TRACE_PLAYBACK_PROGRESS, enregistrements {#trace-playback-progress-records}

Le serveur de manifeste génère des enregistrements de ce type lorsqu’il reçoit un signal sur la progression de la lecture au cours du processus de suivi côté serveur. Les champs au-delà de `TRACE_PLAYBACK_PROGRESS` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| statut | string | Code d’état HTTP |
| bande passante | integer | Bande passante du flux |
| pts | integer | Temps PTS dans le flux |
| ms_time | integer | Heure à laquelle le serveur de manifeste a généré l’URL de suivi |
| url | string | URL de redirection |
| **¿** header_user_agent | string | En-tête HTTP User-Agent |
| **¿** header_dnt | integer | En-tête HTTP do-not-track |
| **¿** effective_remote_address | string | Adresse distante effective IPv4 |
| **¿** remote_address | string | Adresse distante IPv4 |

**Les quatre derniers champs** sont facultatifs.

## Flux de débit binaire multiples {#multiple-bitrate-streams}

Les demandes d’insertion d’annonces du client spécifient généralement plus d’un débit dans la liste de lecture au format M3U8 de variante. Le serveur de manifeste génère et renvoie un nouveau fichier de variante M3U8 contenant un lien M3U8 distinct pour chaque débit binaire. Il génère également un identifiant de groupe unique pour lier ces M3U8s ensemble.

Le serveur de manifeste utilise les informations contenues dans la demande d’URL du Bootstrap du client pour récupérer la liste de lecture de la variante de contenu. Il génère une nouvelle liste de lecture variante contenant des liens de serveur manifeste vers le contenu au niveau du flux. Le client les utilise pour créer des requêtes d’insertion publicitaire. Les liens de contenu au niveau du flux du serveur de manifeste présentent le format suivant :

```shell
https://manifest.auditude.com/auditude/{live/vod}/{publisherAssetID}/{rendition}/
{groupID}/{base64-encoded url of the bit rate stream}.[m3u8]?{Query parameters}
```

* **live/**
vodLe serveur de manifeste définit cette valeur en fonction du type de liste de lecture du contenu : En direct/linéaire (
`#EXT-X-PLAYLIST-TYPE:EVENT`) ou VOD (`#EXT-X-PLAYLIST-TYPE:VOD`)

* **ID unique de**
publisherAssetIDPubliher pour le contenu spécifique fourni dans la demande d’URL du Bootstrap.

* ****
renditionLe serveur de manifeste définit ce paramètre en fonction de 
`BANDWIDTH` du flux de contenu et l’utilise pour faire correspondre le débit de la publicité à celui du contenu. Le débit publicitaire ne peut pas dépasser le débit binaire du contenu, sauf si le rendu publicitaire avec le débit binaire le plus faible le fait.

* ****
groupIDTle serveur de manifeste génère cette valeur et l’utilise pour s’assurer qu’il place les publicités de manière cohérente, quel que soit le débit de rendu des publicités demandé par le client.

* **URL codée en base64 du**
flux de débit binaireBase64, compatible avec l’URL du serveur manifeste, code l’URL absolue du flux de contenu. Chaque flux possède sa propre URL.

* **Paramètres**
de requêteParamètres de requête fournis dans la demande d’URL du Bootstrap.