---
description: Cette section décrit les fonctionnalités disponibles avec différentes versions de Flash Player et de TVSDK.
title: Assistance clientèle RBOP
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# Assistance clientèle RBOP {#rbop-client-support}

Cette section décrit les fonctionnalités disponibles avec différentes versions de Flash Player et de TVSDK.

**Message d’erreur** - Les plateformes TVSDK répertoriées ci-dessous distribuent une erreur d’exécution DRM lorsque la résolution du contenu en cours de lecture dépasse la résolution autorisée pour la configuration de l’appareil définie dans la stratégie DRM :

* Versions de Flash Player 18 à 20
* Android - Versions
* iOS - Versions

>[!NOTE]
>
>* Toutes les plateformes mobiles et de Flash prennent en charge le message d’erreur, mais seuls les clients TVSDK répertoriés ci-dessus traitent les erreurs liées à la RBOP.
>* Lié à RBOP [Erreurs client DRM](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages):
>    * **3371** - Résolution incorrecte basée sur les contraintes de protection de sortie de la licence.
>    * **3372** - La résolution du contenu est supérieure à la résolution maximale spécifiée dans la contrainte de protection de sortie. (Cela peut se produire si quelqu’un a tenté d’injecter du contenu destiné à un autre appareil.)
>    * **3373** - La résolution du contenu est supérieure à celle spécifiée par la contrainte de protection de sortie actuellement active. (Cela signifie que nous devrons procéder à une rétrogradation.)
>

**Réduction automatique** - La technique utilisée pour réduire la taille varie selon la plateforme et la version de Flash Player :

* Flash Player version 21 : prise en charge de la recomposition automatique avec réduction automatique (changement de débit intelligent)
* Firefox version 38 et ultérieure sous Windows (avec Access CDM) : Adobe télécharge automatiquement un flux à débit supérieur à un flux à débit inférieur (contrairement au téléchargement d’un flux à débit inférieur).

>[!NOTE]
>
>Ces plateformes réduisent automatiquement la vidéo et affichent le contenu à une résolution inférieure ou égale à celle spécifiée par la stratégie DRM. Avec cette fonctionnalité, le contenu sera toujours lu au client, tant qu’un flux disponible respecte les restrictions de la stratégie DRM.

**Protection des sorties héritée** - Les clients qui utilisent des Flashs Player antérieurs à la version 18 ne peuvent gérer que les restrictions d’OP héritées. Les clients disposant de la version 18 et ultérieure de Flash Player peuvent gérer les restrictions héritées ou RBOP. Si vous définissez des restrictions RBOP, vous devez également définir des restrictions OP héritées pour les clients plus âgés. Pour les clients qui prennent en charge RBOP, les restrictions RBOP l’emportent sur les restrictions OP héritées.
