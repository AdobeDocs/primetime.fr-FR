---
description: Adobe Access peut être utilisé avec d’autres solutions tierces de diffusion de contenu en flux continu pour configurer un écosystème complet et sécurisé de distribution de médias à base de gestion des droits numériques.
seo-description: Adobe Access peut être utilisé avec d’autres solutions tierces de diffusion de contenu en flux continu pour configurer un écosystème complet et sécurisé de distribution de médias à base de gestion des droits numériques.
seo-title: Support UltraViolet et et Adobe Access
title: Support UltraViolet et et Adobe Access
uuid: d287680f-02de-4cca-aeea-22b7fd8e67d2
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Support UltraViolet et et Adobe Access {#ultraviolet-media-and-adobe-access}

Adobe Access peut être utilisé avec d’autres solutions tierces de diffusion de contenu en flux continu pour configurer un écosystème complet et sécurisé de distribution de médias à base de gestion des droits numériques.

UltraViolet ( [](https://www.uvvu.com/)) est un système d&#39;authentification des droits numériques et de distribution en mode cloud qui permet aux utilisateurs de contenu de divertissement numérique domestique de diffuser en continu et de télécharger le contenu acheté sur plusieurs plates-formes et appareils. Le contenu UltraViolet sera téléchargé (ou diffusé en continu) dans un format de fichier commun (CFF) à l’aide du chiffrement commun (CENC).

Il est facile de configurer un système UltraViolet avec Adobe Access. Le cas d’utilisation suivant illustre le comportement du flux de contenu :

<!--<a id="fig_cxy_dc2_44"></a>-->

![](assets/AdobeUV_web.png)

1. Le propriétaire du contenu code et met en package le contenu dans CFF. Le contenu assemblé est concédé sous licence à un détaillant pour distribution.
1. Le détaillant télécharge le contenu dans un numérique, tel que CDN. Le contenu est désormais disponible en téléchargement. Notez que certains de ces rôles peuvent être joués par un ou plusieurs .

   L’utilisateur final dispose d’un périphérique qui prend en charge Adobe AIR. En outre, l&#39;utilisateur doit installer une application compatible UltraViolet. L’application comprend le code nécessaire pour analyser le fichier CFF et le présenter pour consommation par le moteur d’exécution. Toutes les opérations cryptographiques sensibles sont gérées dans le runtime sécurisé.
1. L’application peut déclencher une jonction de domaine pour le périphérique, qui interagit avec le coordinateur. Le coordinateur gère un casier des droits, une base de données utilisateur et des domaines. Le gestionnaire de domaine du coordinateur est créé à l’aide du SDK Adobe Access pour implémenter des opérations de jointure/sortie de domaines spécifiques à Adobe Access.
1. L’utilisateur peut alors utiliser l’application pour sélectionner une vidéo qu’il souhaite acquérir auprès du détaillant. Le détaillant fournit généralement un portail Web et traite toute la logique commerciale.
1. Le détaillant interagit ensuite avec le coordinateur pour ajouter un jeton de droits. Le détaillant redirige ensuite la demande vers le pour le téléchargement réel du contenu.
1. Si le périphérique n’a pas encore de licence du contenu, il déclenche une demande de licence à l’aide du CFF. La requête comprend généralement un certificat de domaine, des informations d’identification d’utilisateur et des informations sur l’application. Le utilise un serveur de licence Adobe Access (développé à l’aide du kit SDK Adobe Access) qui respecte les spécifications UltraViolet.
1. La logique d&#39;entreprise UltraViolet du interagit avec le coordinateur au besoin pour récupérer le jeton de droits approprié afin de déterminer si une licence de contenu doit être délivrée.

   La licence de contenu est liée au domaine. L’application cliente peut insérer la licence dans le fichier CFF. Le contenu peut désormais être lu dans l’application, avec l’application de toutes les règles de protection et d’utilisation gérée par le composant Adobe Access au moment de l’exécution.
1. Les autres appareils et applications appartenant au même utilisateur final peuvent être enregistrés auprès du coordinateur. Le contenu peut désormais être chargé sur d’autres périphériques Adobe Access sans nécessiter de transaction externe.

