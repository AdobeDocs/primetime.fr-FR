---
title: Mise à jour des stratégies DRM
description: Mise à jour des stratégies DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Mise à jour des stratégies DRM {#updating-drm-policies}

Si les stratégies DRM sont mises à jour après le package du contenu, fournissez les stratégies DRM mises à jour au serveur de licences afin que la version mise à jour puisse être utilisée lors de l’émission d’une licence. Si un serveur de licences a accès à une base de données pour le stockage des stratégies DRM, vous pouvez récupérer la stratégie DRM mise à jour de la base de données et appeler . `LicenseRequestMessage.setSelectedPolicy()` pour fournir la nouvelle version de la stratégie DRM.

Pour les serveurs de licences qui ne reposent pas sur une base de données centrale, le SDK prend en charge les listes de mise à jour de stratégie DRM. Une liste de mise à jour de stratégie DRM est un fichier qui contient une liste de stratégies DRM mises à jour ou révoquées. Lorsqu’une stratégie DRM est mise à jour, générez une nouvelle liste de mise à jour de stratégie DRM et envoyez régulièrement la liste à tous les serveurs de licences. Transmettez la liste au SDK en définissant `HandlerConfiguration.setPolicyUpdateList()`. Si une liste de mise à jour est fournie, le SDK la consulte lorsqu’il analyse les métadonnées de contenu. `ContentInfo.getUpdatedPolicies()` inclut les versions mises à jour des stratégies DRM spécifiées dans les métadonnées.

Voir [Utilisation des stratégies DRM](../../../protecting-content/working-policies-overview/working-with-policies.md) et [Listes de mise à jour des stratégies DRM](../../../protecting-content/working-policies-overview/policy-update-lists/working-with-policy-update-lists.md)
