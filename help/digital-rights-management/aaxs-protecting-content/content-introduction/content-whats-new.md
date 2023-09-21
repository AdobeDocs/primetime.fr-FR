---
description: 'Adobe® Access™ est une solution avancée de gestion des droits numériques et de protection du contenu pour les contenus audiovisuels de grande valeur. Grâce aux outils que vous créez à l’aide des API Java, vous pouvez créer des stratégies, appliquer des stratégies aux fichiers contenant du contenu audio et vidéo et chiffrer ces fichiers. Les étapes générales pour effectuer ces tâches sont les suivantes : '
title: Présentation
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# Présentation {#overview}

Adobe® Access™ est une solution avancée de gestion des droits numériques et de protection du contenu pour les contenus audiovisuels de grande valeur. Grâce aux outils que vous créez à l’aide des API Java, vous pouvez créer des stratégies, appliquer des stratégies aux fichiers contenant du contenu audio et vidéo et chiffrer ces fichiers. Les étapes générales pour effectuer ces tâches sont les suivantes :

1. Utilisez les API Java pour définir les propriétés de la stratégie et les paramètres de chiffrement.
1. Créez une stratégie décrivant les rôles d’utilisation du contenu. (Voir [Utilisation de stratégies](../../aaxs-protecting-content/content-working-with-policies/content-working-with-policies-overview.md)).

   Vous pouvez créer un nombre illimité de stratégies. La plupart des utilisateurs créent un petit nombre de stratégies et les appliquent à de nombreux fichiers.

1. Regroupez un fichier multimédia.

   Dans ce contexte, *création d’un package de fichier* signifie le chiffrer et lui appliquer une stratégie. (Voir [Package de fichiers multimédias](../../aaxs-protecting-content/content-packaging-media-files/content-packaging-media-files-overview.md).)

1. Mettez en oeuvre le serveur de licences pour émettre une licence à l’utilisateur.

Le contenu chiffré est maintenant prêt pour le déploiement et le client peut demander la licence au serveur.

Le SDK fournit une API Java pour accomplir ces tâches. Il comprend des mises en oeuvre de référence du serveur de licences et des outils de ligne de commande reposant sur les API Java. Pour plus d’informations, voir *Utilisation des implémentations de référence d’accès Adobe*.

## Nouveautés d’Adobe Access 5.2 {#section_06220EDE36B54DCB9CA7963B76DA8167}

* **CEK externe**: possibilité d’intégrer un système de gestion de clés de contenu (CKMS) aux workflows de traitement de licences et de package de contenu DRM, au lieu de chiffrer le CEK et de le regrouper dans les métadonnées du contenu. Voir [Présentation du CEK externe Adobe Access DRM](../../aaxs-drm-xkey-mgmt/aaxs-drm-using-external-cek-overview.md).

* **Retour sous licence (bon)**: possibilité pour un client de renvoyer (ou de supprimer) une licence émise au client.
* **Serveur de clés Xbox**: possibilité de protéger le contenu envoyé sur Xbox et Xbox 360. (Un client Adobe Primetime est requis.)

## Règles d’utilisation personnalisées {#custom-usage-rules}

Indique des règles d’utilisation personnalisées. Les données personnalisées peuvent être incluses dans les licences émises par le serveur de licences. L’interprétation/le traitement de ces données dépend entièrement de la mise en oeuvre de l’application cliente et du serveur de licences.

Exemple de cas d’utilisation : permet l’extensibilité des règles d’utilisation en permettant la transmission sécurisée d’autres règles commerciales dans le cadre de la stratégie et/ou de la licence de contenu. Pour des raisons de sécurité, dans la mesure où ces règles d’utilisation sont appliquées dans le code d’application client personnalisé, cette option doit être utilisée conjointement avec l’application AIR ou les options de liste autorisée du SWF de Flash Player. Pour plus d’informations, voir [Restrictions d’exécution et d’application](../../aaxs-protecting-content/content-introduction/content-usage-rules/content-runtime-application-restrictions/content-allowlist-air.md).
