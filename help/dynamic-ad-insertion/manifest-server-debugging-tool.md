---
title: Outil de débogage du serveur Manifest
seo-title: Outil de débogage du serveur Manifest
description: Outil de débogage du serveur Manifest
seo-description: Outil de débogage du serveur Manifest
uuid: 0b4f06f5-4b1f-4f88-980a-5b4df28e0094
products: SG_PRIMETIME
topic-tags: ad-insertion
discoiquuid: 00b49659-ce56-4b5c-87cd-c357a0936641
donotlocalize: false
moreHelpPaths: /content/help/en/primetime/morehelp/ad-insertion;/content/help/en/primetime/morehelp/ad-insertion
pagecreatedat: en
pagelayout: video
sidecolumn: left
translation-type: tm+mt
source-git-commit: b77f4988103b68d0ce8926407d2ccb2e0c68e322

---


# Outil de débogage du serveur Manifest {#manifest-server-debugging-tool}

## Présentation de l’outil de débogage {#overview-of-debugging-tool}

L’outil de débogage permet aux éditeurs d’étudier les problèmes d’insertion d’annonces potentiellement coûteux en examinant les informations de débogage renvoyées en temps réel par le serveur de manifeste dans les en-têtes HTTP ou, lorsque des informations plus détaillées sont nécessaires, en examinant les journaux de session après coup. Les partenaires Adobe tels qu’Akamai peuvent utiliser cet outil pour déboguer leurs intégrations avec Primetime et la prise de décision.

L&#39;outil prend en charge les problèmes de débogage et d&#39;insertion dans n&#39;importe quelle des configurations de suivi des publicités principales du serveur de manifeste :

* Suivi côté client avec un lecteur basé sur TVSDK.
* Suivi côté client avec un lecteur non basé sur TVSDK.
* Suivi côté serveur.

Pour prendre en charge tous ces cas, l’outil ne nécessite pas de code d’éditeur du lecteur ou ne l’utilise pas.

Lorsque vous lancez une session de serveur de manifeste, vous pouvez définir un paramètre sur l’URL de demande pour lui demander de consigner les informations de débogage. En utilisant différentes valeurs de ce paramètre, vous pouvez également demander au serveur de manifeste de renvoyer des éléments d’informations de débogage spécifiés dans les en-têtes HTTP, mais ces derniers ne peuvent contenir qu’une quantité limitée d’informations. Vous pouvez obtenir des informations d’identification d’Adobe pour accéder aux fichiers journaux complets, que le serveur de manifeste enregistre régulièrement (par exemple, toutes les heures) sur un serveur d’archives. Une fois que vous disposez des informations d’identification pour ce serveur, vous pouvez y accéder directement à tout moment.

<!-- You can also see the [server side event tracking captured in the SSAI dashboard](ssai-debugging-dashboard.md).-->

## Options de l’outil de débogage {#debugging-tool-options}

Lorsque vous appelez l&#39;outil de débogage, vous disposez de plusieurs options pour les informations que le serveur de manifeste renvoie dans les en-têtes HTTP. Les options n&#39;affectent pas ce que le serveur de manifeste place dans les fichiers journaux.

### Spécification de ptdebug {#specifying-ptdebug}

Lors de l’ouverture de la journalisation du débogage d’une session de serveur de manifeste, vous pouvez ajouter le paramètre ptdebug à l’URL de demande afin de spécifier les options suivantes pour les informations que le serveur de manifeste renvoie dans les en-têtes HTTP :

* ptdebug=true Tous les enregistrements sauf `TRACE_HTTP_HEADER` et la plupart `call/response data` des enregistrements `TRACE_AD_CALL` .
* ptdebug=AdCall Only TRACE_AD_*type* (par exemple, TRACE_AD_CALL) enregistre.
* ptdebug=En-tête uniquement enregistrements TRACE_HTTP_HEADER.

Les options n&#39;affectent pas ce que le serveur de manifeste place dans les fichiers journaux. Vous n&#39;en avez aucun contrôle, mais les fichiers journaux sont des fichiers texte, vous pouvez donc appliquer une grande variété d&#39;outils pour extraire et reformater les informations qui vous intéressent.

