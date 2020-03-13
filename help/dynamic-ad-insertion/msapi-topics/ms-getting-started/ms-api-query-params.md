---
description: Les paramètres  du indiquent au serveur de manifeste quel type de client a envoyé la demande et ce que ce client souhaite que le serveur de manifeste fasse. Certains sont obligatoires et d’autres ont des formats ou des valeurs acceptables spécifiques.
seo-description: Les paramètres  du indiquent au serveur de manifeste quel type de client a envoyé la demande et ce que ce client souhaite que le serveur de manifeste fasse. Certains sont obligatoires et d’autres ont des formats ou des valeurs acceptables spécifiques.
seo-title: Paramètres  du du serveur de manifeste
title: Paramètres  du du serveur de manifeste
uuid: 03632da3-ae20-427c-bd24-4794ab627cc8
translation-type: tm+mt
source-git-commit: 358c5b02d47f23a6adbc98e457e56c8220cae6e9

---


# Paramètres  du du serveur de manifeste {#manifest-server-query-parameters}

Les paramètres  du indiquent au serveur de manifeste quel type de client a envoyé la demande et ce que ce client souhaite que le serveur de manifeste fasse. Certains sont obligatoires et d’autres ont des formats ou des valeurs acceptables spécifiques.

L’URL complète se compose de l’URL de base suivie d’un point d’interrogation, puis d’arguments, séparés par des esperluettes : `parameterName=value` `Base URL?name1=value1&name2=value2& . . .&name n=value n`

## Paramètres reconnus {#section_072845B7FA94468C8068E9092983C9E6}

Le serveur de manifeste reconnaît les paramètres suivants. Il les traite ou les transmet, avec tous les paramètres non reconnus, au serveur d’annonces.

