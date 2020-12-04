---
description: Adobe Access peut être utilisé avec d’autres solutions tierces de diffusion de contenu en flux continu pour configurer un écosystème complet et sécurisé de distribution de médias à base de DRM.
seo-description: Adobe Access peut être utilisé avec d’autres solutions tierces de diffusion de contenu en flux continu pour configurer un écosystème complet et sécurisé de distribution de médias à base de DRM.
seo-title: Accès aux médias et aux Adobes UltraViolet
title: Accès aux médias et aux Adobes UltraViolet
uuid: d287680f-02de-4cca-aeea-22b7fd8e67d2
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---


# Accès aux médias et aux Adobes UltraViolet {#ultraviolet-media-and-adobe-access}

Adobe Access peut être utilisé avec d’autres solutions tierces de diffusion de contenu en flux continu pour configurer un écosystème complet et sécurisé de distribution de médias à base de DRM.

UltraViolet ( [](https://www.uvvu.com/)) est un système d&#39;authentification des droits numériques et de distribution en mode cloud qui permet aux utilisateurs de contenus de divertissement numérique domestique de diffuser en continu et de télécharger du contenu acheté sur plusieurs plates-formes et appareils. Le contenu UltraViolet sera téléchargé (ou diffusé en continu) dans un format de fichier commun (CFF) à l&#39;aide de Common Encryption (CENC).

Il est facile de configurer un système UltraViolet avec Adobe Access. La casse d’utilisation suivante illustre le comportement de flux de contenu :

<!--<a id="fig_cxy_dc2_44"></a>-->

![](assets/AdobeUV_web.png)

1. Le propriétaire du contenu code et regroupe le contenu dans CFF. Le contenu assemblé est concédé sous licence à un détaillant pour distribution.
1. Le détaillant télécharge le contenu vers un prestataire numérique, tel que CDN. Le contenu est désormais disponible en téléchargement. Notez que certains de ces rôles peuvent être joués par une ou plusieurs sociétés.

   L’utilisateur final dispose d’un périphérique qui prend en charge l’Adobe AIR. En outre, l&#39;utilisateur doit installer une application compatible UltraViolet. L&#39;application comprend le code nécessaire pour analyser le fichier CFF et le présenter pour consommation au moment de l&#39;exécution. Toutes les opérations cryptographiques sensibles sont gérées dans le runtime sécurisé.
1. L’application peut déclencher une jointure de domaine pour le périphérique, qui interagit avec le coordinateur. Le coordinateur gère un casier des droits, une base de données utilisateur et des domaines. Le gestionnaire de domaine du coordinateur est créé à l&#39;aide du SDK d&#39;accès aux Adobes pour mettre en oeuvre des opérations de jointure/sortie de domaine spécifiques à Adobe Access.
1. L’utilisateur peut alors utiliser l’application pour sélectionner la vidéo qu’il souhaite acquérir auprès du détaillant. Le détaillant fournit généralement un portail Web et traite toute la logique commerciale.
1. Le détaillant interagit ensuite avec le coordinateur pour ajouter un jeton de droits. Le détaillant redirige ensuite la demande vers le prestataire pour le téléchargement de contenu réel.
1. Si le périphérique ne dispose pas encore d’une licence du contenu, il déclenche une demande de licence à l’aide du CFF. La demande comprend généralement un certificat de domaine, des informations d’identification d’utilisateur et des informations sur l’application. Le prestataire exploite un serveur de licence d&#39;accès à l&#39;Adobe (développé à l&#39;aide du Adobe Access SDK) qui suit les spécifications UltraViolet.
1. La logique commerciale UltraViolet du prestataire interagit avec le coordinateur si nécessaire pour récupérer le jeton de droits approprié afin de déterminer si une licence de contenu doit être délivrée.

   La licence de contenu est liée au domaine. L’application cliente peut insérer la licence dans le fichier CFF. Il est désormais possible de lire le contenu dans l’application, avec l’application de toutes les règles de protection et d’utilisation gérée par le composant Accès à l’Adobe au moment de l’exécution.
1. D&#39;autres appareils et applications appartenant au même utilisateur final peuvent être enregistrés auprès du coordinateur. Le contenu peut désormais être chargé sur d&#39;autres périphériques d&#39;accès à l&#39;Adobe sans nécessiter de transaction externe.

