---
title: Emission de licences liées à un domaine
description: Emission de licences liées à un domaine
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Emission de licences liées à un domaine{#issuing-domain-bound-licenses}

Pour émettre une licence à l’aide d’une stratégie DRM qui nécessite l’enregistrement du domaine, la demande du client doit inclure un jeton de domaine valide émis par le serveur de domaine spécifié dans la stratégie. Lorsque le client demande une licence, il inclut automatiquement ses jetons de domaine pour tout serveur de domaine spécifié dans les métadonnées de contenu, à condition qu’il ait été enregistré auprès de ces serveurs de domaine. Si la stratégie DRM sélectionnée nécessite l’enregistrement du domaine, le SDK sélectionne automatiquement un jeton de domaine à partir de la demande pour lier la licence ou renvoie une erreur si aucun jeton de domaine approprié n’a été trouvé.

Un jeton de domaine est considéré comme valide s’il n’a pas expiré et s’il a été émis par une autorité de certification de domaine autorisée. Le serveur de licences doit spécifier les autorités du domaine à partir desquelles il accepte les jetons de domaine en configurant `HandlerConfiguration.setDomainCAs()`. Si aucune autorité de certification de domaine n’est configurée, le serveur de licences ne pourra pas émettre de licences liées à un domaine.

Si les métadonnées incluent plusieurs stratégies DRM, la logique commerciale du serveur de licences peut sélectionner une stratégie DRM basée sur la présentation ou non d’un jeton de domaine par le client. Vous pouvez utiliser `LicenseRequestMessage.getDomainTokens()` pour déterminer les domaines avec lesquels le client s’est enregistré.
