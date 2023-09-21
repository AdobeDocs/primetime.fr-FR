---
title: Stockage sécurisé des stratégies
description: Stockage sécurisé des stratégies
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# Stockage sécurisé des stratégies{#securely-storing-policies}

Le SDK Adobe Access offre une grande flexibilité pour le développement d’applications à utiliser dans le conditionnement de contenu et la création de stratégies. Lors de la création de ces applications, vous pouvez autoriser certains utilisateurs à créer et modifier des stratégies, et limiter d’autres utilisateurs de sorte qu’ils puissent appliquer uniquement des stratégies existantes au contenu. Si tel est le cas, vous devez mettre en oeuvre les contrôles d’accès nécessaires pour créer des comptes d’utilisateurs avec des privilèges différents pour la création de stratégies et l’application de stratégies au contenu.

Les stratégies ne sont pas signées ou protégées d’une modification tant qu’elles ne sont pas utilisées dans le package. Si les utilisateurs de vos outils de création de package modifient des stratégies, vous devez envisager de les signer afin de vous assurer qu’elles ne peuvent pas être modifiées.

Pour plus d’informations sur la création d’applications à l’aide du SDK, voir la section *Référence de l’API Adobe Access*.
