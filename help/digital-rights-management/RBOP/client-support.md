---
description: Cette section décrit les fonctionnalités disponibles avec différentes versions de Flash Player et TVSDK.
title: Prise en charge du client RBOP
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Prise en charge du client RBOP {#rbop-client-support}

Cette section décrit les fonctionnalités disponibles avec différentes versions de Flash Player et TVSDK.

**Message d&#39;erreur**  : les plateformes TVSDK répertoriées ci-dessous envoient une erreur d&#39;exécution DRM lorsque la résolution du contenu en cours de lecture dépasse la résolution autorisée pour la configuration de périphérique définie dans la stratégie DRM :

* Versions de Flash Player 18 à 20
* Android - Versions
* iOS - Versions

>[!NOTE]
>
>* Toutes les plateformes de Flash et mobiles prennent en charge le message d’erreur. Cependant, seuls les clients TVSDK répertoriés ci-dessus traitent les erreurs liées à RBOP.
>* Erreurs client DRM [liées à RBOP](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages) :
   >    * **3371** - Résolution mal formée basée sur les contraintes de protection de sortie dans la licence.
   >    * **3372**  - La résolution du contenu est supérieure à la résolution maximale spécifiée dans la contrainte de protection de sortie. (Cela peut se produire si quelqu’un a tenté d’injecter du contenu destiné à un autre périphérique.)
   >    * **3373**  - La résolution du contenu est supérieure à la résolution spécifiée par la contrainte de protection de sortie actuellement principale. (Cela signifie que nous devrons procéder à une rétrogradation.)

>



**Réduction**  automatique de la mise à l&#39;échelle : la technique utilisée pour réduire la mise à l&#39;échelle varie selon la plate-forme et la version de Flash Player :

* Flash Player version 21 : Prend en charge RBOP avec réduction automatique de l’échelle (changement de débit intelligent)
* Firefox version 38 et ultérieure sous Windows (avec Access CDM) : L’Adobe télécharge automatiquement un flux à débit supérieur vers un flux à débit inférieur (contrairement au téléchargement d’un flux à débit inférieur).

>[!NOTE]
>
>Ces plates-formes réduisent automatiquement la vidéo et affichent le contenu à une résolution inférieure ou égale à celle spécifiée par la stratégie DRM. Avec cette fonctionnalité, le contenu sera toujours lu au client, tant qu’un flux disponible respecte les restrictions de la stratégie DRM.

**Protection**  Output héritée - Les clients utilisant des Flashs Player antérieurs à la version 18 ne peuvent gérer que les restrictions OP héritées. Les clients disposant de la version 18 du Flash Player et des versions ultérieures peuvent gérer les restrictions héritées ou RBOP. Si vous définissez des restrictions RBOP, vous devez également définir des restrictions OP héritées pour les clients plus âgés. Pour les clients qui prennent en charge RBOP, les restrictions RBOP l&#39;emportent sur les restrictions OP héritées.
