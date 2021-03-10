---
title: Paramètres de requête du serveur de manifeste
description: Les paramètres de requête indiquent au serveur de manifeste quel type de client a envoyé la demande et ce que ce client souhaite que le serveur de manifeste fasse. Certains sont requis et d'autres ont des formats ou des valeurs acceptables spécifiques.
seo-title: Paramètres de requête du serveur de manifeste
seo-description: Les paramètres de requête indiquent au serveur de manifeste quel type de client a envoyé la demande et ce que ce client souhaite que le serveur de manifeste fasse. Certains sont requis et d'autres ont des formats ou des valeurs acceptables spécifiques.
uuid: 03632da3-ae20-427c-bd24-4794ab627cc8
translation-type: tm+mt
source-git-commit: e1e33d3ac0aad44859cd49566331524da72ac7e4
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# Manifest server requête parameters {#ms-query-params}

Les paramètres de requête indiquent au serveur de manifeste quel type de client a envoyé la demande et ce que ce client souhaite que le serveur de manifeste fasse. Certains sont requis et d&#39;autres ont des formats ou des valeurs acceptables spécifiques.

L’URL complète se compose de l’URL de base suivie d’un point d’interrogation, puis d’`parameterName=value` arguments, séparés par des esperluettes : `Base URL?name1=value1&name2=value2& . . .&name n=value n`.

## Paramètres reconnus {#section_072845B7FA94468C8068E9092983C9E6}

Le serveur de manifeste reconnaît les paramètres suivants. Il les traite ou les transmet, avec tous les paramètres non reconnus, au serveur d’annonces.

