---
title: Outil de débogage du serveur Manifest
description: Outil de débogage du serveur Manifest
products: SG_PRIMETIME
topic-tags: ad-insertion
discoiqdonotlocalize: false
moreHelpPaths: /content/help/en/primetime/morehelp/ad-insertion;/content/help/en/primetime/morehelp/ad-insertion
pagecreatedat: en
pagelayout: video
sidecolumn: left
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '2414'
ht-degree: 0%

---


# Outil de débogage du serveur Manifest {#manifest-server-debugging-tool}

L’outil de débogage permet aux éditeurs d’enquêter sur les problèmes d’insertion de publicités potentiellement coûteux en examinant les informations de débogage renvoyées en temps réel par le serveur de manifeste dans les en-têtes HTTP ou, lorsque des informations plus détaillées sont nécessaires, d’examiner les journaux de session après coup. Les partenaires d’Adobe comme Akamai peuvent utiliser l’outil pour déboguer leurs intégrations avec Primetime et la prise de décision.

L’outil prend en charge le débogage des problèmes d’insertion des publicités dans l’une des configurations de suivi des publicités du serveur de manifeste principales :

* Suivi côté client avec un lecteur basé sur TVSDK.
* Suivi côté client avec un lecteur non basé sur TVSDK.
* Suivi côté serveur.

Pour prendre en charge tous ces cas, l’outil ne nécessite ni n’utilise les codes d’éditeur du lecteur.

Lorsque vous lancez une session de serveur de manifeste, vous pouvez définir un paramètre sur l’URL de demande pour lui demander de consigner les informations de débogage. En utilisant différentes valeurs de ce paramètre, vous pouvez également demander au serveur de manifeste de renvoyer des informations de débogage spécifiées dans les en-têtes HTTP, mais les en-têtes ne peuvent contenir qu’une quantité limitée d’informations. Vous pouvez obtenir des informations d’identification d’Adobe pour accéder aux fichiers journaux complets, que le serveur de manifeste enregistre régulièrement (par exemple toutes les heures) sur un serveur d’archive. Une fois que vous disposez des informations d’identification de ce serveur, vous pouvez y accéder directement à tout moment.

<!-- You can also see the [server side event tracking captured in the SSAI dashboard](ssai-debugging-dashboard.md).-->

## Options des outils de débogage {#debugging-tool-options}

Lors de l’appel de l’outil de débogage, vous disposez de plusieurs options pour connaître les informations que le serveur manifeste renvoie dans les en-têtes HTTP. Les options n’affectent pas les emplacements du serveur de manifeste dans les fichiers journaux.

### Spécification de ptdebug {#specifying-ptdebug}

Lors de l’initialisation de la journalisation du débogage d’une session de serveur de manifeste, vous pouvez ajouter le paramètre ptdebug à l’URL de demande afin de spécifier les options suivantes pour les informations que le serveur de manifeste renvoie dans les en-têtes HTTP :

* ptdebug=true Tous les enregistrements sauf `TRACE_HTTP_HEADER` et `call/response data` de `TRACE_AD_CALL` enregistrements.
* ptdebug=AdCall Only TRACE_AD_*type* (par exemple, les enregistrements TRACE_AD_CALL).
* ptdebug=Header Only TRACE_HTTP_HEADER records.

Les options n’affectent pas les emplacements du serveur de manifeste dans les fichiers journaux. Vous n’en avez aucun contrôle, mais les fichiers journaux sont des fichiers texte, vous pouvez donc appliquer un large éventail d’outils pour extraire et reformater les informations qui vous intéressent.

Voici un exemple de l’en-tête HTTP renvoyé lors de `ptdebug=Header`. Certaines longues chaînes de chiffres hexadécimaux sont remplacées par `. . .` pour plus de clarté.

