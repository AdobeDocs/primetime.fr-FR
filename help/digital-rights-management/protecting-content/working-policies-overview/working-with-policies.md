---
seo-title: Présentation de l’utilisation des stratégies DRM
title: Présentation de l’utilisation des stratégies DRM
uuid: 32423448-013c-4183-bea8-e14b6690abdb
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Présentation {#working-with-drm-policies-overview}

Les fournisseurs de contenu peuvent appliquer des stratégies DRM aux fichiers multimédia à l’aide du SDK DRM Primetime. Les administrateurs peuvent alors créer,  des détails et mettre à jour des stratégies DRM à l’aide des API de gestion des stratégies.

Un *`DRM policy`* est un ensemble d’informations qui comprend des paramètres de sécurité, des exigences d’authentification et des droits d’utilisation. La stratégie définit la manière dont les utilisateurs peuvent  contenu. Les stratégies DRM, le chiffrement et la signature permettent aux fournisseurs de contenu de garder le contrôle sur leur contenu quelle que soit la diffusion du contenu.

Une stratégie DRM sert de modèle que le serveur de licences utilise lorsqu’il génère une licence. Un client peut également se référer à la stratégie DRM avant de demander une licence, afin de déterminer si le client doit demander à l’utilisateur de l’authentifier avant d’envoyer une demande de licence au serveur.

Vous pouvez diffuser du contenu protégé à l’aide d’Adobe Flash Media Server ou d’un serveur HTTP. Les utilisateurs peuvent télécharger et lire du contenu protégé dans des lecteurs personnalisés créés avec le SDK DRM Primetime.

Une stratégie DRM spécifie un ou plusieurs droits accordés au client. En règle générale, une stratégie de gestion des droits numériques inclut, au minimum, la *`Play Right`*. Vous pouvez également spécifier plusieurs droits de lecture, chacun avec des restrictions différentes. Lorsque le client reçoit une licence avec plusieurs droits de lecture, il utilise la première licence qui répond à toutes les restrictions. Par exemple, vous pouvez appliquer différents paramètres de protection de sortie sur différentes plateformes.

Voir `CreatePolicyWithOutputProtection.java` dans le répertoire Reference Implementation Command Line Tools [!DNL samples] pour obtenir un exemple de code qui illustre cet exemple.

Vous pouvez compléter le  de suivant avec les API de gestion des stratégies DRM Primetime :

* Création et mise à jour de stratégies
* Détails de la stratégie DRM 
* Gestion des de mise à jour de stratégie DRM

Pour plus d’informations sur l’API Java, consultez le Guide de référence *de l’API DRM* Primetime.

Pour plus d’informations sur Primetime DRM Policy Manager, consultez le guide *Utilisation des implémentations* de référence DRM de Primetime.