Voici un exemple de l’en-tête HTTP renvoyé lorsque `ptdebug=Header`ce paramètre est activé. Certaines longues chaînes de chiffres hexadécimaux sont remplacées par `. . .` pour plus de clarté.

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

Chaque enregistrement de journal comporte un type et un ensemble de champs, dont certains peuvent être facultatifs. Les champs de tous les enregistrements jusqu&#39;au type d&#39;enregistrement sont identiques. Ils fournissent un horodatage et des informations sur la session. Le type d’enregistrement identifie le type de événement en cours de journalisation et les champs suivants fournissent des informations sur le événement consigné.

La structure d&#39;un enregistrement de journal est la suivante :

`datetime request_id session_id zone_id record_type` *autres champs.*

| Champ | Type | Description |
|--- |--- |--- |
| datetime | string | Horodatage |
| request_id | string | ID de demande utilisé par le serveur de manifeste (horodatage unix) |
| session_id | string | ID de session utilisé par le serveur de manifeste |
| zone_id | integer | ID de zone |
| record_type | string | Type de événement en cours de journalisation |
| autres champs | *** | Dépend du type de événement |

### enregistrements TRACE_REQUEST_INFO {#trace-request-info-records}

Les enregistrements de ce type enregistrent les résultats des requêtes HTTP. Les champs situés au-delà de TRACE_REQUEST_INFO apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| statut | string | Code d’état HTTP renvoyé |
| request_method | string | Méthode HTTP (GET ou POST) |
| request_uri | string | URI de requête HTTP (sans hôte) |
| request_length | integer | Longueur de la requête (octets) |
| response_length | integer | Longueur de la réponse (octets) |
| delta | integer | Temps (millisecondes) nécessaire au traitement de la demande |
| module_type | string | Variante, Diffusion en continu ou VOD |
| remote_address_aud_client_ip | string | (voir note) |
| remote_address_x_fwd_for_hdr_key | string | (voir note) |
| remote_host_port | string | (voir note) |

>[!NOTE]
>
>Les trois derniers champs sont facultatifs.

Exemple :

```
1427263800524 6495aafc-3f34-4047-ad36-350d4f056eb4 189938
TRACE_REQUEST_INFO 301 GET /auditude/variant/pubAsset/aHR0cDov. . ..m3u8
?u=cecebae72a919de350b9ac52602623f3&z=189938&ptcueformat=turner& sid =yk-cnnlive-003 &ptdebug=true 0 0 0 Variant 111.22.3.44 111.22.3.45 127.0.0.1:46383
```

### enregistrements TRACE_HTTP_HEADER {#trace-http-header-records}

Les enregistrements de ce type consignent les en-têtes HTTP échangés lors des appels HTTP entre le serveur de manifeste et le client, le serveur d’annonces ou le serveur de contenu. Les champs situés au-delà de TRACE_HTTP_HEADER apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| request_type | string | Type de demande (MAIN ou UNKNOWN) |
| request_response | string | En-tête de réponse (requête ou réponse) |
| header_name | string | Nom de l’en-tête HTTP |
| header_value | string | Valeur d’en-tête HTTP codée en base 64 |

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

### enregistrements TRACE_AD_CALL {#trace-ad-call-records}

Les enregistrements de ce type consignent les résultats des demandes d&#39;annonce du serveur de manifeste. Les champs situés au-delà de TRACE_AD_CALL apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| statut | string | Code d’état HTTP renvoyé |
| request_duration | integer | Temps (millisecondes) entre la requête et la réponse |
| ad_server_requête_url | string | URL de l’appel publicitaire, y compris les paramètres de requête |
| ad_system_id | string | Système publicitaire, à partir de la réponse du serveur publicitaire (Auditude si elle n’est pas spécifiée) |
| avail_id | string | ID de la valeur, à partir du repère publicitaire dans le fichier manifeste de contenu (S/O pour VOD) |
| avail_duration | nombre | Durée (secondes) de la valeur, à partir du repère publicitaire dans le fichier manifeste de contenu (S/O pour VOD) |
| ad_server_response | string | Réponse codée en base 64 du serveur d’annonces |

