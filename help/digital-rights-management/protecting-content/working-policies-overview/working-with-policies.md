---
seo-title: Présentation de l’utilisation des stratégies DRM
title: Présentation de l’utilisation des stratégies DRM
uuid: 32423448-013c-4183-bea8-e14b6690abdb
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Présentation {#working-with-drm-policies-overview}

Les fournisseurs de contenu peuvent appliquer des stratégies DRM aux fichiers de médias à l’aide du SDK DRM Primetime. Les administrateurs peuvent ensuite créer, vue des détails et mettre à jour des stratégies DRM à l’aide des API de gestion des stratégies.

Un *`DRM policy`* est un ensemble d’informations qui comprend des paramètres de sécurité, des exigences d’authentification et des droits d’utilisation. La stratégie définit comment les utilisateurs peuvent vue du contenu. Les stratégies DRM, le chiffrement et la signature permettent aux fournisseurs de contenu de contrôler leur contenu quelle que soit la diffusion du contenu.

Une stratégie DRM sert de modèle que le serveur de licences utilise lorsqu’il génère une licence. Un client peut également se référer à la stratégie DRM avant de demander une licence, afin de déterminer si le client doit demander à l&#39;utilisateur de l&#39;authentifier avant d&#39;envoyer une demande de licence au serveur.

Vous pouvez diffuser du contenu protégé à l’aide d’Adobe Flash Media Server ou d’un serveur HTTP. Les utilisateurs peuvent télécharger et lire du contenu protégé dans des lecteurs personnalisés créés avec le SDK DRM Primetime.

Une stratégie DRM spécifie un ou plusieurs droits accordés au client. En règle générale, une politique de gestion des droits numériques comprend, au minimum, la *`Play Right`* politique de gestion des droits numériques. Vous pouvez également spécifier plusieurs droits de lecture, chacun avec des restrictions différentes. Lorsque le client reçoit une licence avec plusieurs droits de lecture, il utilise la première licence qui satisfait à toutes les restrictions. Par exemple, vous pouvez appliquer différents paramètres de protection de sortie sur différentes plates-formes.

Voir `CreatePolicyWithOutputProtection.java` [!DNL samples] dans le répertoire Reference Implementation Command Line Tools (Outils de ligne de commande de mise en oeuvre de référence) pour consulter un exemple de code qui illustre cet exemple.

Vous pouvez exécuter les tâches suivantes avec les API de gestion des stratégies DRM Primetime :

* Création et mise à jour de stratégies
* Détails de la stratégie de gestion des droits numériques de Vue
* Gérer les listes de mise à jour de stratégie DRM

Pour plus d’informations sur l’API Java, voir le Guide de référence *de l’API DRM* Primetime.

Consultez le guide *Utilisation des implémentations* de référence DRM de Primetime pour en savoir plus sur le Gestionnaire de stratégies DRM de Primetime.
