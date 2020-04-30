---
seo-title: Délivrance de licences liées à un domaine
title: Délivrance de licences liées à un domaine
uuid: 706650b7-6044-4c01-9f5a-90779127c9e1
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Délivrance de licences liées à un domaine{#issuing-domain-bound-licenses}

Pour délivrer une licence à l’aide d’une stratégie DRM qui requiert l’enregistrement du domaine, la demande du client doit inclure un jeton de domaine valide émis par le serveur de domaine spécifié dans la stratégie. Lorsque le client demande une licence, il inclut automatiquement ses jetons de domaine pour tout serveur de domaine spécifié dans les métadonnées de contenu, à condition qu’il ait été enregistré auprès de ces serveurs de domaine. Si la stratégie DRM sélectionnée requiert l’enregistrement du domaine, le SDK sélectionne automatiquement un jeton de domaine à partir de la demande pour lier la licence ou renvoie une erreur si aucun jeton de domaine approprié n’a été trouvé.

Un jeton de domaine est considéré comme valide s’il n’a pas expiré et s’il a été émis par une autorité de certification de domaine autorisée. Le serveur de licences doit spécifier les autorités de domaine à partir desquelles il accepte les jetons de domaine en configurant `HandlerConfiguration.setDomainCAs()`. Si aucune autorité de certification de domaine n’est configurée, le serveur de licences ne pourra pas émettre de licences liées à un domaine.

Si les métadonnées comprennent plusieurs stratégies DRM, la logique métier du serveur de licences peut sélectionner une stratégie DRM basée sur la présentation ou non d’un jeton de domaine par le client. Vous pouvez utiliser `LicenseRequestMessage.getDomainTokens()` pour déterminer les domaines avec lesquels le client s’est enregistré.