Exemple :

```
2015-03-25T06:13:31.271Z 14272. . . 189938 TRACE_AD_CALL
200 8 https://ad.stg2.auditude.com/adserver/a?cip=0.0.0.0&g=1000012&of=1.5 &ptcueformat=turner&ptdebug=true&tl=l,150,30,m&tm=63&u=ceceb. . . Auditude IvpIyC. . . 150 PD94bWw. . .
```

### enregistrements TRACE_AD_INSERT, TRACE_AD_RESOLVE et TRACE_AD_REDIRECT {#trace-ad-insert-trace-ad-resolve-and-trace-ad-redirect-records}

Les enregistrements de ce type consignent les résultats des demandes d&#39;annonce indiquées par le type d&#39;enregistrement. Les champs situés au-delà du type d’enregistrement s’affichent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| statut | string | Code d’état HTTP renvoyé |
| avail_id | string | ID de la valeur, à partir du repère publicitaire dans le fichier manifeste de contenu (en direct) ou du serveur manifeste (VOD) |
| ad_type | string | Type de publicité (DIRECT ou REDIRECT) |
| ad_duration | integer | Durée (secondes) de la publicité, d’après la réponse du serveur d’annonces |
| ad_content_url | string | URL du fichier manifeste de la publicité, à partir de la réponse du serveur d’annonces |
| ad_content_url_true | string | URL du fichier manifeste de l’annonce insérée. Vide pour TRACE_AD_REDIRECT. |
| ad_system_id | string | Système publicitaire, à partir de la réponse du serveur publicitaire (Auditude si elle n’est pas spécifiée) |
| ad_id | string | ID de la publicité, à partir de la réponse du serveur d’annonces |
| creative_id | string | ID du créatif, à partir du noeud publicitaire, de la réponse du serveur publicitaire |
| ad_call_id | string | Non utilisé. Réservé pour une utilisation ultérieure. |
| delta | integer | Temps (millisecondes) pris par ce événement |
| misc | string | Raison de l&#39;abandon de la publicité |

>[!NOTE]
>
>Les champs ad_content_url_true, ad_call_id et divers sont facultatifs.

Pour TRACE_AD_RESOLVE et TRACE_AD_INSERT, l’URL du champ ad_content_url_true correspond à la publicité transcodée si elle est disponible. Sinon, le champ est vide pour TRACE_AD_RESOLVE ou identique à ad_content_url pour TRACE_AD_INSERT.

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

### enregistrements TRACE_TRACKING_URL {#trace-tracking-url-records}

Les enregistrements de ce type consignent les résultats des demandes d&#39;annonce du serveur de manifeste. Les champs situés au-delà de TRACE_TRACKING_URL apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| pts | nombre | Horodatage du Programme. Temps passé dans la vidéo pour appeler l’URL. |
| ad_system | string | Système publicitaire (auditude ou roue libre) |
| url | string | URL avec sabot |
| statut | string | État HTTP renvoyé par le ping |

Exemple :

```
2015-06-04T23:24:42.000-0700    1426742736208     3086f5cd . . .    12345    TRACE_TRACKING_URL
    0.000000    ExampleSystem    https://localhost/index.php?stream:test#8.1433485415;
    sid:3086f5cd . . .;pts:0    200
```

### enregistrements TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE {#trace-transcoding-no-media-to-transcode-records}

Les enregistrements de ce type consignent un élément publicitaire manquant. Le seul champ situé au-delà de TRACE_TRANSCODING_NO_MEDIA_TO_TRANSCODE apparaît dans le tableau.

| Champ | Type | Description |
|--- |--- |--- |
| ad_id | string | ID publicitaire complet `(FQ_AD_ID: Q_AD_ID[;Q_AD_ID[;Q_AD_ID...]`] Q_AD_ID : `PROTOCOL:AD_SYSTEM:AD_ID[:CREATIVE_ID[:MEDIA_ID]`] PROTOCOLE : AUDITUDE, VAST) |

