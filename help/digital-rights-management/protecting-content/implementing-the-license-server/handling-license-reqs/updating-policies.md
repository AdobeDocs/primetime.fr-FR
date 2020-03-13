---
seo-title: Mise à jour des stratégies DRM
title: Mise à jour des stratégies DRM
uuid: 6f7a1432-88e4-499b-a008-6c8cf0e9c09b
translation-type: tm+mt
source-git-commit: d5986e9bc8689bf37abdf242a41aea5e768df754

---


# Mise à jour des stratégies DRM {#updating-drm-policies}

Si les stratégies DRM sont mises à jour une fois le contenu compressé, fournissez les stratégies DRM mises à jour au serveur de licences afin que la version mise à jour puisse être utilisée lors de l’émission d’une licence. Si un serveur de licences a accès à une base de données pour le stockage des stratégies DRM, vous pouvez récupérer la stratégie DRM mise à jour dans la base de données et appeler `LicenseRequestMessage.setSelectedPolicy()` pour fournir la nouvelle version de la stratégie DRM.

Pour les serveurs de licences qui ne reposent pas sur une base de données centrale, le SDK prend en charge le de mise à jour de stratégie DRM. Un de mise à jour de stratégie DRM est un fichier qui inclut un de stratégies DRM mises à jour ou révoquées. Lorsqu’une stratégie DRM est mise à jour, générez un nouveau de mise à jour de stratégie DRM et poussez régulièrement le vers tous les serveurs de licences. Transmettez le  au SDK en définissant `HandlerConfiguration.setPolicyUpdateList()`. Si un  de mise à jour est fourni, le kit SDK consulte ce  lorsqu’il analyse les métadonnées du contenu. `ContentInfo.getUpdatedPolicies()` inclut les versions mises à jour des stratégies DRM spécifiées dans les métadonnées.

Voir [Utilisation des stratégies](../../../protecting-content/working-policies-overview/working-with-policies.md) DRM et des de mise à jour des stratégies [DRM](../../../protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)