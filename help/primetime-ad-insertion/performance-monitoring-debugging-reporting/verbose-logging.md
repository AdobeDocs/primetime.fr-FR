---
title: Journalisation détaillée
description: Journalisation détaillée
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '2155'
ht-degree: 0%

---

# Journalisation détaillée {#verbose-logging}

## description des événements de débogage et de journalisation {#ptdebug-logging-events}

Lors de l’initialisation de la journalisation du débogage d’une session de serveur manifeste, vous pouvez ajouter la variable `ptdebug` pour spécifier les options suivantes pour les informations que le serveur manifest renvoie dans les en-têtes HTTP :

* `ptdebug=true`
Tous les enregistrements, à l’exception de TRACE_HTTP_HEADER et de la plupart des données d’appel/réponse des enregistrements TRACE_AD_CALL.

* `ptdebug=AdCall`
Seul le type TRACE_AD_ (par exemple, TRACE_AD_CALL) enregistre.

* `ptdebug=Header`
Seuls les enregistrements TRACE_HTTP_HEADER sont enregistrés.

## Formats des enregistrements de journal {#log-record-formats}

Chaque enregistrement de journal comporte un type et un ensemble de champs, dont certains peuvent être facultatifs. Les champs de tous les enregistrements jusqu&#39;au type d&#39;enregistrement sont les mêmes. Ils fournissent un horodatage et des informations sur la session. Le type d’enregistrement identifie le type d’événement consigné et les champs suivants fournissent des informations sur l’événement consigné.

La structure d&#39;un enregistrement de journal est la suivante :

`datetime request_id session_id zone_id record_type other fields`.

| Champ | Type | Description |
|---|---|---|
| datetime | string | Horodatage |
| request_id | string | ID de demande utilisé par le serveur de manifeste (horodatage Unix) |
| session_id | string | ID de session utilisé par le serveur de manifeste |
| zone_id | entier | Zone |
| record_type | string | Type d’événement en cours de journalisation |
| Autres champs | varie | Dépend du type d’événement |

Les enregistrements de ce type consignent les résultats des requêtes HTTP. Champs au-delà de `TRACE_REQUEST_INFO` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| status | string | Code d’état HTTP renvoyé |
| request_method | string | Méthode HTTP (GET ou POST) |
| request_uri | string | URI de requête HTTP (sans hôte) |
| request_length | entier | Longueur de la requête (octets) |
| response_length | entier | Longueur de la réponse (octets) |
| delta | entier | Temps (millisecondes) nécessaire au traitement de la demande |
| module_type | string | Variante, diffusion ou VOD |
| remote_address_aud_client_ip | string | **‡** |
| remote_address_x_fwd_for_hdr_key | string | **‡** |
| remote_host_port | string | **‡** |

**‡** Les trois derniers champs sont facultatifs.

**Exemple**

```shell
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### Enregistrements TRACE_HTTP_HEADER {#trace-http-header-records}

Les enregistrements de ce type consignent les en-têtes HTTP échangés lors d’appels HTTP entre le serveur manifeste et le client, le serveur publicitaire ou le serveur de contenu. Les champs situés au-delà de TRACE_HTTP_HEADER apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| request_type | string | Type de requête (MAIN ou UNKNOWN) |
| request_response | string | En-tête de réponse (requête ou réponse) |
| header_name | string | Nom de l’en-tête HTTP |
| header_value | string | Valeur d’en-tête HTTP codée en Base64 |

>[!NOTE]
>
>La variable `request_type` et `header_value` sont facultatifs.

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

### Enregistrements TRACE_AD_CALL {#tracing-ad-call-records}

Les enregistrements de ce type consignent les résultats des demandes de publicité de serveur manifeste. Champs au-delà de `TRACE_AD_CALL` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| status | string | Code d’état HTTP renvoyé |
| request_duration | entier | Durée (millisecondes) entre la requête et la réponse |
| ad_server_query_url | string | URL de l’appel publicitaire, y compris les paramètres de requête |
| ad_system_id | string | Système publicitaire, à partir de la réponse du serveur publicitaire (Auditude si non spécifié) |
| avail_id | string | Identifiant de la publicité, à partir du repère publicitaire dans le fichier manifeste de contenu (S/O pour VOD) |
| avail_duration | nombre | Durée (secondes) de la valeur, à partir du repère publicitaire dans le fichier de manifeste de contenu (S/O pour VOD) |
| ad_server_response | string | Réponse codée en base 64 depuis le serveur de publicités |

Exemple :

```shell
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### Enregistrements TRACE_AD_INSERT, TRACE_AD_RESOLVE et TRACE_AD_REDIRECT {#trace-ad-insert-resolve-redirect}