### enregistrements TRACE_TRANSCODING_REQUESTED {#trace-transcoding-requested-records}

Les enregistrements de ce type consignent les résultats des demandes de transcodage que le serveur de manifeste envoie à CRS. Les champs situés au-delà de TRACE_TRANSCODING_REQUESTED apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| ad_id | string | ID publicitaire complet |
| ad_manifest_url | string | URL du fichier manifeste de la publicité, à partir de la réponse du serveur d’annonces |
| creative_type | string | Type de support |
| indicateurs | string | ID3 indique si la demande de transcodage inclut une demande d’ajout d’une balise ID3. |
| cible_duration | string | Durée de Cible (en secondes) de l’élément créatif transcodé |

### enregistrements TRACE_TRACKING_REQUEST {#trace-tracking-request-records}

Les enregistrements de ce type indiquent une demande de suivi côté serveur. Les champs situés au-delà de TRACE_TRACKING_REQUEST apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| tracking_url_count | integer | Nombre d’URL de suivi |
| début | flotter | début du fragment PTS (secondes avec une précision de milliseconde) |
| end | flotter | Heure de fin du fragment PTS (secondes avec une précision de milliseconde) |

### enregistrements TRACE_TRACKING_REQUEST_URL {#trace-tracking-request-url-records}

Les enregistrements de ce type fournissent une URL de suivi pour le suivi côté serveur. Les champs situés au-delà de TRACE_TRACKING_REQUEST_URL apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| timestamp | flotter | Durée (en secondes, avec précision 0,001) de la session de lecture pour effectuer un test ping sur l’URL de suivi |
| ad_system | string | Système publicitaire (par exemple, auditude) |
| url | string | URL vers ping |

### enregistrements TRACE_WEBVTT_REQUEST {#trace-webvtt-request-records}

Enregistrements de ce type de journal demande que le serveur manifeste crée pour les légendes WEBVTT. Les champs situés au-delà de TRACE_WEBVTT_REQUEST apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| statut | string | Code d’état HTTP renvoyé |
| vtt_uri | string | URL de la demande |
| début | flotter | Temps début fractionné (secondes avec précision de milliseconde) |
| end | flotter | Temps de fin fractionné (secondes avec précision de milliseconde) |

### enregistrements TRACE_WEBVTT_RESPONSE {#trace-webvtt-response-records}

Enregistre ``of ``ce ``type ``journal ``responses ``du ``manifest ``serveur ``sends ``dans ``clients ```` `answer` ``les légendes. ``requests ```for```WEBVTT `` Les champs situés au-delà de TRACE_WEBVTT_RESPONSE &quot;apparaissent dans l&#39;ordre indiqué dans le tableau, `by`onglets séparés.

| Champ | Type | Description |
|--- |--- |--- |
| statut | string | Code d’état HTTP renvoyé |
| réponse | string | Réponse codée en base 64 envoyée au client |

### enregistrements TRACE_WEBVTT_SOURCE {#trace-webvtt-source-records}

Enregistrements de ce type de réponses au journal des requêtes effectuées par le serveur de manifeste pour les légendes WEBVTT. Les champs situés au-delà de TRACE_WEBVTT_SOURCE apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| statut | string | Code d’état HTTP renvoyé |
| source | string | Contenu VTT d’origine codé en base 64 |


### enregistrements TRACE_MISC {#trace-misc-records}

Les enregistrements de ce type permettent au serveur de manifeste de consigner les événements et les informations non planifiées lors de l&#39;assimilation de publicités. Le champ situé au-delà de TRACE_MISC se compose d’une chaîne de message. Les messages qui peuvent s’afficher sont les suivants :

