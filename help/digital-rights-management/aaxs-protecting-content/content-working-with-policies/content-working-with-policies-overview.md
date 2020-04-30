---
seo-title: Présentation
title: Présentation
uuid: 7363d241-6947-4a9c-80e5-e50be71066b9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation  {#overview}

Avec Adobe® Access™, les fournisseurs de contenu peuvent appliquer des stratégies aux fichiers de support. Grâce aux API de gestion des stratégies, les administrateurs peuvent créer, vue des détails et mettre à jour des stratégies.

Une *stratégie* définit comment les utilisateurs peuvent vue du contenu ; il s&#39;agit d&#39;un ensemble d&#39;informations comprenant les paramètres de sécurité, les exigences d&#39;authentification et les droits d&#39;utilisation. Lorsque des stratégies sont appliquées, le chiffrement et la signature permettent aux fournisseurs de contenu de conserver le contrôle de leur contenu quelle que soit la diffusion de celui-ci. Les fichiers protégés peuvent être diffusés à l’aide d’Adobe® Flash® Media Server ou d’un serveur HTTP. Ils peuvent être téléchargés et lus dans des lecteurs personnalisés créés avec Adobe® AIR®, Adobe® Flash® Player et Adobe® Primetime SDK pour iOS. La stratégie est un modèle que le serveur de licences doit utiliser lorsqu’il génère une licence. Le client peut également consulter la stratégie avant de demander une licence afin de déterminer s’il doit demander à l’utilisateur de s’authentifier avant d’envoyer une demande de licence au serveur.

Une stratégie spécifie un ou plusieurs droits accordés au client. En règle générale, une stratégie comprend, au minimum, le &quot;jeu juste&quot;. Il est également possible de spécifier plusieurs droits de lecture, chacun avec des restrictions différentes. Lorsque le client rencontre une licence avec plusieurs droits de lecture, il utilise la première licence pour laquelle il satisfait à toutes les restrictions. Par exemple, cette fonctionnalité peut être utilisée pour appliquer différents paramètres de protection de sortie sur différentes plates-formes. Pour obtenir un exemple de code illustrant cet exemple, voir `CreatePolicyWithOutputProtection.java` le répertoire &quot;samples&quot; des outils de ligne de commande de mise en oeuvre de référence.

Vous pouvez accomplir les tâches suivantes à l’aide des API de gestion des stratégies :

* Création et mise à jour de stratégies
* Détails de la stratégie de Vue
* Gérer les listes de mise à jour des stratégies

Pour plus d’informations sur l’API Java abordée dans ce chapitre, voir Référence *sur les API* Adobe Access.

Pour plus d’informations sur l’implémentation de référence de Policy Manager, voir *Utilisation des implémentations* de référence d’Adobe Access.