```
X-ADBE-AI-DBG-1 TRACE_MISC    HTTP request received
X-ADBE-AI-DBG-2 TRACE_MISC    Processing Variant
X-ADBE-AI-DBG-3 TRACE_MISC    Valid URL received.
X-ADBE-AI-DBG-4 TRACE_MISC    Initialize new session
X-ADBE-AI-DBG-5 TRACE_MISC    Requesting: /auditude/variant/pubAsset/aHR0cDovL . . .m3u8
 ?u=cecebae . . .&z=189962&pttrackingmode=simple&pttrackingversion=v1
 &ptcueformat=turner&__sid__=yk-sat953pm-112
 &ptdebug=true
X-ADBE-AI-DBG-6  TRACE_HTTP_HEADER  MAIN  REQUEST  Host    bWFuaWZl. . .
X-ADBE-AI-DBG-7  TRACE_HTTP_HEADER  MAIN  REQUEST  Connection       Y2xvc2U=
X-ADBE-AI-DBG-8  TRACE_HTTP_HEADER  MAIN  REQUEST  Accept   dGV4dC. . .
X-ADBE-AI-DBG-9  TRACE_HTTP_HEADER  MAIN  REQUEST  Cookie   c3NhaT. . .
X-ADBE-AI-DBG-10 TRACE_HTTP_HEADER  MAIN  REQUEST  User-Agent       TW96aWxs. . .
X-ADBE-AI-DBG-11 TRACE_HTTP_HEADER  MAIN  REQUEST  Accept-Language  ZW4tdXM=
X-ADBE-AI-DBG-12 TRACE_HTTP_HEADER  MAIN  REQUEST  Accept-Encoding  Z3ppcCwg. . .=
X-ADBE-AI-DBG-13 TRACE_REQUEST_INFO  200   GET
 /auditude/variant/pubAsset/aHR0cD. . ..m3u8
 ?u=cecebae72a919de350b9ac52602623f3&z=189962&pttrackingmode=simple
 &pttrackingversion=v1&ptcueformat=turner&__sid__=yk-sat953pm-112
 &ptdebug=true   0 0 0   Variant  NA  null  null  127.0.0.1:43357
X-ADBE-AI-DBG-14 TRACE_HTTP_HEADER  MAIN  RESPONSE Content-Type     YXBwbG. . .
X-ADBE-AI-DBG-15 TRACE_HTTP_HEADER  MAIN  RESPONSE Cache-Control    bm8tY2. . .
X-ADBE-AI-DBG-16 TRACE_HTTP_HEADER  MAIN  RESPONSE Access-Control-Allow-Origin    Kg==
X-ADBE-AI-DBG-17 TRACE_MISC   Done
```

## Formats des enregistrements de journal {#formats-of-log-records}

Chaque enregistrement de journal comporte un type et un ensemble de champs, dont certains peuvent être facultatifs. Les champs de tous les enregistrements jusqu&#39;au type d&#39;enregistrement sont les mêmes. Ils fournissent un horodatage et des informations sur la session. Le type d’enregistrement identifie le type d’événement consigné et les champs suivants fournissent des informations sur l’événement consigné.

La structure d&#39;un enregistrement de journal est la suivante :

`datetime request_id session_id zone_id record_type` *autres champs.*

| Champ | Type | Description |
|--- |--- |--- |
| datetime | string | Horodatage |
| request_id | string | ID de demande utilisé par le serveur de manifeste (horodatage unix) |
| session_id | string | ID de session utilisé par le serveur de manifeste |
| zone_id | entier | ID de zone |
| record_type | string | Type d’événement en cours de journalisation |
| Autres champs | *** | Dépend du type d’événement |

### Enregistrements TRACE_REQUEST_INFO {#trace-request-info-records}

Les enregistrements de ce type consignent les résultats des requêtes HTTP. Les champs situés au-delà de TRACE_REQUEST_INFO apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| status | string | Code d’état HTTP renvoyé |
| request_method | string | Méthode HTTP (GET ou POST) |
| request_uri | string | URI de requête HTTP (sans hôte) |
| request_length | entier | Longueur de la requête (octets) |
| response_length | entier | Longueur de la réponse (octets) |
| delta | entier | Temps (millisecondes) nécessaire au traitement de la demande |
| module_type | string | Variante, diffusion ou VOD |
| remote_address_aud_client_ip | string | (voir remarque) |
| remote_address_x_fwd_for_hdr_key | string | (voir remarque) |
| remote_host_port | string | (voir remarque) |

>[!NOTE]
>
>Les trois derniers champs sont facultatifs.

Exemple :