* Publicité ignorée : AdPlacement `[adManifestURL=https://cdn2.auditude.com/assets/3p/v2/8c/2b/8c2bb. . . .m3u8, durationSeconds=15.0, ignore=false, redirectAd=false, priority=1]`
* AdPlacement adManifestURL=*adManifestURL*, durationSeconds=*secondes*, ignore=*ignore*, redirectAd=*redirectAd, priority=priority***
* L’emplacement de la publicité a renvoyé la valeur null.
* La publicité a été assemblée avec succès.
* Échec de l&#39;appel de publicité : *message* d’erreur.
* Ajout de User-Agent pour récupérer le manifeste brut : *user-agent*.
* Ajout de cookie pour récupérer le manifeste brut : [cookie]
* Message *d&#39;erreur d&#39;URL* demandé par une URL incorrecte. (Échec de l&#39;analyse de l&#39;URL de variante)
* URL appelée : URL *renvoyée : code* de réponse. (URL active)
* URL appelée : Code *de retour d&#39;URL : code* de réponse. (URL VOD)
* Conflit détecté lors de la résolution des publicités : l&#39;un ou l&#39;autre des débuts - milieu ou milieu de la gamme est compris dans les modèles pré-rouleau ou pré-rouleau contenus dans le milieu de la gamme (VOD).
* Exception non gérée détectée générée par le gestionnaire pour URI : *URL* de requête.
* Génération du manifeste de variante terminée. (Variant)
* Génération du manifeste de variante terminée.
* Exception lors de la gestion de la redirection VAST *redirect URL *error: *message* d’erreur.
* Échec de la récupération de la liste de lecture de la publicité pour l’URL *du manifeste de la* publicité.
* Échec de la génération du manifeste ciblé. (HLSManifestResolver)
* Échec de l&#39;analyse de la première réponse d&#39;appel publicitaire : *message* d’erreur.
* Échec du traitement de la demande *GET|POST *pour le chemin d&#39;accès : *URL* de requête. (Live/VOD)
* Échec du traitement de la demande de manifeste en direct : *URL* de requête. (En direct)
* Impossible de renvoyer un manifeste de variante : *message* d’erreur.
* Échec de la validation de l&#39;identifiant de groupe : *ID* de groupe.
* Récupération du manifeste brut : *URL* du contenu. (En direct)
* Après la redirection VAST : *URL* de redirection.
* Disponibilités vides trouvées. (VOD)
* *nombre *publicités trouvées. (VOD)
* Demande HTTP reçue. (Tout premier message)
* La publicité est ignorée car la différence entre la durée de réponse de la publicité (*durée de réponse de la publicité *s) et la durée de la publicité réelle (*durée réelle *s) est supérieure à la limite. (HLSManifestResolver)
* Valeur qui n’a fourni aucune valeur d’ID ignorée. (GroupAdResolver.java)
* La valeur de temps fournie n&#39;est pas valide : *time *pour availId = ID ** de valeur.
* La valeur de durée fournie par la valeur de durée non valide a été ignorée : *duration *for availId = ID ** de valeur.
* Initialisez une nouvelle session. (Variant)
* Méthode HTTP non valide. Ça doit être une GET. (VOD)
* Méthode HTTP non valide. La demande de suivi doit être une instruction GET. (En direct)
* Message *d&#39;erreur* d&#39;URLrequis non valide. (Variant)
* Groupe non valide. (HLSManifestResolver)
* Demande non valide. La légende n&#39;est pas une demande de suivi valide. (VOD)
* Demande non valide. La demande de légende doit être effectuée après l’établissement de la session. (VOD)
* Demande non valide. La demande de suivi doit être effectuée après l&#39;établissement de la session. (VOD)
* Instance de serveur non valide pour l&#39;ID de groupe de surcharge : *ID* de groupe. (En direct)
* Limite des redirections VAST atteinte - *nombre*.
* Appel publicitaire : *URL* d’appel publicitaire.
* Aucun manifeste trouvé pour : *URL* du contenu. (En direct)
* Aucune valeur correspondante n&#39;a été trouvée pour l&#39;ID de la valeur : *ID* valide. (HLSManifestResolver)
* Session de lecture introuvable. (HLSManifestResolver)
* Traitement de la demande VOD pour l’URL *du* contenu du manifeste.
* Traitement de la variante.
* Traitement de la demande de légende pour l’URL *du* contenu manifeste.
* Traitement de la demande de suivi. (VOD)
* Rediriger la réponse publicitaire vide. (VASTStAX)
* Demande : *URL*.
* Renvoi d’une réponse d’erreur pour la demande GET car aucune session de lecture n’a été trouvée. (VOD)
* Renvoi d’une réponse d’erreur pour la demande GET en raison d’une erreur de serveur interne.
* Renvoi d’une réponse d’erreur pour la demande GET spécifiant une ressource non valide : *ID* de demande d&#39;annonce. (VOD)
* Renvoi d&#39;une réponse d&#39;erreur pour la demande GET spécifiant un ID de groupe non valide ou vide : *ID* de groupe. (VOD)
* Renvoi d&#39;une réponse d&#39;erreur pour la demande GET spécifiant une valeur de position de suivi non valide. (VOD)
* Renvoi d’une réponse d’erreur pour la requête GET avec une syntaxe non valide - URL *de* requête. (Live/VOD)
* Renvoi d’une réponse d’erreur pour la requête avec une méthode HTTP non prise en charge : *GET|POST*. (Live/VOD)
* Renvoi du manifeste à partir du cache. (VOD)
* Le serveur est surchargé. Continuer sans la demande de raccordement d’annonces. (Variant)
* Début générant le manifeste ciblé. (HLSManifestResolver)
* Début générant un manifeste de variante à partir de : *URL* du contenu. (Variant)
* Début d’assemblage de publicités dans le manifeste. (Volontaire VODHLSR)
* Tentative d&#39;assemblage de la publicité à *HH:MM:SS*: AdPlacement [URL du manifeste de la publicité&#x200B;*, duréeSeconds=* secondes *, ignorer=* ignorer *, redirigerAd=**redirect ad, priority=priority.*** (HLSManifestResolver)
* Impossible d&#39;obtenir les publicités en raison d&#39;une chronologie incorrecte. Le contenu a été renvoyé sans publicité. (VOD)
* Impossible d&#39;obtenir les publicités - a renvoyé le contenu sans publicité. (VOD)
* Impossible d&#39;obtenir la requête publicitaire et aucune URL de contenu n&#39;a été fournie. (VOD)
* URL valide reçue. (VOD/Variant)
* Variante M3U8 introuvable. (Variant)

