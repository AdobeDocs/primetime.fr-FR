---
seo-title: Délivrance de licences liées au domaine
title: Délivrance de licences liées au domaine
uuid: 175d3b7d-d1df-44ee-85ad-a0db4a1bdb9d
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Délivrance de licences liées au domaine{#issuing-domain-bound-licenses}

Pour délivrer une licence à l’aide d’une stratégie qui requiert l’enregistrement de domaine, la demande du client doit inclure un jeton de domaine valide émis par le serveur de domaine spécifié dans la stratégie. Lorsque le client demande une licence, il inclut automatiquement ses jetons de domaine pour tout serveur de domaine spécifié dans les métadonnées de contenu, s’il s’est enregistré auprès de ces serveurs de domaine. Si la stratégie sélectionnée nécessite l’enregistrement du domaine, le SDK sélectionne automatiquement un jeton de domaine à partir de la demande pour lier la licence ou renvoie une erreur si aucun jeton de domaine approprié n’a été trouvé.

Un jeton de domaine est considéré comme valide s’il n’a pas expiré et s’il a été émis par une autorité de certification de domaine autorisée. Le serveur de licences doit spécifier les autorités de domaine à partir desquelles il acceptera les jetons de domaine en configurant `HandlerConfiguration.setDomainCAs()`. Si aucune autorité de certification de domaine n’est configurée, le serveur de licences ne pourra pas émettre de licences liées à un domaine.

Si les métadonnées comprennent plusieurs stratégies, la logique métier du serveur de licences peut sélectionner une stratégie selon que le client a présenté un jeton de domaine ou non. Permet `LicenseRequestMessage.getDomainTokens()` de déterminer les domaines avec lesquels le client s’est enregistré.