```
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938
TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8
?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### Enregistrements TRACE_HTTP_HEADER {#trace-http-header-records}

Les enregistrements de ce type consignent les en-têtes HTTP échangés lors d’appels HTTP entre le serveur manifeste et le client, le serveur publicitaire ou le serveur de contenu. Les champs situés au-delà de TRACE_HTTP_HEADER apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| request_type | string | Type de requête (MAIN ou UNKNOWN) |
| request_response | string | En-tête de réponse (requête ou réponse) |
| header_name | string | Nom de l’en-tête HTTP |
| header_value | string | Valeur d’en-tête HTTP codée en Base64 |

>[!NOTE]
>
>Les champs request_type et header_value sont facultatifs.

Exemple :

```
2015-03-25T06:10:00.927Z  1427263800573  6495aa. . .  189938 TRACE_MISC
    Requesting: /cnn/tvecnn/stream4/stream_Layer.m3u8
2015-03-25T06:10:00.927Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN REQUEST Cookie  aGRu. . .
2015-03-25T06:10:00.928Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN REQUEST User-Agent  TW96aW. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Server  bmd4X2. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Content-Type    YXBwb. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Last-Modified   V2VkL. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  ETag    IjIyY2. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Vary    QWNjZXB. . .
2015-03-25T06:10:01.063Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Cache-Control   bWF4LW. . .
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Expires V2VkL. . .
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Date    V2VkLCA. . .
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Age MQ==
2015-03-25T06:10:01.064Z  1427263800573  6495aa. . .  189938 TRACE_HTTP_HEADER
    UNKNOWN RESPONSE  Via MS4xIH. . .
```

### Enregistrements TRACE_AD_CALL {#trace-ad-call-records}

Les enregistrements de ce type consignent les résultats des demandes de publicité de serveur manifeste. Les champs situés au-delà de TRACE_AD_CALL apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| status | string | Code d’état HTTP renvoyé |
| request_duration | entier | Durée (millisecondes) entre la requête et la réponse |
| ad_server_query_url | string | URL de l’appel publicitaire, y compris les paramètres de requête |
| ad_system_id | string | Système publicitaire, à partir de la réponse du serveur publicitaire (Auditude si non spécifié) |
| avail_id | string | Identifiant de la publicité, à partir du repère publicitaire dans le fichier manifeste de contenu (S/O pour VOD) |
| avail_duration | nombre | Durée (secondes) de la valeur, à partir du repère publicitaire dans le fichier de manifeste de contenu (S/O pour VOD) |
| ad_server_response | string | Réponse codée en base 64 depuis le serveur de publicités |

Exemple :

```
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL
200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### Enregistrements TRACE_AD_INSERT, TRACE_AD_RESOLVE et TRACE_AD_REDIRECT {#trace-ad-insert-trace-ad-resolve-and-trace-ad-redirect-records}

Les enregistrements de ce type consignent les résultats des requêtes de publicité indiquées par le type d’enregistrement. Les champs situés au-delà du type d’enregistrement s’affichent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| status | string | Code d’état HTTP renvoyé |
| avail_id | string | Identifiant de la publicité, à partir du repère publicitaire dans le fichier manifeste de contenu (en direct) ou du serveur manifeste (VOD) |
| ad_type | string | Type de publicité (DIRECT ou REDIRECT) |
| ad_duration | entier | Durée (secondes) de la publicité, à partir de la réponse du serveur de publicités |
| ad_content_url | string | URL du fichier manifeste de la publicité, à partir de la réponse du serveur de publicités |
| ad_content_url_real | string | URL du fichier de manifeste de la publicité insérée. Vide pour TRACE_AD_REDIRECT. |
| ad_system_id | string | Système publicitaire, à partir de la réponse du serveur publicitaire (Auditude si non spécifié) |
| ad_id | string | ID de la publicité, provenant de la réponse du serveur de publicités |
| creative_id | string | Identifiant du créatif, à partir du noeud publicitaire, de la réponse du serveur de publicités. |
| ad_call_id | string | Inutilisée. Réservé pour une utilisation ultérieure. |
| delta | entier | Durée (millisecondes) prise par cet événement |
| misc | string | Raison pour laquelle la publicité a été ignorée |

>[!NOTE]
>
>Les champs ad_content_url_real, ad_call_id et misc sont facultatifs.

Pour TRACE_AD_RESOLVE et TRACE_AD_INSERT, l’URL du champ ad_content_url_real correspond à la publicité transcodée, le cas échéant. Sinon, le champ est vide pour TRACE_AD_RESOLVE ou identique à ad_content_url pour TRACE_AD_INSERT.

Exemple :

