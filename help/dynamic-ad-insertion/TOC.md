---
cloud: experience-cloud
product: adobe primetime
audience: end-user
user-guide-title: Aide de l’Ad Insertion dynamique Primetime
user-guide-description: Explains how to monetize content by inserting user-targeted dynamic ads on the server and engage audience with personalized ads.
translation-type: tm+mt
source-git-commit: 7d74e526dbc4c9f623d1ec30e4bc70d9318a89f9
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---


# Aide pour les Ad Insertion dynamiques {#ad-insertion}

+ [Présentation des Ad Insertion dynamiques](home.md)
+ Commencer avec l’Ad Insertion Primetime{#get-started}
   + [Présentation](get-started-ptai.md)
   + [Préparation à l’utilisation de l’Ad Insertion Primetime](setup-ptai.md)
   + [Intégration de votre serveur d’annonces](integrate-ad-server.md)
   + [Intégration de votre CDN](integrate-cdn.md)
   + [Utiliser l’insertion publicitaire dans les flux dynamiques/linéaires](ad-insertion-live-linear-stream.md)
   + [Utiliser l&#39;insertion publicitaire pour VOD](ad-insertion-vod.md)
   + [Configuration du suivi des publicités](set-up-ad-tracking.md)
+ [Notes de mise à jour des Ad Insertion dynamiques](https://docs.adobe.com/content/help/en/primetime/release-notes/ptai/ptai-19x-release-notes.html)
+ [Outil de débogage du serveur Manifest](manifest-server-debugging-tool.md)

<!-- + [Server Side Ad Insertion debugging dashboard](ssai-debugging-dashboard.md)-->
+ API du serveur de manifeste pour l&#39;Ad Insertion {#manifest-server}
   + [Présentation des interactions du serveur de manifeste](msapi-topics/ms-overview.md)
   + Commencer avec Manifest Server {#get-started}
      + [Envoyer une commande au serveur de manifeste](msapi-topics/ms-getting-started/ms-sending-cmd.md)
      + [Paramètres de requête du serveur de manifeste](msapi-topics/ms-getting-started/ms-api-query-params.md)
   + Requêtes d’insertion publicitaire {#ad-insert}
      + [Demandes d’insertion de publicités](msapi-topics/ms-insert-ads/ms-ad-insert.md)
      + [Paramètres de requête facultatifs par client et situation](msapi-topics/ms-insert-ads/ms-api-query-param-situation.md)
      + [Faciliter le passage du lecteur HLS aux flux de basculement/sauvegarde](msapi-topics/ms-insert-ads/hls-switching-to-failover.md)
      + [Flux de débit binaire multiples](msapi-topics/ms-insert-ads/ms-api-mbr-streams.md)
      + [Insertion partielle de coupures publicitaires](msapi-topics/ms-insert-ads/partial-ad-break-insetion.md)
      + [Prise en charge de plusieurs réseaux CDN pour CRS et diffusion](msapi-topics/ms-insert-ads/ms-api-multi-cdns-for-crs.md)
   + Remplacer les calendriers VOD {#replace-vod}
      + [Modifications apportées à VOD](msapi-topics/ms-changes-vod-timeline/ms-replace-vod-timeline.md)
      + [Format de chronologie VOD](msapi-topics/ms-changes-vod-timeline/ms-api-timeline-format.md)
      + [Remplacement d’une chronologie VOD](msapi-topics/ms-changes-vod-timeline/t-ms-replace-vod-timeline.md)
   + Suivi de l’efficacité des publicités {#ad}
      + [Suivi des publicités](msapi-topics/ms-at-effectiveness/ms-at-overview.md)
      + [Activation du suivi des publicités côté client](msapi-topics/ms-at-effectiveness/ms-enable-client-side-ad-tracking.md)
      + [Présentation du suivi côté client non TVSDK](msapi-topics/ms-at-effectiveness/notvsdk-csat-overview.md)
      + [API permettant aux lecteurs d’interagir avec le serveur de manifeste](msapi-topics/ms-at-effectiveness/notvsdk-csat-ms-interface.md)
      + [Directive EXT-X-MARKER](msapi-topics/ms-at-effectiveness/ms-api-playlists.md)
   + [Cookies](msapi-topics/ms-cookies.md)
   + [Prise en charge des légendes WebVTT](msapi-topics/ms-webvtt-captions.md)
   + Liste des formats de fichier {#list}
      + [Formats de fichier](msapi-topics/ms-list-file-formats/ms-api-file-formats.md)
      + [Format JSON pour l’URL de demande de liste de lecture du manifeste de variante](msapi-topics/ms-list-file-formats/ms-json-m3u8.md)
      + [Formats JSON pour le suivi des URL](msapi-topics/ms-list-file-formats/notvsdk-csat-sidecar.md)
      + [Format VMAP pour les URL de suivi](msapi-topics/ms-list-file-formats/notvsdk-csat-vmap.md)
   + [Configuration requise pour le lecteur vidéo](msapi-topics/ms-player-req.md)
+ Service de reconditionnement créatif Primetime {#crs}
   + [Vue d&#39;ensemble des SIR](creative-repackaging-service/crs-overview.md)
   + [Principales utilisations des SIR](creative-repackaging-service/jit-async-hls-conv.md)
   + [Prise en charge de CDN multiple](creative-repackaging-service/multi-cdn-supportt.md)
   + [Workflows détaillés pour la restauration JIT](creative-repackaging-service/jit-repackage.md)
   + [Utilisation de CRS pour injecter des balises de métadonnées minutées ID3](creative-repackaging-service/inject-id3.md)
   + [API de restauration](creative-repackaging-service/api-repackage.md)
