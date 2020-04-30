---
description: Cette section décrit les fonctionnalités disponibles avec différentes versions de Flash Player et TVSDK.
seo-description: Cette section décrit les fonctionnalités disponibles avec différentes versions de Flash Player et TVSDK.
seo-title: Prise en charge du client RBOP
title: Prise en charge du client RBOP
uuid: d1d0f788-7bc1-488c-807e-be47f83725e9
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Prise en charge du client RBOP {#rbop-client-support}

Cette section décrit les fonctionnalités disponibles avec différentes versions de Flash Player et TVSDK.

**Message d’erreur** - Les plateformes TVSDK répertoriées ci-dessous envoient une erreur d’exécution DRM lorsque la résolution du contenu en cours de lecture dépasse la résolution autorisée pour la configuration de périphérique définie dans la stratégie DRM :

* Flash Player versions 18 à 20
* Android - Versions
* iOS - Versions

>[!NOTE]
>
>* Toutes les plates-formes Flash et mobiles prennent en charge le message d’erreur, mais seuls les clients TVSDK répertoriés ci-dessus traitent les erreurs liées à RBOP.
>* Erreurs [client](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)DRM liées à la RBOP : >
   >    * **3371** - Résolution incorrecte basée sur les contraintes de protection de sortie dans la licence.
   >    * **3372** - La résolution du contenu est supérieure à la résolution maximale spécifiée dans la contrainte de protection de sortie. (Cela peut se produire si quelqu’un a tenté d’injecter du contenu destiné à un autre périphérique.)
   >    * **3373** - La résolution du contenu est supérieure à la résolution spécifiée par la contrainte de protection de sortie actuellement active. (Cela signifie que nous devrons procéder à une rétrogradation.)
>



**Télémise à l&#39;échelle** automatique - La technique utilisée pour réduire l&#39;échelle varie selon la plate-forme et la version de Flash Player :

* Flash Player Version 21 : Prend en charge RBOP avec réduction automatique de l’échelle (changement de débit intelligent)
* Firefox version 38 et ultérieure sous Windows (avec Access CDM) : Adobe télécharge automatiquement un flux de débit supérieur à un flux inférieur (contrairement au téléchargement d’un flux de niveau inférieur).

>[!NOTE]
>
>Ces plates-formes réduisent automatiquement la vidéo et affichent le contenu à une résolution inférieure ou égale à celle spécifiée par la stratégie DRM. Avec cette fonctionnalité, le contenu sera toujours lu au client, tant qu’un flux disponible respecte les restrictions de la stratégie DRM.

**Protection** Output héritée - Les clients utilisant des lecteurs Flash avant la version 18 ne peuvent gérer que les restrictions OP héritées. Les clients disposant de Flash Player version 18 et ultérieure peuvent gérer les restrictions héritées ou RBOP. Si vous définissez des restrictions RBOP, vous devez également définir des restrictions OP héritées pour les clients plus âgés. Pour les clients qui prennent en charge RBOP, les restrictions RBOP l&#39;emportent sur les restrictions OP héritées.