Les enregistrements de ce type consignent les résultats des requêtes de publicité indiquées par le type d’enregistrement. Les champs situés au-delà du type d’enregistrement s’affichent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| status | string | Code d’état HTTP renvoyé. |
| avail_id | string | Identifiant de la publicité, à partir du repère publicitaire dans le fichier manifeste de contenu (en direct) ou du serveur manifeste (VOD). |
| ad_type | string | Type de publicité (DIRECT ou REDIRECT). |
| ad_duration | entier | Durée (secondes) de la publicité, provenant de la réponse du serveur de publicités. |
| ad_content_url | string | URL du fichier de manifeste de la publicité, à partir de la réponse du serveur de publicités. |
| **†** ad_content_url_real | string | URL du fichier de manifeste de la publicité insérée. Vide pour TRACE_AD_REDIRECT. |
| ad_system_id | string | Système publicitaire, à partir de la réponse du serveur publicitaire (Auditude si non spécifié). |
| ad_id | string | Identifiant de la publicité, provenant de la réponse du serveur de publicités. |
| creative_id | string | Identifiant de l’élément créatif, à partir du noeud publicitaire, de la réponse du serveur de publicités. |
| **†** ad_call_id | string | Inutilisée. Réservé pour une utilisation ultérieure. |
| delta | entier | Durée (millisecondes) prise par cet événement. |
| **†** misc | string | Raison de la saut de publicité. |

**†** `ad_content_url_actual`, `ad_call_id`, et `misc` sont facultatifs.

