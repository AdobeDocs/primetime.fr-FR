---
description: 'Adobe® Access™ est une solution avancée de gestion des droits numériques et de protection du contenu pour les contenus audiovisuels de grande valeur. Les outils que vous créez à l’aide des API Java vous permettent de créer des stratégies, d’appliquer des stratégies aux fichiers contenant du contenu audio et vidéo et de chiffrer ces fichiers. Les étapes de haut niveau pour exécuter ces tâches sont les suivantes : '
seo-description: 'Adobe® Access™ est une solution avancée de gestion des droits numériques et de protection du contenu pour les contenus audiovisuels de grande valeur. Les outils que vous créez à l’aide des API Java vous permettent de créer des stratégies, d’appliquer des stratégies aux fichiers contenant du contenu audio et vidéo et de chiffrer ces fichiers. Les étapes de haut niveau pour exécuter ces tâches sont les suivantes : '
seo-title: Présentation
title: Présentation
uuid: 874c175b-8207-49fa-aad4-204ccbee9c2c
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# Aperçu {#overview}

Adobe® Access™ est une solution avancée de gestion des droits numériques et de protection du contenu pour les contenus audiovisuels de grande valeur. Les outils que vous créez à l’aide des API Java vous permettent de créer des stratégies, d’appliquer des stratégies aux fichiers contenant du contenu audio et vidéo et de chiffrer ces fichiers. Les étapes de haut niveau pour exécuter ces tâches sont les suivantes :

1. Utilisez les API Java pour définir les propriétés de la stratégie et les paramètres de chiffrement.
1. Créez une stratégie décrivant les rôles d’utilisation du contenu. (Voir [Utilisation de stratégies](../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md)).

   Vous pouvez créer autant de stratégies que vous le souhaitez. La plupart des utilisateurs créent un petit nombre de stratégies et les appliquent à de nombreux fichiers.

1. Assemblage d’un fichier multimédia.

   Dans ce contexte, *empaqueter un fichier* signifie le chiffrer et lui appliquer une stratégie. (Voir [Création de packages de fichiers multimédias](../../aaxs-protecting-content/content-packaging-media-files/content-packaging-media-files-overview.md).)

1. Mettez en oeuvre le serveur de licences pour délivrer une licence à l’utilisateur.

Le contenu chiffré est maintenant prêt pour le déploiement et le client peut demander la licence au serveur.

Le SDK fournit une API Java pour accomplir ces tâches et inclut des implémentations de référence du serveur de licences et des outils de ligne de commande basés sur les API Java. Pour plus d&#39;informations, voir *Utilisation des implémentations de référence d&#39;accès à l&#39;Adobe*.

## Nouveautés de Adobe Access 5.2 {#section_06220EDE36B54DCB9CA7963B76DA8167}

* **CEK** externe : Possibilité d’intégrer un système de gestion de clés de contenu (CKMS) aux workflows de diffusion de licences DRM et d’empaquetage de contenu, plutôt que de chiffrer le CEK et de le regrouper dans les métadonnées du contenu. Voir [Présentation du CEK externe DRM d&#39;accès aux Adobes](../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md).

* **Licence (bon) Retour** : La possibilité pour un client de renvoyer (ou de supprimer) une licence délivrée au client.
* **Serveur** clé Xbox : Possibilité de protéger le contenu envoyé à la Xbox et à la Xbox 360. (Un client Adobe Primetime est requis.)

## Règles d’utilisation personnalisée {#custom-usage-rules}

Indique des règles d’utilisation personnalisées. Les données personnalisées peuvent être incluses dans les licences délivrées par le serveur de licences. L’interprétation/le traitement de ces données dépend entièrement de la mise en oeuvre de l’application cliente et du serveur de licences.

Exemple de cas d’utilisation : Permet l’extensibilité des règles d’utilisation en permettant la transmission sécurisée d’autres règles métier dans le cadre de la stratégie et/ou de la licence de contenu. Pour des raisons de sécurité, dans la mesure où ces règles d’utilisation sont appliquées dans le code d’application client personnalisé, cette option doit être utilisée conjointement avec l’application AIR ou les options de liste autorisée SWF Flash Player. Pour plus d’informations, voir [Restrictions d’exécution et d’application](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-allowlist-air.md).
