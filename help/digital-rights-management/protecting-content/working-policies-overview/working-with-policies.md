---
title: Présentation de l’utilisation des stratégies DRM
description: Présentation de l’utilisation des stratégies DRM
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Présentation {#working-with-drm-policies-overview}

Les fournisseurs de contenu peuvent appliquer des stratégies DRM aux fichiers multimédias à l’aide du SDK DRM Primetime. Les administrateurs peuvent ensuite créer, afficher des détails et mettre à jour des stratégies DRM à l’aide des API de gestion des stratégies.

A *`DRM policy`* est un ensemble d’informations qui comprend les paramètres de sécurité, les exigences d’authentification et les droits d’utilisation. La stratégie définit la manière dont les utilisateurs peuvent afficher le contenu. Les stratégies DRM, le cryptage et la signature permettent aux fournisseurs de contenu de contrôler leur contenu quelle que soit la diffusion du contenu.

Une stratégie DRM sert de modèle que le serveur de licences utilise lorsqu’il génère une licence. Un client peut également se référer à la stratégie DRM avant de demander une licence, afin de déterminer si le client doit demander à l’utilisateur de s’authentifier avant d’envoyer une demande de licence au serveur.

Vous pouvez diffuser du contenu protégé à l’aide d’un Flash Media Server Adobe ou d’un serveur HTTP. Les utilisateurs peuvent télécharger et lire du contenu protégé dans des lecteurs personnalisés créés avec le SDK Primetime DRM.

Une stratégie DRM spécifie un ou plusieurs droits accordés au client. En règle générale, une stratégie DRM comprend, au minimum, les *`Play Right`*. Vous pouvez également spécifier plusieurs droits de lecture, chacun avec des restrictions différentes. Lorsque le client reçoit une licence comportant plusieurs droits de lecture, il utilise la première licence qui répond à toutes les restrictions. Par exemple, vous pouvez appliquer différents paramètres de protection de sortie sur différentes plateformes.

Voir `CreatePolicyWithOutputProtection.java` dans les outils de ligne de commande de mise en oeuvre de référence [!DNL samples] pour un exemple de code qui illustre cet exemple.

Vous pouvez effectuer les tâches suivantes avec les API de gestion des stratégies DRM Primetime :

* Création et mise à jour de stratégies
* Affichage des détails de la stratégie DRM
* Gestion des listes de mise à jour des stratégies DRM

Voir *Référence de l’API DRM Primetime* pour plus d’informations sur l’API Java.

Voir *Utilisation des implémentations de référence DRM Primetime* guide pour plus d’informations sur Primetime DRM Policy Manager.