>[!NOTE]
>
>Pour `TRACE_AD_RESOLVE` et `TRACE_AD_INSERT`, l’URL dans le `ad_content_url_actual` est pour la publicité transcodée, le cas échéant. Sinon, le champ est vide pour `TRACE_AD_RESOLVE` ou identique à `ad_content_url` pour `TRACE_AD_INSERT`.

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

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE records {#trace-transcoding-no-media-to-transcode}

Les enregistrements de ce type consignent un élément créatif publicitaire manquant. Le seul champ au-delà `TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE` apparaît dans le tableau.

| Champ | Type | Description |
|---|---|---|
| ad_id | string | ID de publicité complète (FQ_AD_ID: Q_AD_ID\[;Q_AD_ID\[;Q_AD_ID\[;Q_AD_ID...\] \] Q_AD_ID: PROTOCOL:AD_SYSTEM:AD_ID\[:CREATIVE_ID\[:MEDIA_ID\] \] PROTOCOLE : AUDITUDE,VAST) |

Les enregistrements de ce type consignent les résultats des demandes de transcodage que le serveur de manifeste envoie à CRS. Champs au-delà de `TRACE_TRANSCODING_REQUESTED` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| ad_id | string | Identifiant de publicité complet |
| ad_manifest_url | string | URL du fichier manifeste de la publicité, à partir de la réponse du serveur de publicités |
| creative_type | string | Type de média |
| flags | string | ID3 indique si la demande de transcodage comprend une demande d’ajout d’une balise ID3. |
| target_duration | string | Durée cible (secondes) du créatif transcodé |

Les enregistrements de ce type indiquent une demande d’exécution du suivi côté serveur. Champs au-delà de `TRACE_TRACKING_REQUEST` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| tracking_url_count | entier | Nombre d&#39;URL de tracking |
| start | float | Heure de début du fragment PTS (secondes avec précision en millisecondes) |
| end | float | Temps de fin du fragment PTS (secondes avec précision en millisecondes) |

Les enregistrements de ce type fournissent une URL de suivi pour le suivi côté serveur. Champs au-delà de `TRACE_TRACKING_REQUEST_URL` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| timestamp | float | Durée (secondes, avec précision 0,001) de la session de lecture permettant d’envoyer un ping à l’URL de suivi. |
| ad_system | string | Système publicitaire (par exemple, auditude) |
| url | string | URL vers ping |

Enregistrements de ce type de requêtes de journal que le serveur manifeste crée pour `WEBVTT` légendes. Champs au-delà de `TRACE_WEBVTT_REQUEST` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| status | string | Code d’état HTTP renvoyé |
| vtt_uri | string | URL de la requête |
| start | float | Partage de l’heure de début (secondes avec précision en millisecondes) |
| end | float | Partage de l’heure de fin (secondes avec précision de millisecondes) |

Enregistrements de ce type de réponses de journal que le serveur de manifeste envoie aux clients dans `answer` aux requêtes `WEBVTT` légendes. Champs au-delà de `TRACE_WEBVTT_RESPONSE` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| status | string | Code d’état HTTP renvoyé |
| response | string | Réponse codée en Base64 envoyée au client |

Enregistrements de ce type de réponses de journal aux demandes que le serveur manifeste crée pour `WEBVTT` légendes. Champs au-delà de `TRACE_WEBVTT_SOURCE` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| status | string | Code d’état HTTP renvoyé |
| source | string | Contenu VTT d’origine codé en base 64 |

Les enregistrements de ce type permettent au serveur de manifeste de consigner des événements et des informations non planifiés par ailleurs lors de l’ingestion de publicités. Le champ situé au-delà `TRACE_MISC` se compose d’une chaîne de message. Les messages qui peuvent apparaître sont les suivants :

* Ad ignorée : AdPlacement \[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . . .m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1\]
* AdPlacement adManifestURL= adManifestURL, durationSeconds= secondes, ignore= ignore, redirectAd= redirectAd, priority= priority
* L’emplacement de la publicité a renvoyé la valeur null.
* Ajout réussi.
* Échec de l’appel de publicité : message d’erreur.
* Ajout de User-Agent pour récupérer le manifeste brut : user-agent.
* Ajout d’un cookie pour récupérer le manifeste brut : #
* Message d’erreur d’URL demandée incorrect. (Échec de l’analyse de l’URL de variante)
* URL appelée : URL renvoyée : code de réponse. (URL active)
* URL appelée : code de retour URL : code de réponse. (URL VOD)
* Conflit détecté lors de la résolution des publicités : l’un des démarrages mid-roll ou mid-roll se trouve dans preroll ou pre-roll contenu dans mid-roll (VOD).
* Exception non gérée détectée générée par le gestionnaire pour l’URI : URL de requête.
* Terminé la génération du manifeste de variante. (Variante)
* Terminé la génération du manifeste de variante.
* Exception lors de la gestion de la redirection VAST *redirect URL *error: message d’erreur.
* Échec de la récupération de la liste de lecture de la publicité pour l’URL du manifeste de publicité.
* Échec de la génération du manifeste ciblé. (HLSManifestResolver)
* Échec de l’analyse de la première réponse d’appel publicitaire : message d’erreur.
* Échec du traitement de la demande *GET|POST* pour le chemin d’accès : URL de la demande. (En direct/VOD)
* Échec du traitement de la demande de manifeste en direct : URL de la demande. (En direct)
* Échec du renvoi d’un manifeste de variante : message d’erreur.
* Échec de la validation de l’ID de groupe : ID de groupe.
* Récupération du manifeste brut : URL du contenu. (En direct)
* Redirection VAST suivante : URL de redirection.
* Disponibles vides trouvées. (VOD)
* Trouvé *nombre* publicités. (VOD)
* Requête HTTP reçue. (Tout premier message)
* Ignorer la publicité car la différence entre la durée de réponse de publicité (*durée de réponse de publicité *sec) et la durée de publicité réelle (*durée réelle *sec) est supérieure à la limite. (HLSManifestResolver)
* Ignorer la valeur qui n’a fourni aucune valeur d’identifiant. (GroupAdResolver.java)
* Ignorer la valeur qui a fourni une valeur de temps non valide : *time *pour availId = identifiant de la valeur.
* Ignorer la valeur de durée non valide fournie : *duration *pour availId = ID de valeur.
* Initialisez une nouvelle session. (Variante)
* Méthode HTTP non valide. Ça doit être un GET. (VOD)
* Méthode HTTP non valide. La demande de suivi doit être un GET. (En direct)
* Message d’erreur URL demandée non valide. (Variante)
* Groupe non valide. (HLSManifestResolver)
* Requête non valide. La légende n’est pas une requête de suivi valide. (VOD)
* Requête non valide. Une fois la session établie, la demande de légende doit être effectuée. (VOD)
* Requête non valide. La demande de suivi doit être effectuée après l’établissement de la session. (VOD)
* Instance de serveur non valide pour l’ID de groupe de surcharge : ID de groupe. (En direct)
* Limite des redirections VAST atteinte - nombre.
* Appel publicitaire : URL de l’appel publicitaire.
* Manque de manifeste trouvé pour : URL de contenu. (En direct)
* Aucune valeur correspondante n’a été trouvée pour l’ID de la valeur : ID de la valeur. (HLSManifestResolver)
* Aucune session de lecture n’a été trouvée. (HLSManifestResolver)
* Traitement de la requête VOD pour l’URL de contenu manifeste.
* Variante de traitement.
* Traitement de la demande de légende pour l’URL de contenu manifeste.
* Traitement de la demande de suivi. (VOD)
* Rediriger la réponse de publicité vide. (VASTStAX)
* Demande : URL.
* Renvoie une réponse d’erreur pour la demande de GET, car aucune session de lecture n’a été trouvée. (VOD)
* Renvoi d’une réponse d’erreur pour une demande de GET en raison d’une erreur de serveur interne.
* Renvoi d’une réponse d’erreur pour une requête de GET spécifiant une ressource non valide : ID de requête de publicité. (VOD)
* Retour de la réponse d’erreur pour la demande de GET spécifiant un ID de groupe non valide ou vide : ID de groupe. (VOD)
* Renvoi d’une réponse d’erreur pour une demande de GET spécifiant une valeur de position de suivi non valide. (VOD)
* Renvoi d’une réponse d’erreur pour une requête de GET avec une syntaxe non valide - URL de requête. (En direct/VOD)
* Retour de la réponse d’erreur pour la requête avec la méthode HTTP non prise en charge : GET|POST. (En direct/VOD)
* Renvoi du manifeste à partir du cache. (VOD)
* Serveur surchargé. Poursuivez sans demande de groupement publicitaire. (Variante)
* Commencez à générer le manifeste ciblé. (HLSManifestResolver)
* Commencez à générer le manifeste de variante à partir de : URL du contenu. (Variante)
* Commencez à regrouper des publicités dans un manifeste. (VODHLSResolver)
* Test d’assemblage de la publicité à l’adresse `HH:MM:SS`: AdPlacement \[adManifestURL= et URL du manifeste, durationSeconds= secondes, ignore=, redirectAd= publicité de redirection, priority= priorité.\] \(HLSManifestResolver\)
* Impossible d’obtenir les publicités en raison d’une chronologie non valide : a renvoyé le contenu sans publicité. (VOD)
* Impossible d’obtenir les publicités : renvoyait le contenu sans les publicités. (VOD)
* Impossible d’obtenir la requête de publicité et aucune URL de contenu n’a été fournie. (VOD)
* URL valide reçue. (VOD/Variant)
* Variante M3U8 introuvable. (Variante)

### Enregistrements TRACE_PLAYBACK_PROGRESS {#trace-playback-progress-records}

Le serveur de manifeste génère des enregistrements de ce type lorsqu’il reçoit un signal sur la progression de la lecture pendant le workflow de suivi côté serveur. Champs au-delà de `TRACE_PLAYBACK_PROGRESS` apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|---|---|---|
| status | string | Code d’état HTTP |
| bande passante | entier | Bande passante de la diffusion |
| pts | entier | Temps PTS dans le flux |
| ms_time | entier | Heure à laquelle l’URL de suivi générée par le serveur manifeste |
| url | string | URL de redirection |
| **On on** header_user_agent | string | En-tête HTTP User-Agent |
| **On on** header_dnt | entier | En-tête HTTP do-not-track |
| **On on** effective_remote_address | string | Adresse distante effective IPv4 |
| **On on** remote_address | string | Adresse distante IPv4 |

**On on** Les quatre derniers champs sont facultatifs.

## Flux de débit de plusieurs bits {#multiple-bitrate-streams}

Les demandes client pour l’insertion de publicités spécifient généralement plus d’un débit dans la liste de lecture au format M3U8 de variante. Le serveur de manifeste génère et renvoie un nouveau fichier de variante M3U8 contenant un lien M3U8 distinct pour chaque débit binaire. Il génère également un identifiant de groupe unique pour lier ces M3U8s.

Le serveur de manifeste utilise les informations contenues dans la requête d’URL du Bootstrap du client pour récupérer la liste de lecture de la variante de contenu. Elle génère une nouvelle liste de lecture de variante contenant des liens de serveur manifestes vers le contenu au niveau du flux. Le client les utilise pour créer des requêtes d’insertion de publicités. Les liens de contenu au niveau du flux du serveur de manifeste présentent le format suivant :

```shell
https://manifest.auditude.com/auditude/{live/vod}/{publisherAssetID}/{rendition}/
{groupID}/{base64-encoded url of the bit rate stream}.[m3u8]?{Query parameters}
```

* **live/vod**
Le serveur de manifeste définit cette valeur en fonction du type de liste de lecture du contenu : Live/linear (`#EXT-X-PLAYLIST-TYPE:EVENT`) ou VOD (`#EXT-X-PLAYLIST-TYPE:VOD`)

* **publisherAssetID**
Identifiant unique de l’éditeur pour le contenu spécifique fourni dans la requête d’URL du Bootstrap.

* **rendu**
Le serveur de manifeste définit ce paramètre en fonction de la variable `BANDWIDTH` de la diffusion en continu de contenu et l’utilise pour correspondre au débit de la publicité au débit de diffusion du contenu. Le débit publicitaire ne peut pas excéder le débit du contenu, sauf si le rendu publicitaire avec le débit le plus faible le fait.

* **groupID**
Le serveur de manifeste génère cette valeur et l’utilise pour s’assurer qu’il place les publicités de manière cohérente, quel que soit le débit de rendu des publicités demandé par le client.

* **URL codée en base64 du flux de débit binaire**
La base64 sécurisée pour l’URL du serveur de manifeste code l’URL absolue du flux de contenu. Chaque flux possède sa propre URL.

* **Paramètres de requête**
Paramètres de requête fournis dans la requête d’URL du Bootstrap.
