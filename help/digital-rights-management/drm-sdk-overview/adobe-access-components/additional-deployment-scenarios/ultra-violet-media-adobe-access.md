---
seo-title: Support UltraViolet et et DRM Adobe Primetime
title: Support UltraViolet et et DRM Adobe Primetime
uuid: 7076c0f9-e092-48e4-9118-8a414bd03c7a
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Support UltraViolet et et DRM Adobe Primetime {#ultraviolet-media-and-adobe-primetime-drm}

Adobe Primetime DRM peut être utilisé avec d’autres solutions tierces de diffusion de contenu en flux continu pour configurer un écosystème complet et sécurisé de distribution de médias à base de DRM.

UltraViolet ( [https://www.myuv.com/](https://www.uvvu.com/)) est un système d’authentification des droits numériques et de distribution en mode cloud qui permet aux utilisateurs de contenus de divertissement numérique domestique de diffuser en continu et de télécharger les contenus achetés sur plusieurs plates-formes et appareils. Le contenu UltraViolet sera téléchargé (ou diffusé en continu) dans un format de fichier commun (CFF) à l’aide du chiffrement commun (CENC).

Il est facile de configurer un système UltraViolet avec Adobe Primetime DRM. Le cas d’utilisation suivant illustre le comportement du flux de contenu :

<!--<a id="fig_cxy_dc2_44"></a>-->

![](assets/AdobeUV_web.png)

1. Le propriétaire du contenu code et met en package le contenu dans CFF. Le contenu assemblé est concédé sous licence à un détaillant pour distribution.
1. Le détaillant télécharge le contenu dans un numérique, tel que CDN. Le contenu est désormais disponible en téléchargement. Notez que certains de ces rôles peuvent être joués par un ou plusieurs .

   L’utilisateur final dispose d’un périphérique qui prend en charge Adobe AIR. En outre, l&#39;utilisateur doit installer une application compatible UltraViolet. L’application comprend le code nécessaire pour analyser le fichier CFF et le présenter pour consommation par le moteur d’exécution. Toutes les opérations cryptographiques sensibles sont gérées dans le runtime sécurisé.
1. L’application peut déclencher une jonction de domaine pour le périphérique, qui interagit avec le coordinateur. Le coordinateur gère un casier des droits, une base de données utilisateur et des domaines. Le gestionnaire de domaine du coordinateur est créé à l’aide du SDK DRM Primetime pour mettre en oeuvre des opérations de jointure/sortie de domaines spécifiques à DRM Primetime.
1. L’utilisateur peut alors utiliser l’application pour sélectionner une vidéo qu’il souhaite acquérir auprès du détaillant. Le détaillant fournit généralement un portail Web et traite toute la logique commerciale.
1. Le détaillant interagit ensuite avec le coordinateur pour ajouter un jeton de droits. Le détaillant redirige ensuite la demande vers le pour le téléchargement réel du contenu.
1. Si le périphérique n’a pas encore de licence du contenu, il déclenche une demande de licence à l’aide du CFF. La requête comprend généralement un certificat de domaine, des informations d’identification d’utilisateur et des informations sur l’application. Le exploite un serveur de licence DRM Primetime (développé à l’aide du SDK DRM Primetime) qui suit les spécifications UltraViolet.
1. La logique d&#39;entreprise UltraViolet du interagit avec le coordinateur au besoin pour récupérer le jeton de droits approprié afin de déterminer si une licence de contenu doit être délivrée.

   La licence de contenu est liée au domaine. L’application cliente peut insérer la licence dans le fichier CFF. Il est désormais possible de lire le contenu dans l’application, avec l’application de toutes les règles de protection et d’utilisation gérée par le composant DRM Primetime au moment de l’exécution.
1. Les autres appareils et applications appartenant au même utilisateur final peuvent être enregistrés auprès du coordinateur. Le contenu peut désormais être chargé dans d’autres périphériques DRM Primetime sans nécessiter aucune transaction externe.