```
2015-03-18T22:25:36.229-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE
200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA

2015-03-18T22:25:36.230-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_RESOLVE
200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 Auditude 308008 0  cecebae72a919de350b9ac52602623f3 0 NA

2015-03-18T22:25:36.562-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT
200 0 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8
Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
2015-03-18T22:25:36.563-07:00 1426742736208 1120feb. . . 147465 TRACE_AD_INSERT
200 2 DIRECT 15 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8 https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . ..m3u8
Auditude 308008 0 cecebae72a919de350b9ac52602623f3 0 NA
```

### Enregistrements TRACE_TRACKING_URL {#trace-tracking-url-records}

Les enregistrements de ce type consignent les résultats des demandes de publicité de serveur manifeste. Les champs situés au-delà de TRACE_TRACKING_URL apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| pts | nombre | Horodatage du programme. Durée dans la vidéo d’appel de l’URL. |
| ad_system | string | Système publicitaire (auditude ou roue libre) |
| url | string | URL ping |
| status | string | État HTTP renvoyé par le ping |

Exemple :

```
2015-06-04T23:24:42.000-0700    1426742736208     3086f5cd . . .    12345    TRACE_TRACKING_URL
    0.000000    ExampleSystem    https://localhost/index.php?stream:test#8.1433485415;
    sid:3086f5cd . . .;pts:0    200
```

### TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE records {#trace-transcoding-no-media-to-transcode-records}

Les enregistrements de ce type consignent un élément créatif publicitaire manquant. Le seul champ situé au-delà de TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE apparaît dans le tableau.

| Champ | Type | Description |
|--- |--- |--- |
| ad_id | string | Identifiant de publicité complet `(FQ_AD_ID: Q_AD_ID\[;Q_AD_ID\[;Q_AD_ID...\]\]` Q_AD_ID : `PROTOCOL:AD_SYSTEM:AD_ID\[:CREATIVE_ID\[:MEDIA_ID\]\]` PROTOCOLE : AUDITUDE,VAST) |

### TRACE_TRANSCODING_REQUESTED records {#trace-transcoding-requested-records}

Les enregistrements de ce type consignent les résultats des demandes de transcodage que le serveur de manifeste envoie à CRS. Les champs situés au-delà de TRACE_TRANSCODING_REQUESTED apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| ad_id | string | Identifiant de publicité complet |
| ad_manifest_url | string | URL du fichier manifeste de la publicité, à partir de la réponse du serveur de publicités |
| creative_type | string | Type de média |
| flags | string | ID3 indique si la demande de transcodage comprend une demande d’ajout d’une balise ID3. |
| target_duration | string | Durée cible (secondes) du créatif transcodé |

### TRACE_TRACKING_REQUEST records {#trace-tracking-request-records}

Les enregistrements de ce type indiquent une demande d’exécution du suivi côté serveur. Les champs situés au-delà de TRACE_TRACKING_REQUEST apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| tracking_url_count | entier | Nombre d&#39;URL de tracking |
| start | float | Heure de début du fragment PTS (secondes avec précision en millisecondes) |
| end | float | Temps de fin du fragment PTS (secondes avec précision en millisecondes) |

### TRACE_TRACKING_REQUEST_URL records {#trace-tracking-request-url-records}

Les enregistrements de ce type fournissent une URL de suivi pour le suivi côté serveur. Les champs situés au-delà de TRACE_TRACKING_REQUEST_URL apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| timestamp | float | Durée (secondes, avec précision 0.001) de la session de lecture pour envoyer un ping à l’URL de suivi |
| ad_system | string | Système publicitaire (par exemple, auditude) |
| url | string | URL vers ping |

### TRACE_WEBVTT_REQUEST records {#trace-webvtt-request-records}

Enregistrements de ce type de requêtes de journal que le serveur manifeste crée pour les sous-titres WEBVTT. Les champs situés au-delà de TRACE_WEBVTT_REQUEST apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| status | string | Code d’état HTTP renvoyé |
| vtt_uri | string | URL de la requête |
| start | float | Partage de l’heure de début (secondes avec précision en millisecondes) |
| end | float | Partage de l’heure de fin (secondes avec précision de millisecondes) |

### TRACE_WEBVTT_RESPONSE records {#trace-webvtt-response-records}

Enregistrements ``of ``this ``type ``log ``responses ``la valeur ``manifest ``server ``sends ``to ``clients ``in `` `answer` ``to ``requests `` `for` ``WEBVTT ``légendes. Les champs situés au-delà de TRACE_WEBVTT_RESPONSE &quot;apparaissent dans l’ordre indiqué dans le tableau, séparés `by`onglets.

