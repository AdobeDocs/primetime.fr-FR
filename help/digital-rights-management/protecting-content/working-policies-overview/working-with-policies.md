---
title: Présentation de l’utilisation des stratégies DRM
description: Présentation de l’utilisation des stratégies DRM
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# Aperçu {#working-with-drm-policies-overview}

Les fournisseurs de contenu peuvent appliquer des stratégies DRM aux fichiers de médias à l’aide du SDK DRM Primetime. Les administrateurs peuvent ensuite créer, vue des détails et mettre à jour des stratégies DRM à l’aide des API de gestion des stratégies.

Un *`DRM policy`* est un ensemble d&#39;informations qui comprend les paramètres de sécurité, les exigences d&#39;authentification et les droits d&#39;utilisation. La stratégie définit comment les utilisateurs peuvent vue du contenu. Les stratégies DRM, le chiffrement et la signature permettent aux fournisseurs de contenu de contrôler leur contenu quelle que soit la diffusion du contenu.

Une stratégie DRM sert de modèle que le serveur de licences utilise lorsqu’il génère une licence. Un client peut également se référer à la stratégie DRM avant de demander une licence, afin de déterminer si le client doit demander à l&#39;utilisateur de l&#39;authentifier avant d&#39;envoyer une demande de licence au serveur.

Vous pouvez diffuser du contenu protégé à l’aide d’un Flash Media Server d’Adobe ou d’un serveur HTTP. Les utilisateurs peuvent télécharger et lire du contenu protégé dans des lecteurs personnalisés créés avec le SDK DRM Primetime.

Une stratégie DRM spécifie un ou plusieurs droits accordés au client. En règle générale, une stratégie DRM comprend, au minimum, le *`Play Right`*. Vous pouvez également spécifier plusieurs droits de lecture, chacun avec des restrictions différentes. Lorsque le client reçoit une licence avec plusieurs droits de lecture, il utilise la première licence qui satisfait à toutes les restrictions. Par exemple, vous pouvez appliquer différents paramètres de protection de sortie sur différentes plates-formes.

Voir `CreatePolicyWithOutputProtection.java` dans le répertoire Reference Implementation Command Line Tools [!DNL samples] pour obtenir un exemple de code qui illustre cet exemple.

Vous pouvez exécuter les tâches suivantes avec les API de gestion des stratégies DRM Primetime :

* Création et mise à jour de stratégies
* Détails de la stratégie de gestion des droits numériques de vue
* Gérer les listes de mise à jour de stratégie DRM

Pour plus d’informations sur l’API Java, consultez la *Référence API DRM Primetime*.

Pour plus d&#39;informations sur Primetime DRM Policy Manager, consultez le guide *Using the Primetime DRM Reference Implementations*.
