---
description: Adobe Access peut être utilisé avec d’autres solutions tierces de diffusion de contenu en continu pour configurer un écosystème complet et sécurisé de distribution de médias DRM.
title: Média UltraViolet et accès Adobe
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Média UltraViolet et accès Adobe {#ultraviolet-media-and-adobe-access}

Adobe Access peut être utilisé avec d’autres solutions tierces de diffusion de contenu en continu pour configurer un écosystème complet et sécurisé de distribution de médias DRM.

UltraViolet est un système d’authentification des droits numériques et de distribution dans le cloud qui permet aux consommateurs de contenu de divertissement numérique domestique de diffuser et de télécharger du contenu acheté sur plusieurs plateformes et appareils. Le contenu UltraViolet sera téléchargé (ou diffusé en continu) dans un format de fichier commun (CFF) à l’aide d’un chiffrement commun (CENC).

Il est facile de configurer un système UltraViolet avec un accès Adobe. Le cas d’utilisation suivant illustre le comportement du flux de contenu :

<!--<a id="fig_cxy_dc2_44"></a>-->

![](assets/AdobeUV_web.png)

1. Le propriétaire du contenu code et regroupe le contenu dans CFF. Le contenu conditionné est mis sous licence pour distribution à un détaillant.
1. Le détaillant télécharge le contenu vers un fournisseur de services numériques, comme CDN. Le contenu est maintenant disponible en téléchargement. Notez que certains de ces rôles peuvent être joués par une ou plusieurs entreprises.

   L’utilisateur final dispose d’un appareil qui prend en charge Adobe AIR. En outre, l’utilisateur doit installer une application compatible UltraViolet. L’application comprend le code nécessaire pour analyser le CFF et le présenter pour consommation par le runtime. Toutes les opérations cryptographiques sensibles sont gérées dans le runtime sécurisé.
1. L’application peut déclencher une jointure de domaine pour l’appareil, qui interagit avec le coordinateur. Le coordinateur gère un casier des droits, une base de données utilisateur et des domaines. Le gestionnaire de domaine du coordinateur est créé à l’aide du SDK Adobe Access pour mettre en oeuvre des opérations de sortie/jointure de domaine spécifiques à un accès par Adobe.
1. L’utilisateur peut ensuite utiliser l’application pour sélectionner une vidéo qu’il souhaite acquérir auprès du détaillant. Le détaillant fournit généralement un portail web et gère toute la logique commerciale.
1. Le détaillant interagit ensuite avec le coordinateur pour ajouter un jeton de droits. Le détaillant redirige ensuite la demande vers le fournisseur de services pour le téléchargement réel de contenu.
1. Si le périphérique ne dispose pas encore d’une licence pour le contenu, il déclenche une demande de licence à l’aide du CFF. La requête inclut généralement un certificat de domaine, des informations d’identification de l’utilisateur et des informations sur l’application. Le fournisseur de services gère un serveur de licences d’accès Adobe (développé à l’aide du SDK Adobe Access) conforme aux spécifications UltraViolet.
1. La logique commerciale UltraViolet du fournisseur de services interagit avec le coordinateur si nécessaire pour récupérer le jeton de droits approprié afin de déterminer si une licence de contenu doit être émise.

   La licence de contenu est liée au domaine. L’application cliente peut insérer la licence dans le fichier CFF. Le contenu peut désormais être lu dans l’application, avec l’application de toutes les règles de protection et d’utilisation gérée par le composant Accès à l’Adobe dans le composant d’exécution.
1. D’autres appareils et applications appartenant au même utilisateur final peuvent être enregistrés auprès du coordinateur. Le contenu peut désormais être chargé dans d’autres appareils Adobe Access sans nécessiter de transaction externe.