| Champ | Type | Description |
|--- |--- |--- |
| status | string | Code d’état HTTP renvoyé |
| response | string | Réponse codée en Base64 envoyée au client |

### TRACE_WEBVTT_SOURCE records {#trace-webvtt-source-records}

Enregistrements de ce type de réponses de journal aux demandes que le serveur manifeste crée pour les sous-titres WEBVTT. Les champs situés au-delà de TRACE_WEBVTT_SOURCE apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| status | string | Code d’état HTTP renvoyé |
| source | string | Contenu VTT d’origine codé en base 64 |


### Enregistrements TRACE_MISC {#trace-misc-records}

Les enregistrements de ce type permettent au serveur de manifeste de consigner des événements et des informations non planifiés par ailleurs lors de l’ingestion de publicités. Le champ situé au-delà de TRACE_MISC est constitué d’une chaîne de message. Les messages qui peuvent apparaître sont les suivants :

* Ad ignored : AdPlacement `[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . . .m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1]`
* AdPlacement adManifestURL=*adManifestURL*, durationSeconds=*seconds*, ignore=*ignore*, redirectAd=*redirectAd*, priority=*priority*
* L’emplacement de la publicité a renvoyé la valeur null.
* Ajout réussi.
* Échec de l’appel de publicité : *message d&#39;erreur*.
* Ajout de User-Agent pour récupérer le manifeste brut : *user-agent*.
* Ajout de cookie pour récupérer le manifeste brut : [cookie]
* URL incorrecte *message d’erreur d’URL demandée*. (Échec de l’analyse de l’URL de variante)
* URL appelée : URL *retour obtenu : code de réponse*. (URL active)
* URL appelée : URL *code de retour : code de réponse*. (URL VOD)
* Conflit détecté lors de la résolution des publicités : l’un des démarrages mid-roll ou mid-roll se trouve dans preroll ou pre-roll contenu dans mid-roll (VOD).
* Exception non gérée détectée générée par le gestionnaire pour l’URI : *URL de requête*.
* Terminé la génération du manifeste de variante. (Variante)
* Terminé la génération du manifeste de variante.
* Exception lors de la gestion de la redirection VAST *redirect URL *error: *message d&#39;erreur*.
* Impossible de récupérer la liste de lecture de la publicité pour *URL du manifeste publicitaire*.
* Échec de la génération du manifeste ciblé. (HLSManifestResolver)
* Échec de l’analyse de la première réponse d’appel publicitaire : *message d&#39;erreur*.
* Échec du traitement de la demande *GET|POST *pour le chemin d’accès : *URL de requête*. (En direct/VOD)
* Échec du traitement de la demande de manifeste en direct : *URL de requête*. (En direct)
* Échec du renvoi d’un manifeste de variante : *message d&#39;erreur*.
* Échec de la validation de l’ID de groupe : *ID de groupe*.
* Récupération du manifeste brut : *URL du contenu*. (En direct)
* Suite à la redirection VAST : *URL de redirection*.
* Disponibles vides trouvées. (VOD)
* *nombre* de publicités trouvé. (VOD)
* Requête HTTP reçue. (Tout premier message)
* Ignorer la publicité car la différence entre la durée de réponse de publicité (*durée de réponse de publicité *sec) et la durée de publicité réelle (*durée réelle *sec) est supérieure à la limite. (HLSManifestResolver)
* Ignorer la valeur qui n’a fourni aucune valeur d’identifiant. (GroupAdResolver.java)
* Ignorer la valeur qui a fourni une valeur de temps non valide : *time *pour availId = *ID de la diffusion*.
* Ignorer la valeur de durée non valide fournie : *duration *pour availId = *ID de la diffusion*.
* Initialisez une nouvelle session. (Variante)
* Méthode HTTP non valide. Ça doit être un GET. (VOD)
* Méthode HTTP non valide. La demande de suivi doit être un GET. (En direct)
* URL non valide *message d’erreur d’URL demandée*. (Variante)
* Groupe non valide. (HLSManifestResolver)
* Requête non valide. La légende n’est pas une requête de suivi valide. (VOD)
* Requête non valide. Une fois la session établie, la demande de légende doit être effectuée. (VOD)
* Requête non valide. La demande de suivi doit être effectuée après l’établissement de la session. (VOD)
* Instance de serveur non valide pour l’ID de groupe de surcharge : *ID de groupe*. (En direct)
* Limite des redirections VAST atteinte - *nombre*.
* Effectuer un appel publicitaire : *URL d’appel publicitaire*.
* Aucun manifeste trouvé pour : *URL du contenu*. (En direct)
* Aucune valeur correspondante trouvée pour l’ID de valeur : *ID de la diffusion*. (HLSManifestResolver)
* Aucune session de lecture n’a été trouvée. (HLSManifestResolver)
* Traitement de la requête VOD pour le manifeste *URL du contenu*.
* Variante de traitement.
* Traitement de la demande de légende pour le manifeste *URL du contenu*.
* Traitement de la demande de suivi. (VOD)
* Rediriger la réponse de publicité vide. (VASTStAX)
* Demande : *URL*.
* Renvoie une réponse d’erreur pour la demande de GET, car aucune session de lecture n’a été trouvée. (VOD)
* Renvoi d’une réponse d’erreur pour une demande de GET en raison d’une erreur de serveur interne.
* Renvoi d’une réponse d’erreur pour une demande de GET spécifiant une ressource non valide : *ID de requête publicitaire*. (VOD)
* Renvoi d’une réponse d’erreur pour une demande de GET spécifiant un ID de groupe non valide ou vide : *ID de groupe*. (VOD)
* Renvoi d’une réponse d’erreur pour une demande de GET spécifiant une valeur de position de suivi non valide. (VOD)
* Renvoi de la réponse d’erreur pour la requête de GET avec une syntaxe non valide - *URL de requête*. (En direct/VOD)
* Renvoi de la réponse d’erreur pour la requête avec la méthode HTTP non prise en charge : *GET|POST*. (En direct/VOD)
* Renvoi du manifeste à partir du cache. (VOD)
* Serveur surchargé. Poursuivez sans demande de groupement publicitaire. (Variante)
* Commencez à générer le manifeste ciblé. (HLSManifestResolver)
* Commencez à générer le manifeste de variante à partir de : *URL du contenu*. (Variante)
* Commencez à regrouper des publicités dans un manifeste. (VODHLSResolver)
* Test d’assemblage de la publicité à l’adresse `HH:MM:SS`: AdPlacement \[adManifestURL=*URL du manifeste publicitaire*, durationSeconds=*seconds*, ignore=*ignore*, redirectAd=*rediriger l&#39;annonce*, priority=*priority*.\]
* Impossible d’obtenir les publicités en raison d’une chronologie non valide : a renvoyé le contenu sans publicité. (VOD)
* Impossible d’obtenir les publicités : renvoyait le contenu sans les publicités. (VOD)
* Impossible d’obtenir la requête de publicité et aucune URL de contenu n’a été fournie. (VOD)
* URL valide reçue. (VOD/Variant)
* Variante M3U8 introuvable. (Variante)

### Enregistrements TRACE_TRACKING_URL {#trace-tracking-url-records-1}

Le serveur de manifeste génère des enregistrements de ce type après avoir appelé une URL de suivi au cours du workflow de suivi côté serveur. Les champs situés au-delà de TRACE_TRACKING_URL apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| pts | nombre | Temps PTS dans le flux |
| ad_system | string | Système publicitaire de la publicité (auditude ou roue libre) |
| url | string | URL ping |
| state | string | Code d’état HTTP |

### Enregistrements TRACE_PLAYBACK_PROGRESS {#trace-playback-progress-records}

Le serveur de manifeste génère des enregistrements de ce type lorsqu’il reçoit un signal sur la progression de la lecture pendant le workflow de suivi côté serveur. Les champs situés au-delà de TRACE_PLAYBACK_PROGRESS apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| status | string | Code d’état HTTP |
| bande passante | entier | Bande passante de la diffusion |
| pts | entier | Temps PTS dans le flux |
| ms_time | entier | Heure à laquelle l’URL de suivi générée par le serveur manifeste |
| url | string | URL de redirection |
| header_user_agent | string | En-tête HTTP User-Agent |
| header_dnt | entier | En-tête HTTP do-not-track |
| effective_remote_address | string | Adresse distante effective IPv4 |
| remote_address | string | Adresse distante IPv4 |

>[!NOTE]
>
>Les quatre derniers champs sont facultatifs.

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète à l’adresse [Formation et assistance pour Adobe Primetime](https://helpx.adobe.com/support/primetime.html) page.
