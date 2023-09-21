---
title: Paramètres de requête du serveur de manifeste
description: Les paramètres de requête indiquent au serveur de manifeste quel type de client a envoyé la demande et ce que ce client souhaite que le serveur de manifeste fasse. Certains sont obligatoires et d’autres ont des formats ou des valeurs acceptables spécifiques.
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 0%

---


# Paramètres de requête du serveur de manifeste {#ms-query-params}

Les paramètres de requête indiquent au serveur de manifeste quel type de client a envoyé la demande et ce que ce client souhaite que le serveur de manifeste fasse. Certains sont obligatoires et d’autres ont des formats ou des valeurs acceptables spécifiques.

L’URL complète se compose de l’URL de base suivie d’un point d’interrogation, puis `parameterName=value` arguments, séparés par des esperluettes : `Base URL?name1=value1&name2=value2& . . .&name n=value n`.

## Paramètres reconnus {#section_072845B7FA94468C8068E9092983C9E6}

Le serveur de manifeste reconnaît les paramètres suivants. Il les traite ou les transmet, avec tous les paramètres non reconnus, au serveur d’annonces.

| Clé | Description | Obligatoire | Valeurs valides |
|---|---|---|---|
| `__sid__` | Identifiant unique utilisé par le serveur de manifeste pour générer l’ID de session. | Oui | Alphanumérique |
| g | Type de périphérique client | Lorsque les règles de ciblage dépendent du type d’appareil | Voir list at [Types de clients](https://adobeprimetime.zendesk.com). Nécessite un accès Zendesk. |
| k | Mots-clés pour le ciblage publicitaire personnalisé | Non | Chaîne compatible avec les URL au format `key1=value1;key2=value2;. . .` |
| u | ID de ressource d’insertion de publicités Primetime. | Oui | Valeur de hachage MD5 |
| z | Identifiant de zone d’insertion de publicité Primetime pour la ressource. | Oui | Entier |
| enableC3 | Le client se trouve dans une fenêtre C3. Si la valeur est true, remplacez uniquement les ressources locales ; dans le cas contraire, remplacez toutes les ressources disponibles. | Non | Booléen |
| live | Indique si le contenu est un flux Live ou VOD (vidéo à la demande). | Client Akamai Ad Scaler ou iOS Safari. | Booléen |
| `pabimode` | [Activer l’insertion de coupure publicitaire partielle](/help/primetime-ad-insertion/~old-msapi-topics/ms-insert-ads/partial-ad-break-insetion.md) la prise en charge. <br> Activez s’il est défini sur true ou démarrez.<br> Désactivez si la valeur est false. | Non (désactivée par défaut) | start, true ou false |
| `ptadwindow` | Durée (secondes) de la fenêtre de regroupement des publicités : combien de temps il faut remonter pour rechercher des publicités lorsqu’un utilisateur de l’enregistreur numérique rejoint la diffusion. | Non (par défaut = 1800) | 0 à 1800 |
| `ptassetid` | Identifiant unique du contenu affecté et géré par l’éditeur. | Akamai Ad Scaler | Chaîne compatible avec les URL |
| `ptcdn` | Liste d’un ou de plusieurs CDN pour héberger des ressources transcodées. Voir [Prise en charge multi-CDN](/help/primetime-ad-insertion/~old-creative-repackaging-service/multi-cdn-supportt.md). | Non (default=Akamai) | Exemple : Akamai, Level3, Limelight, Comcast |
| `ptcueformat` | Nom du format de repère de publicité personnalisé présent dans le M3U8. | Non | DPISimple, DPIScte35, Elemental, NBC, NFL ou Turner |
| `ptfailover` | Indique au serveur de manifeste d’identifier les flux principaux et de basculement spécifiés dans la liste de lecture principale et de les traiter comme des ensembles distincts. Cela facilite le basculement et évite les erreurs de synchronisation. (Pour les appareils Apple HLS uniquement). Voir  [Faciliter le changement de lecteur HLS](/help/primetime-ad-insertion/~old-msapi-topics/ms-insert-ads/hls-switching-to-failover.md). | Non | true |
| `ptmulticall` | S’il est défini sur true, plusieurs appels publicitaires Auditude pour FER sont effectués ; un pour chaque coupure publicitaire. Si elle est absente ou définie sur false, un appel publicitaire est effectué vers l’auditude pour FER. | Non | Booléen <br> **Remarque**: les exigences suivantes : <ul><li>`ptcueformat` doit être défini sur nbc</li><li>Le paramètre pttimeline est ignoré.</li></ul> |
| `ptplayer` | Lecteur effectuant la requête. | iOS/Safari | ios-mobileweb |
| `ptrendition` | Généré automatiquement par l’insertion de publicités et utilisé par Akamai. N’ajoutez ou ne supprimez pas. | Akamai Ad Scaler | |
| `pttagds` | Activer [EXT-X- DISCONTINUITÉ- SÉQUENCE](https://tools.ietf.org/html/draft-pantos-http-live-streaming-19#section-4.3.3.3) tags | Non | true - le serveur manifest inclut une balise de séquence avant le contenu de chaque fichier m3u8 qu’il envoie ; si le paramètre n’est pas présent ou s’il est faux, le serveur manifest n’inclut pas de balise de séquence. |
| `pttimeline` | Chaîne contenant la chronologie souhaitée du placement et du contenu de la publicité, qui remplace les coupures publicitaires dans le flux de contenu. | Non | [Chronologie VOD](/help/primetime-ad-insertion/~old-msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md) |
| `pttoken` | Activez les jetons d’autorisation de segment TS.<br> **Remarque**: seuls les jetons CDN Akamai pris en charge | Pour les jetons d’autorisation de segment TS | Booléen |
| `pttrackingmode` | Activez le suivi des publicités : côté client personnalisé (simple), côté serveur (sstm) ou hybride (simplesstm). | Non | simple, sstm ou simple.<br> **Remarque**: si ce paramètre n’est pas inclus, le #EX-X-MARKER est injecté dans le manifeste. Voir [Directive EXT-X-MARKER](/help/primetime-ad-insertion/~old-msapi-topics/ms-at-effectiveness/ms-api-playlists.md). |
| `pttrackingposition` | Indique au serveur de manifeste de renvoyer uniquement les informations de suivi des publicités. Ne spécifiez pas ce paramètre dans la requête de bootstrap. | Suivi côté client | Remarque alphanumérique : le serveur de manifeste ignore toutes les valeurs transmises. Cependant, si vous transmettez une chaîne nulle ou vide, le serveur de manifeste renvoie le M3U8 au lieu des informations de suivi. |
| `pttrackingversion` | Version du format des informations de suivi côté client. | Suivi côté client | v1, v2, v3 ou vmap |
| `scteTracking` | Récupérez M3U8 avant de récupérer les informations de suivi SCTE dans le sidecar JSON V2. <br>Ce paramètre indique au serveur de manifeste que le lecteur qui récupère le M3U8 a besoin que les informations de balise SCTE soient récupérées. | Non (par défaut : false) | true ou false. <br> **Remarque**: les données SCTE-35 sont renvoyées dans le fichier sidecar JSON avec la combinaison suivante de valeurs de paramètre de requête : <ul><li>`ptcueformat=turner | elemental | nfl | DPIScte35`</li><li>`pttrackingversion=v2`</li><li>`scteTracking=true`</li></ul> |
| `vetargetmultiplier` | Le nombre de segments à partir du point d’activation Le décalage preroll est configuré à l’aide : `(vetargetmultiplier * targetduration + vebufferlength`<br/><br/>**Remarque**: actif/linéaire uniquement | Non (par défaut : 3.0) | Flottant |
| `vebufferLength` | Nombre de secondes à partir du point d’activation. **Remarque**: actif/linéaire uniquement. | Non (par défaut : 3.0) | Flottant |
