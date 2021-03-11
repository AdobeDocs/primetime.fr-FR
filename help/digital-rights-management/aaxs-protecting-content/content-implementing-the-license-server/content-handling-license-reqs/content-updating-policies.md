---
title: Mise à jour des stratégies
description: Mise à jour des stratégies
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Mise à jour des stratégies {#updating-policies}

Si les stratégies sont mises à jour une fois le contenu compressé, fournissez les stratégies mises à jour au serveur de licences afin que la version mise à jour puisse être utilisée lors de l’émission d’une licence. Si votre serveur de licences a accès à une base de données pour le stockage des stratégies, vous pouvez récupérer la stratégie mise à jour de la base de données et appeler `LicenseRequestMessage.setSelectedPolicy()` pour fournir la nouvelle version de la stratégie.

Pour les serveurs de licences qui ne dépendent pas d’une base de données centrale, le SDK fournit la prise en charge des Listes de mise à jour des stratégies. Une liste de mise à jour de stratégie est un fichier contenant une liste de stratégies mises à jour ou révoquées. Lorsqu’une stratégie est mise à jour, générez une nouvelle Liste de mise à jour de stratégie et poussez périodiquement la liste vers tous les serveurs de licences. Transférez la liste au SDK en définissant `HandlerConfiguration.setPolicyUpdateList()`. Si une liste de mise à jour est fournie, le SDK consulte cette liste lors de l’analyse des métadonnées de contenu. `ContentInfo.getUpdatedPolicies()` contient les versions mises à jour des stratégies spécifiées dans les métadonnées.

Voir [Utilisation des stratégies](../../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md) et [listes de mise à jour des stratégies.](/help/digital-rights-management/protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
