---
title: Émission de licences liées aux domaines
description: Émission de licences liées aux domaines
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%

---

# Émission de licences liées aux domaines{#issuing-domain-bound-licenses}

Pour délivrer une licence à l’aide d’une stratégie nécessitant l’enregistrement de domaine, la demande du client doit inclure un jeton de domaine valide émis par le serveur de domaine spécifié dans la stratégie. Lorsque le client demande une licence, elle inclut automatiquement ses jetons de domaine pour tout serveur de domaine spécifié dans les métadonnées de contenu, s’il s’est enregistré auprès de ces serveurs de domaine. Si la stratégie sélectionnée nécessite l’enregistrement du domaine, le SDK sélectionne automatiquement un jeton de domaine à partir de la demande à laquelle lier la licence ou renvoie une erreur si aucun jeton de domaine approprié n’a été trouvé.

Un jeton de domaine est considéré comme valide s’il n’a pas expiré et s’il a été émis par une autorité de certification de domaine autorisée. Le serveur de licences doit spécifier les autorités du domaine à partir desquelles il acceptera les jetons de domaine en configurant `HandlerConfiguration.setDomainCAs()`. Si aucune autorité de certification de domaine n’est configurée, le serveur de licences ne pourra pas émettre de licences liées à un domaine.

Si les métadonnées contiennent plusieurs stratégies, la logique commerciale du serveur de licences peut sélectionner une stratégie selon que le client a présenté un jeton de domaine ou non. Utilisation `LicenseRequestMessage.getDomainTokens()` pour déterminer les domaines avec lesquels le client s’est enregistré.
