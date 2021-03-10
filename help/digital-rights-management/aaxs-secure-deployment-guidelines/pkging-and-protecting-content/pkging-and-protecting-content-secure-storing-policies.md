---
title: Stockage sécurisé des stratégies
description: Stockage sécurisé des stratégies
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---


# Stockage sécurisé des stratégies{#securely-storing-policies}

Adobe Access SDK offre une grande flexibilité dans le développement d&#39;applications destinées à être utilisées dans l&#39;emballage de contenu et la création de stratégies. Lors de la création de ces applications, vous pouvez autoriser certains utilisateurs à créer et modifier des stratégies et limiter d’autres utilisateurs de sorte qu’ils puissent appliquer uniquement des stratégies existantes au contenu. Si tel est le cas, vous devez implémenter les contrôles d&#39;accès nécessaires pour créer des comptes d’utilisateurs avec des privilèges différents pour la création de stratégies et l’application de stratégies au contenu.

Les stratégies ne sont pas signées ou protégées contre toute modification tant qu&#39;elles ne sont pas utilisées dans l&#39;emballage. Si les utilisateurs de vos outils de création de package modifient des stratégies, vous devez envisager de les signer pour vous assurer qu’elles ne peuvent pas être modifiées.

Pour plus d&#39;informations sur la création d&#39;applications à l&#39;aide du SDK, consultez la *Référence de l&#39;API d&#39;accès aux Adobes*.
