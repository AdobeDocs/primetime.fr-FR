---
title: API Bootstrap
description: 'API Bootstrap '
translation-type: tm+mt
source-git-commit: bf99c76bbbb67560adc675cf84297b8d3b04e19d
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 0%

---


# API du Bootstrap {#bootstrap-api}

L’API du Bootstrap est généralement l’URL envoyée aux API de lecture vidéo/client.  Pour connaître les options et les paramètres qui peuvent être configurés, consultez les [paramètres de l&#39;API du Bootstrap](#bootstrap-api-parameters).

## Envoyer une commande au serveur de manifeste {#send-a-command-to-the-manifest-server}

1. Envoyez une demande `HTTP GET` pour une URL d’amorçage construite à l’aide du modèle suivant :

   ```
   https://{manifest-server:port}/auditude/variant/
    {PublisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]
    ?{query parameters}
   ```

   * **Extension** de fichierDefined. `.m3u8` si le manifeste de cible est HLS,  `.mpd` si le manifeste de cible se trouve dans la DASH.

   * **** PublisherAssetIDRrequired. ID unique de l’éditeur pour le contenu spécifique.

   * **Contenu** URLRrequired. URL du fichier de contenu M3U8, codé Base64 pour être sécurisé dans l&#39;URL du serveur de manifeste. L’URL de contenu doit pointer vers un fichier variante M3U8, même s’il n’y a qu’un seul flux de débit binaire.

   * **** Paramètres de requêteCes paramètres constituent la partie la plus variée de la requête. Ils indiquent au serveur de manifeste quel type de client effectue la demande et ce qu&#39;il souhaite que le serveur de manifeste fasse.

   Par exemple :

   ```
   https://manifest.auditude.com/auditude/variant/
    {publisherAssetID}/{Content URL (base64)}.[m3u8 or mpd]?
   u={Asset ID}&z={zone}&_sid_=0&pttrackingmode=simple
   &pttrackingversion=v2&live=false
   ```

   **Requêtes HTTP ou HTTPS**

   Le serveur de manifeste crée des URL à l’aide du même protocole HTTP de la demande du client. Si un lecteur effectue une requête HTTP (http) non sécurisée, le serveur de manifeste renvoie des URL de suivi de manifeste et d’Auditude avec le protocole http. Si un lecteur établit une connexion HTTP sécurisée (https), un serveur manifest, il renvoie des URL de suivi de manifeste et d’Auditude avec le protocole https.

   >[!NOTE]
   >
   >Le serveur de manifeste ne peut pas modifier le protocole (HTTP ou HTTPS) des balises de suivi tierces. Vous devez contacter le contenu et les fournisseurs d’annonces tiers pour qu’ils configurent les protocoles souhaités.  Les protocoles d’URL de segments peuvent être modifiés, cependant, par défaut, utilisez les mêmes protocoles que ceux définis dans les manifestes de cible.

## Paramètres de l&#39;API Bootstrap {#bootstrap-api-parameters}

Les paramètres de requête indiquent au serveur de manifeste quel type de client a envoyé la demande et ce que ce client souhaite que le serveur de manifeste fasse. Certains sont requis et d&#39;autres ont des formats ou des valeurs acceptables spécifiques.
L’URL complète se compose de l’URL de base suivie d’un point d’interrogation, puis d’arguments `parameterName=value` séparés par des esperluettes. Par exemple, `Base URL?name1=value1&name2=value2& . . .&name n=value n`.

Le serveur de manifeste reconnaît les paramètres suivants. Toute chaîne de requête\
sont transmis au serveur d’annonces.

| parameter | description | formats |
|---|---|---|
| _sid_ | Identifiant unique que le serveur de manifeste utilisera pour générer l&#39;identifiant de session. | Obligatoire pour les DASH/HLS |
| live | Avertit l’Ad Insertion Primetime que l’élément de contenu transmis est un flux en direct.  Si ce paramètre n’est pas transmis, l’insertion de publicité Primetime effectue une requête secondaire sur l’appel de manifeste initial afin de déterminer si le manifeste est actif ou vide.<br>Valeurs possibles : <br>true pour <br>contentfalse en direct pour vod <br>contentomit pour la détection automatique | Facultatif pour HLS.  Requis pour DASH |
| z | ID de zone de la ressource qui doit être fournie à l’Ad Insertion Primetime. Fourni par votre gestionnaire de compte technique Adobe. | Obligatoire pour les DASH/HLS |
| pabimode | Active [l’insertion partielle de coupures publicitaires](/help/primetime-ad-insertion/getting-started/ad-insertion-live-linear-stream.md#partial-ad-break-support) pour les flux en direct.<br>Valeurs possibles : <br>true pour <br>autoriser la désactivation (désactivation par défaut) | HLS/DASH |
| ptadtimeout | Permet de limiter le temps global de résolution des publicités si les fournisseurs en aval mettent trop de temps à répondre.  Les réponses longues peuvent provoquer des problèmes de lecture, ce qui permet à l’interface d’identification de Primetime de forcer une réponse dans un délai précis.<br>Valeurs possibles : chaîne <br>numérique en millisecondes.<br>omettre de désactiver (désactivé par défaut) | HLS/DASH |
| ptadwindow | Durée (en secondes) de la fenêtre de consultation et de prise de décision — jusqu&#39;où l&#39;Ad Insertion Primetime va chercher des indices publicitaires lorsqu&#39;un utilisateur du DVR rejoint le flux. La valeur zéro désactivera la prise de décision publicitaire intermédiaire dans le manifeste initial, la prise de décision ne reprenant qu’après la première mise à jour. Ce paramètre est utile pour désactiver l’insertion publicitaire dans des sessions qui ne peuvent durer que quelques secondes (c’est-à-dire un basculement de canal).<br>Valeurs possibles : chaîne <br>numérique 0-1800 (1800 par défaut) | HLS uniquement |
| ptassetid | ID unique du contenu affecté et conservé par l’éditeur.  Requis en cas d’utilisation conjointe avec la mise à l’échelle de l’annonce Akamai. | HLS/DASH |
| ptcdn | Liste d’un ou de plusieurs CDN pour héberger des ressources transcodées. Pour plus d&#39;informations, voir [Diffusion et enregistrement](/help/primetime-ad-insertion/just-in-time-transcoding/delivery-and-storage.md).<br>Valeurs possibles : <br>akamai, level3, lnw (limelight Networks), comcast.<br>Par défaut, les réseaux CDN Ad Insertion Primetime sont utilisés. | HLS/DASH |
| ptcueformat | Format spécifié des balises pour effectuer la prise de décision publicitaire (par exemple, scte35).<br>Valeurs possibles : <br>dpisimple, dpiscte35, <br>elementalPour les formats de indices personnalisés, contactez votre gestionnaire de compte technique pour connaître la valeur à utiliser pour votre cas d’utilisation. | HLS/DASH |
| ptfailover | Indique au serveur de manifeste d’identifier les flux Principaux et de basculement spécifiés dans la liste de lecture principale et de les traiter comme des jeux disjoints. Cela facilite le basculement et évite les erreurs de minutage. (Pour les périphériques Apple HLS uniquement). Pour plus d’informations, voir [Facilitation du changement de lecteur HLS](hls-switching-to-failover.md) | HLS uniquement |
| ptmulticall | Si cette option est activée, une demande d’annonce distincte est effectuée pour chaque valeur trouvée dans une ressource VOD.  Par défaut, l’Ad Insertion Primetime tente de collecter toutes les informations disponibles et de les envoyer au serveur d’annonces dans une seule requête. Valeurs possibles : true pour activer, <br>omit pour désactiver (désactivé par défaut) | HLS/DASH |
| ptparallelstream | Permet aux clients disposant de lecteurs qui demandent des flux audio ou vidéo déuxés CMAF en parallèle de s’assurer que les publicités des pistes audio et vidéo sont cohérentes. | HLS uniquement |
| ptprotocommutateur | Active les règles de réécriture de manifeste nommées et les règles de récupération des publicités, qui seront généralement configurées par votre représentant du support technique.<br>Exemple : adfetch_fw, cdn_akm | HLS/DASH |
| pttagds | Permet l&#39;injection de balises EXT-X-DISCONTINUITY-SEQUENCE dans les en-têtes HLS.Valeurs possibles : true pour autoriser la désactivation (désactivation par défaut) | HLS uniquement |
| pttimeline | Chaîne contenant la chronologie souhaitée pour l’emplacement et le contenu de la publicité, qui remplace les coupures publicitaires dans le flux de contenu. [ Voir Format de chronologie VOD  ] | HLS/DASH |
| pttoken | Active les schémas de protection des jetons d’autorisation de fragment/segment de contenu pour les réseaux de diffusion de contenu<br>Valeurs possibles :<br>akamai, lnw (limelight), ctl (centurylink) (la segmentation par défaut est désactivée) | HLS/DASH |
| pttrackingmode | Activez les schémas de suivi des publicités.<br>Valeurs possibles : <br>simple pour le <br>suivi publicitaire côté client pour le <br>suivi publicitaire côté serveur simplesstm pour le suivi publicitaire hybride client/serveur (par défaut, aucun suivi publicitaire n’est effectué) | HLS/DASH |
| pttrackingposition | Indique au serveur de manifeste de renvoyer uniquement les informations de suivi des publicités. Ne spécifiez pas ce paramètre dans la demande d&#39;amorçage.<br>Remarque : Le serveur de manifeste ignore toutes les valeurs transmises. Cependant, si vous transmettez une chaîne nulle ou vide, le serveur de manifeste renvoie le M3U8 | HLS/DASH<br>Suivi côté client |
| pttrackingversion | Définit la version de format à renvoyer.<br>Valeurs possibles : <br>v1, v2, v3 ou vmap | HLS/DASH<br>Suivi côté client |
| scteTracking | Ce paramètre indique au serveur de manifeste que le lecteur qui récupère le M3U8 a besoin des informations de balise SCTE pour être récupéré.<br>Valeurs possibles : <br>true ou false (false par défaut)<br> Remarque : Les données SCTE-35 sont renvoyées dans le fichier annexe JSON avec la combinaison suivante de valeurs de paramètre de requête : <br>ptcueformat=turner | élémentaire | nfl | DPIScte35<br>pttrackingversion=v2<br>scteTracking=true<br> | HLS uniquement |
| vetargetmultiplicateur | Le nombre de segments à partir du point d’activation Le décalage de pré-roulage est configuré à l’aide : ( vetargetmultiplicateur * targetduration ) + vebufferlength<br>Remarque : Ce paramètre s’applique aux flux HLS en direct/linéaire uniquement <br>Valeurs possibles :<br>nombre flottant<br>(par défaut : 3.0 - identique à la spécification HLS) | HLS uniquement |
| vebufferLength | Nombre de secondes écoulées depuis le point de production, utilisé conjointement avec le multiplicateur de vetargetmultiplicateur.<br>Remarque : Ce paramètre s’applique aux flux HLS en direct/linéaires <br>uniquementValeurs possibles : flotteur<br> <br>numérique (par défaut : 3.0) | HLS uniquement |
