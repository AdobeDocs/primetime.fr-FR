---
seo-title: Mise à jour des stratégies DRM
title: Mise à jour des stratégies DRM
uuid: 6f7a1432-88e4-499b-a008-6c8cf0e9c09b
translation-type: tm+mt
source-git-commit: d5986e9bc8689bf37abdf242a41aea5e768df754
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Mise à jour des stratégies DRM {#updating-drm-policies}

Si les stratégies DRM sont mises à jour une fois le contenu compressé, fournissez les stratégies DRM mises à jour au serveur de licences afin que la version mise à jour puisse être utilisée lors de l’émission d’une licence. Si un serveur de licences a accès à une base de données pour le stockage des stratégies DRM, vous pouvez récupérer la stratégie DRM mise à jour de la base de données et appeler `LicenseRequestMessage.setSelectedPolicy()` pour fournir la nouvelle version de la stratégie DRM.

Pour les serveurs de licences qui ne reposent pas sur une base de données centrale, le SDK fournit la prise en charge des Listes de mise à jour de stratégie DRM. Une liste de mise à jour de stratégie DRM est un fichier qui inclut une liste de stratégies DRM mises à jour ou révoquées. Lorsqu’une stratégie DRM est mise à jour, générez une nouvelle Liste de mise à jour de stratégie DRM et poussez périodiquement la liste sur tous les serveurs de licences. Transférez la liste au SDK en définissant `HandlerConfiguration.setPolicyUpdateList()`. Si une liste de mise à jour est fournie, le SDK consulte cette liste lorsqu’il analyse les métadonnées du contenu. `ContentInfo.getUpdatedPolicies()` inclut les versions mises à jour des stratégies DRM spécifiées dans les métadonnées.

Voir [Utilisation des stratégies DRM](../../../protecting-content/working-policies-overview/working-with-policies.md) et [listes de mise à jour des stratégies DRM](../../../protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md).