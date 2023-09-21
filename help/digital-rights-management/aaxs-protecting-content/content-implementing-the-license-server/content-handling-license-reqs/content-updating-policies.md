---
title: Mise à jour des stratégies
description: Mise à jour des stratégies
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---

# Mise à jour des stratégies {#updating-policies}

Si les stratégies sont mises à jour après le package du contenu, fournissez les stratégies mises à jour au serveur de licences afin que la version mise à jour puisse être utilisée lors de l’émission d’une licence. Si votre serveur de licences a accès à une base de données pour le stockage des stratégies, vous pouvez récupérer la stratégie mise à jour de la base de données et appeler `LicenseRequestMessage.setSelectedPolicy()` pour fournir la nouvelle version de la stratégie.

Pour les serveurs de licences qui ne reposent pas sur une base de données centrale, le SDK prend en charge les listes de mise à jour de stratégie. Une liste de mises à jour de stratégie est un fichier contenant une liste de stratégies mises à jour ou révoquées. Lorsqu’une stratégie est mise à jour, générez une nouvelle liste de mise à jour de stratégie et envoyez régulièrement la liste à tous les serveurs de licences. Transmettez la liste au SDK en définissant `HandlerConfiguration.setPolicyUpdateList()`. Si une liste de mise à jour est fournie, le SDK consulte cette liste lors de l’analyse des métadonnées de contenu. `ContentInfo.getUpdatedPolicies()` contient les versions mises à jour des stratégies spécifiées dans les métadonnées.

Voir [Utilisation des stratégies](../../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md) et [Listes de mise à jour des stratégies.](/help/digital-rights-management/protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