| Clé | Description | Obligatoire | Valeurs valides |
|---|---|---|---|
| `__sid__` | ID unique utilisé par le serveur de manifeste pour générer l’ID de session. | Oui | alphanumérique |
| g | Type de périphérique client | Lorsque les règles de ciblage dépendent du type de périphérique | Voir liste à [Types de client](https://adobeprimetime.zendesk.com). Requiert un accès Zendesk. |
| k | Mots-clés pour le ciblage publicitaire personnalisé | Non | Chaîne URL sécurisée au format `key1=value1;key2=value2;. . .` |
| u | ID du fichier d’insertion et de priorité. | Oui | Valeur de hachage MD5 |
| z | ID de zone d’insertion et d’heure de priorité pour la ressource. | Oui | Entier |
| enableC3 | Le client se trouve dans une fenêtre C3. Si la valeur est true, remplacez uniquement les disponibilités locales ; sinon, remplacez toutes les disponibilités. | Non | Boolean |
| live | Indique si le contenu est un flux en direct ou VOD (vidéo à la demande). | Client Akamai Ad Scaler ou iOS Safari. | Boolean |
| `pabimode` | [Activez la prise en charge de l’](/help/primetime-ad-insertion/~old-msapi-topics/ms-insert-ads/partial-ad-break-insetion.md) insertion de coupures publicitaires partielles. <br> Activez si la valeur est true ou début.<br> Désactivez si la valeur est false. | Non (la valeur par défaut est désactivée) | début, true ou false |
| `ptadwindow` | Durée (secondes) de la fenêtre de raccordement d’annonces : combien de temps pour rechercher des publicités lorsqu’un utilisateur d’un enregistreur numérique rejoint le flux. | Non (par défaut = 1800) | 0 à 1800 |
| `ptassetid` | ID unique du contenu affecté et conservé par l’éditeur. | Akamai Ad Scaler | Chaîne sécurisée pour les URL |
| `ptcdn` | Liste d’un ou de plusieurs CDN pour héberger des ressources transcodées. Voir [Prise en charge de CDN multiple](/help/primetime-ad-insertion/~old-creative-repackaging-service/multi-cdn-supportt.md). | Non (par défaut=Akamai) | Exemple : Akamai, Niveau3, Limelight, Comcast |
| `ptcueformat` | Nom du format de repère publicitaire personnalisé présent dans le M3U8. | Non | DPISimple, DPIScte35, Elemental, NBC, NFL ou Turner |
| `ptfailover` | Indique au serveur de manifeste d’identifier les flux Principaux et de basculement spécifiés dans la liste de lecture principale et de les traiter comme des jeux disjoints. Cela facilite le basculement et évite les erreurs de minutage. (Pour les périphériques Apple HLS uniquement). Voir [Facilitation du changement de lecteur HLS](/help/primetime-ad-insertion/~old-msapi-topics/ms-insert-ads/hls-switching-to-failover.md). | Non | true |
| `ptmulticall` | Si ce paramètre est défini sur true, plusieurs appels publicitaires Auditude pour FER sont effectués ; une pour chaque coupure publicitaire. Si elle est absente ou définie sur false, un appel publicitaire est effectué à l’auditude pour FER. | Non | Booléen <br> **Remarque** : Les conditions requises sont les suivantes : <ul><li>`ptcueformat` doit être défini sur nbc</li><li>le paramètre pttimeline est ignoré.</li></ul> |
| `ptplayer` | Joueur qui fait la demande. | iOS/Safari | ios-mobileweb |
| `ptrendition` | Généré automatiquement par insertion publicitaire et utilisé par Akamai. N’ajoutez ou ne supprimez pas. | Akamai Ad Scaler |  |
| `pttagds` | Activez les balises [EXT-X- DISCONTINUITÉ- SEQUENCE](https://tools.ietf.org/html/draft-pantos-http-live-streaming-19#section-4.3.3.3). | Non | true - manifest server inclut une balise de séquence avant le contenu de chaque fichier m3u8 qu&#39;il envoie ; si le paramètre n’est pas présent ou n’est pas vrai, le serveur manifest n’inclut pas de balise de séquence. |
| `pttimeline` | Chaîne contenant la chronologie souhaitée pour l’emplacement et le contenu de la publicité, qui remplace les coupures publicitaires dans le flux de contenu. | Non | [Chronologie VOD](/help/primetime-ad-insertion/~old-msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md) |
| `pttoken` | Activez les jetons d&#39;autorisation de segment TS.<br> **Remarque** : Seuls les jetons CDN Akamai pris en charge | Pour les jetons d’autorisation de segment TS | Boolean |
| `pttrackingmode` | Activer le suivi des publicités ; soit côté client personnalisé (simple), côté serveur (sstm), soit hybride (simplesstm). | Non | simple, sstm ou simple.<br> **Remarque** : Si ce paramètre n&#39;est pas inclus, #EX-X-MARKER est injecté dans le manifeste. Voir [Directive EXT-X-MARKER](/help/primetime-ad-insertion/~old-msapi-topics/ms-at-effectiveness/ms-api-playlists.md). |
| `pttrackingposition` | Indique au serveur de manifeste de renvoyer uniquement les informations de suivi des publicités. Ne spécifiez pas ce paramètre dans la demande d&#39;amorçage. | Suivi côté client | Note alphanumérique :  Le serveur de manifeste ignore toutes les valeurs transmises. Cependant, si vous transmettez une chaîne nulle ou vide, le serveur de manifeste renvoie le M3U8 au lieu des informations de suivi. |
| `pttrackingversion` | Version du format des informations de suivi côté client. | Suivi côté client | v1, v2, v3 ou vmap |
| `scteTracking` | Récupérez M3U8 avant de récupérer les informations de suivi SCTE dans le sidecar JSON V2. <br>Ce paramètre indique au serveur de manifeste que le lecteur qui récupère le M3U8 a besoin des informations de balise SCTE pour être récupéré. | Non (par défaut : false) | true ou false. <br> **Remarque** : Les données SCTE-35 sont renvoyées dans le fichier annexe JSON avec la combinaison suivante de valeurs de paramètre de requête : <ul><li>`ptcueformat=turner | elemental | nfl | DPIScte35`</li><li>`pttrackingversion=v2`</li><li>`scteTracking=true`</li></ul> |
| `vetargetmultiplier` | Le nombre de segments à partir du point d’activation Le décalage de pré-roulage est configuré à l’aide : `(vetargetmultiplier * targetduration + vebufferlength`<br/><br/>**Note** :  En direct/Linéaire uniquement | Non (par défaut :  3.0) | Flottant |
| `vebufferLength` | Nombre de secondes écoulées depuis le point de production. **Remarque** : En direct/Linéaire uniquement. | Non (par défaut : 3.0) | Flottant |