| Clé | Description | Obligatoire | Valeurs valides |
|--- |--- |--- |--- |
| `__sid__` | ID unique utilisé par le serveur de manifeste pour générer l’ID de session. | Oui | Alphanumérique |
| g | Type de périphérique client | Lorsque les règles de ciblage dépendent du type de périphérique | Reportez-vous à la page  sur les types [de](https://adobeprimetime.zendesk.com) client (nécessite un accès Zendesk). |
| k | Mots-clés pour le ciblage publicitaire personnalisé | Non | Chaîne sécurisée pour l’URL au format key1=value1;key2=value2;. . . |
| u | ID du fichier d’insertion et de priorité. | Oui | Valeur de hachage MD5 |
| z | ID de zone d’insertion de la ressource au moment de la première lecture et de l’instant. | Oui | Entier |
| enableC3 | Le client se trouve dans une fenêtre C3. Si la valeur est true, remplacez uniquement les disponibilités locales ; dans le cas contraire, remplacez toutes les valeurs disponibles. | Non | Booléen |
| live | Indique si le contenu est un flux en direct ou VOD (vidéo à la demande). | Client Akamai Ad Scaler ou Safari iOS | Booléen |
| pabimode | [Activer la prise en charge de l&#39;insertion](../../msapi-topics/ms-insert-ads/partial-ad-break-insetion.md) partielle de coupures publicitaires Activer si true ou  Désactiver si false | Non (la valeur par défaut est désactivée) |  , true ou false |
| ptadwindow | Durée (secondes) de la fenêtre de raccordement d’annonces publicitaires : combien de temps pour rechercher des publicités lorsqu’un utilisateur d’un DVR rejoint le flux. | Non (par défaut = 1800) | 0 à 1 800 |
| ptassetid | Identifiant unique du contenu affecté et conservé par l’éditeur. | Akamai Ad Scaler | Chaîne sécurisée pour l’URL |
| ptcdn |  d’un ou de plusieurs CDN pour héberger des fichiers transcodés. Reportez-vous à la page Prise en charge [de](../../creative-repackaging-service/multi-cdn-supportt.md)plusieurs réseaux CDN. | Non (par défaut=Akamai) | Exemple : Akamai, Niveau3, Limelight, Comcast |
| ptcueformat | Nom du format de repère publicitaire personnalisé présent dans le M3U8. | Non | DPISimple, DPIScte35, Elemental, NBC, NFL ou Turner |
| ptfailover | Indique au serveur de manifeste d’identifier les flux principaux et de basculement spécifiés dans la liste de lecture principale et de les traiter comme des jeux disjoints. Cela facilite le basculement et évite les erreurs de minutage. (Pour les périphériques Apple HLS uniquement). Voir [Faciliter le changement](../../msapi-topics/ms-insert-ads/hls-switching-to-failover.md) de lecteur HLS . | Non | true |
| ptmulticall | S’il est défini sur true, plusieurs appels publicitaires Auditude pour FER effectués ; une pour chaque coupure publicitaire.  En cas d’absence ou de valeur false, un appel publicitaire est effectué à l’auditude pour FER. | Non | Remarque booléenne :  Les conditions suivantes sont requises : <ul><li>Le paramètre ptcueformat doit être défini sur nbc</li><li>le paramètre pttimeline est ignoré.</li></ul> |
| ptplayer | Lecteur qui émet la requête. | iOS/Safari | ios-mobileweb |
| ptrendition | Généré automatiquement par insertion de publicité et utilisé par Akamai. N’ajoutez ou ne supprimez pas. | Akamai Ad Scaler |  |
| pttagds | Activer les balises [EXT-X- DISCONTINUITÉ- SÉQUENCE](https://tools.ietf.org/html/draft-pantos-http-live-streaming-19#section-4.3.3.3) | Non | true - le serveur manifest inclut une balise de séquence avant le contenu de chaque fichier m3u8 qu&#39;il envoie ; si le paramètre n’est pas présent ou s’il est faux, le serveur manifest n’inclut pas de balise de séquence. |
| pttimeline | Chaîne contenant la chronologie souhaitée pour l’emplacement et le contenu de la publicité, qui remplace les coupures publicitaires dans le flux de contenu. | Non | Chronologie VOD (voir le format [de chronologie](../../msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md)VOD) |
| pttoken | Activer les jetons d’autorisation de segment TS Remarque :  Seuls les jetons CDN Akamai pris en charge | Pour les jetons d’autorisation de segment TS | Booléen |
| pttrackingmode | Activer le suivi des publicités ; côté client personnalisé (simple), côté serveur (sstm) ou hybride (simplesstm). | Non | simple, sstm ou simple Remarque :  Si ce paramètre n’est pas inclus, le #EX-X-MARKER est injecté dans le manifeste. Voir Directive [EXT-X-MARKER](../../msapi-topics/ms-at-effectiveness/ms-api-playlists.md). |
| pttrackingposition | Indique au serveur de manifeste de renvoyer uniquement les informations de suivi des publicités. Ne spécifiez pas ce paramètre dans la requête d’amorçage. | Suivi côté client | Note alphanumérique :  Le serveur de manifeste ignore toutes les valeurs transmises. Cependant, si vous transmettez une chaîne nulle ou vide, le serveur de manifeste renvoie le M3U8 au lieu des informations de suivi. |
| pttrackingversion | Version de format des informations de suivi côté client. | Suivi côté client | v1, v2, v3 ou vmap |
| scteTracking | Récupérez M3U8 avant de récupérer les informations de suivi SCTE dans le sidecar JSON V2.  <br/>Ce paramètre indique au serveur de manifeste que le lecteur qui récupère le M3U8 a besoin des informations de balise SCTE pour être récupéré. | Non (par défaut :  false ) | true ou false Remarque :  Les données SCTE-35 sont renvoyées dans le fichier sidecar JSON avec la combinaison suivante de valeurs de paramètre  : <ul><li>`ptcueformat=turner | elemental | nfl | DPIScte35` </li><li>pttrackingversion=v2 </li><li>scteTracking=true</li></ul> |
| vetargetmultiplicateur | Le nombre de segments à partir du point de production Le décalage de pré-roulage est configuré à l’aide de :   `(  vetargetmultiplier  *  targetduration ) +  vebufferlength` Remarque <br/><br/>****:  En direct/Linéaire uniquement | Non (par défaut :  3.0 ) | Flottant |
| vebufferLength | Nombre de secondes à partir du point de production Remarque :  En direct/Linéaire uniquement | Non (par défaut :  3.0 ) | Flottant |
