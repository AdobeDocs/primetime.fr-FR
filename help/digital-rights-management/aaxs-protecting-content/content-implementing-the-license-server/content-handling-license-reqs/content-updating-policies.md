---
seo-title: Mise à jour des stratégies
title: Mise à jour des stratégies
uuid: f6686c8b-bedf-4ec5-a14e-f03326519f89
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Mise à jour des stratégies {#updating-policies}

Si les stratégies sont mises à jour une fois le contenu compressé, fournissez les stratégies mises à jour au serveur de licences afin que la version mise à jour puisse être utilisée lors de l’émission d’une licence. Si votre serveur de licences a accès à une base de données pour y stocker des stratégies, vous pouvez récupérer la stratégie mise à jour de la base de données et appeler `LicenseRequestMessage.setSelectedPolicy()` pour fournir la nouvelle version de la stratégie.

Pour les serveurs de licences qui ne dépendent pas d’une base de données centrale, le SDK fournit la prise en charge des Listes de mise à jour des stratégies. Une liste de mise à jour de stratégie est un fichier contenant une liste de stratégies mises à jour ou révoquées. Lorsqu’une stratégie est mise à jour, générez une nouvelle Liste de mise à jour de stratégie et poussez périodiquement la liste vers tous les serveurs de licences. Transmettez la liste au SDK en définissant `HandlerConfiguration.setPolicyUpdateList()`. Si une liste de mise à jour est fournie, le SDK consulte cette liste lors de l’analyse des métadonnées de contenu. `ContentInfo.getUpdatedPolicies()` contient les versions mises à jour des stratégies spécifiées dans les métadonnées.

Voir [Utilisation des listes de mise à jour des stratégies](../../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md) et des [stratégies.](/help/digital-rights-management/protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
