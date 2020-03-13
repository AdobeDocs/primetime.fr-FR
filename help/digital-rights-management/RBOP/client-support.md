---
description: Cette section décrit les fonctionnalités disponibles avec différentes versions de Flash Player et de TVSDK.
seo-description: Cette section décrit les fonctionnalités disponibles avec différentes versions de Flash Player et de TVSDK.
seo-title: Prise en charge du client RBOP
title: Prise en charge du client RBOP
uuid: d1d0f788-7bc1-488c-807e-be47f83725e9
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Prise en charge du client RBOP {#rbop-client-support}

Cette section décrit les fonctionnalités disponibles avec différentes versions de Flash Player et de TVSDK.

**Error Dispatch** - Les plateformes TVSDK répertoriées ci-dessous distribuent une erreur d’exécution DRM lorsque la résolution du contenu en cours de lecture dépasse la résolution autorisée pour la configuration de périphérique définie dans la stratégie DRM :

* Flash Player versions 18 à 20
* Android - Versions
* iOS - Versions

>[!NOTE]
>
>* Toutes les plateformes Flash et mobiles prennent en charge le message d’erreur, mais seuls les clients TVSDK répertoriés ci-dessus traitent les erreurs RBOP.
>* Erreurs [client](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)DRM liées à RBOP : >
   >    * **3371** - Résolution incorrecte basée sur les contraintes de protection de sortie dans la licence.
   >    * **3372** - La résolution du contenu est supérieure à la résolution maximale spécifiée dans la contrainte de protection de sortie. (Cela peut se produire si un utilisateur tente d’injecter du contenu destiné à un autre périphérique.)
   >    * **3373** - La résolution du contenu est supérieure à la résolution spécifiée par la contrainte active de protection de sortie. (Cela signifie que nous devrons procéder à une rétrogradation.)
>



**Réduction** automatique - La technique utilisée pour réduire la mise à l&#39;échelle varie selon la plate-forme et la version de Flash Player :

* Flash Player Version 21 : Prend en charge RBOP avec réduction automatique de l’échelle (commutation de débit intelligente)
* Firefox version 38 et ultérieure sous Windows (avec Access CDM) : Adobe télécharge automatiquement un flux à débit supérieur vers un flux à débit inférieur (contrairement au téléchargement d’un flux à débit inférieur).

>[!NOTE]
>
>Ces plateformes réduisent automatiquement la vidéo et affichent le contenu à une résolution inférieure ou égale à celle spécifiée par la stratégie DRM. Avec cette fonctionnalité, le contenu sera toujours lu au client, tant qu’il existe un flux disponible qui respecte les restrictions de la stratégie DRM.

**Protection** de sortie héritée : les clients utilisant des lecteurs Flash antérieurs à la version 18 peuvent uniquement gérer les restrictions d’opération héritées. Les clients disposant de Flash Player versions 18 et ultérieures peuvent gérer les restrictions héritées ou RBOP. Si vous définissez des restrictions RBOP, vous devez également définir des restrictions OP héritées pour les clients plus âgés. Pour les clients qui prennent en charge RBOP, les restrictions RBOP l’emportent sur les restrictions OP héritées.
