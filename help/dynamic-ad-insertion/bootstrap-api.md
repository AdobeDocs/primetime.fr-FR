---
title: API Bootstrap
description: null
translation-type: tm+mt
source-git-commit: aa43834fea161c537c448b7616c9bd8f779d1a74
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---


# API Bootstrap {#bootstrap-api}

Paramètres requisGénération d&#39;une amorce

## Description du paramètre {#parameter-description}

| parameter | description | formats |
|---|---|---|
| pabimode | Permet l’insertion [](ad-insertion-live-linear-stream.md#partial-ad-break-support) partielle de coupures publicitaires pour les flux en direct. Valeurs possibles : true pour autoriser la désactivation (désactivation par défaut) | HLS/DASH |
| ptadwindow | Durée (en secondes) de la fenêtre de consultation et de prise de décision — jusqu&#39;où l&#39;Ad Insertion Primetime va chercher des indices publicitaires lorsqu&#39;un utilisateur du DVR rejoint le flux. La valeur zéro désactivera la prise de décision publicitaire intermédiaire dans le manifeste initial, la prise de décision ne reprenant qu’après la première mise à jour. Ce paramètre est utile pour désactiver l’insertion publicitaire dans des sessions qui ne peuvent durer que quelques secondes (c’est-à-dire un basculement de canal). Valeurs possibles : chaîne numérique 0-1800 (1800 par défaut) | HLS uniquement |
| ptassetid | ID unique du contenu affecté et conservé par l’éditeur.  Requis en cas d’utilisation conjointe avec la mise à l’échelle de l’annonce Akamai. | HLS/DASH |
| ptcdn | Liste d’un ou de plusieurs CDN pour héberger des ressources transcodées. Pour plus d’informations, voir Prise en charge [de](multi-cdn-support.md)plusieurs CDN. Valeurs possibles : akamai, level3, lnw (réseaux limelight), comcastPar défaut, les réseaux CDN Ad Insertion Primetime sont utilisés | HLS/DASH |
| ptcueformat | Format spécifié des balises pour effectuer la prise de décision publicitaire (par exemple, scte35). Valeurs possibles : dpisimple, dpiscte35, élémentaire Pour les formats de indices personnalisés, veuillez contacter votre gestionnaire de compte technique pour connaître la valeur à utiliser pour votre cas d&#39;utilisation. | HLS/DASH |
| ptfailover | Indique au serveur de manifeste d’identifier les flux Principaux et de basculement spécifiés dans la liste de lecture principale et de les traiter comme des jeux disjoints. Cela facilite le basculement et évite les erreurs de minutage. (Pour les périphériques Apple HLS uniquement). Pour plus d’informations, voir [Facilitation du changement de lecteur HLS.](hls-switching-to-failover.md) | HLS uniquement |
| ptmulticall | Si cette option est activée, une demande d’annonce distincte est effectuée pour chaque valeur trouvée dans une ressource VOD.  Par défaut, l’Ad Insertion Primetime tente de collecter toutes les informations disponibles et de les envoyer au serveur d’annonces dans une seule requête. Valeurs possibles : true pour autoriser la désactivation (désactivation par défaut) | HLS/DASH |
| pttagds | Permet l&#39;injection de balises EXT-X-DISCONTINUITY-SEQUENCE dans les en-têtes HLS.Valeurs possibles : true pour autoriser la désactivation (désactivation par défaut) | HLS uniquement |
| pttimeline | Chaîne contenant la chronologie souhaitée pour l’emplacement et le contenu de la publicité, qui remplace les coupures publicitaires dans le flux de contenu. [ Voir Format de chronologie VOD ] | HLS/DASH |
| pttoken | Active les modèles de protection des jetons d’autorisation de fragments de contenu/segments pour les CDN Valeurs possibles : akamai, lnw (limelight), ctl (centurylink) (la segmentation par jeton par défaut est désactivée) | HLS/DASH |
| pttrackingmode | Activation des schémas de suivi des publicités : valeurs possibles : simples pour le suivi des publicités côté client pour le suivi des publicités côté serveur simplesstesstesesesesesesesesesesesesesesespour le suivi des publicités client/serveur hybride (par défaut, aucun suivi des publicités n&#39;est effectué) | HLS/DASH |
| pttrackingversion |  |  |
| ptadtimeout (comme dans 20.9.2) |  |  |
| ptparallelstream (comme dans le 20.9.3) |  |  |