### enregistrements TRACE_TRACKING_URL {#trace-tracking-url-records-1}

Le serveur de manifeste génère des enregistrements de ce type après avoir appelé une URL de suivi pendant le processus de suivi côté serveur. Les champs situés au-delà de TRACE_TRACKING_URL apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| pts | nombre | Temps PTS dans le flux |
| ad_system | string | Système publicitaire de la publicité (auditude ou roue libre) |
| url | string | URL avec sabot |
| state | string | Code d’état HTTP |

### enregistrements TRACE_PLAYBACK_PROGRESS {#trace-playback-progress-records}

Le serveur de manifeste génère des enregistrements de ce type lorsqu’il reçoit un signal sur la progression de la lecture au cours du processus de suivi côté serveur. Les champs situés au-delà de TRACE_PLAYBACK_PROGRESS apparaissent dans l’ordre indiqué dans le tableau, séparés par des onglets.

| Champ | Type | Description |
|--- |--- |--- |
| statut | string | Code d’état HTTP |
| bande passante | integer | Bande passante du flux |
| pts | integer | Temps PTS dans le flux |
| ms_time | integer | Heure à laquelle le serveur de manifeste a généré l’URL de suivi |
| url | string | URL de redirection |
| header_user_agent | string | En-tête HTTP User-Agent |
| header_dnt | integer | En-tête HTTP do-not-track |
| effective_remote_address | string | Adresse distante effective IPv4 |
| remote_address | string | Adresse distante IPv4 |

>[!NOTE]
>
>Les quatre derniers champs sont facultatifs.

## Ressources utiles {#helpful-resources}

* Consultez la documentation d’aide complète sur la page de formation et d’assistance [d’](https://helpx.adobe.com/support/primetime.html) Adobe Primetime.
