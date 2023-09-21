---
title: Présentation
description: Présentation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Présentation  {#overview}

Grâce à Adobe® Access™, les fournisseurs de contenu peuvent appliquer des stratégies aux fichiers multimédias. Grâce aux API de gestion des stratégies, les administrateurs peuvent créer, afficher les détails et mettre à jour des stratégies.

A *policy* définit la manière dont les utilisateurs peuvent afficher le contenu ; il s’agit d’un ensemble d’informations comprenant les paramètres de sécurité, les exigences d’authentification et les droits d’utilisation. Lorsque des stratégies sont appliquées, le chiffrement et la signature permettent aux fournisseurs de contenu de conserver le contrôle de leur contenu, quelle que soit la diffusion. Les fichiers protégés peuvent être diffusés en utilisant Adobe® Flash® Media Server ou un serveur HTTP. Ils peuvent être téléchargés et lus dans des lecteurs personnalisés créés avec Adobe® AIR®, Adobe® Flash® Player et Adobe® Primetime SDK pour iOS. La stratégie est un modèle que le serveur de licences peut utiliser lorsqu’il génère une licence. Le client peut également se référer à la stratégie avant de demander une licence afin de déterminer s’il doit inviter l’utilisateur à s’authentifier avant d’envoyer une demande de licence au serveur.

Une stratégie spécifie un ou plusieurs droits accordés au client. En règle générale, une stratégie inclut, au minimum, le &quot;droit de lecture&quot;. Il est également possible de spécifier plusieurs droits de lecture, chacun avec des restrictions différentes. Lorsque le client rencontre une licence avec plusieurs droits de lecture, il utilise le premier pour lequel il répond à toutes les restrictions. Par exemple, cette fonctionnalité peut être utilisée pour appliquer différents paramètres de protection de sortie sur différentes plateformes. Pour obtenir un exemple de code illustrant cet exemple, voir `CreatePolicyWithOutputProtection.java` dans le répertoire &quot;Exemples&quot; des outils de ligne de commande de mise en oeuvre de référence.

Vous pouvez accomplir les tâches suivantes à l’aide des API de gestion des stratégies :

* Création et mise à jour de stratégies
* Affichage des détails de la stratégie
* Gestion des listes de mise à jour des stratégies

Pour plus d’informations sur l’API Java discutée dans ce chapitre, voir *Référence de l’API Adobe Access*.

Pour plus d’informations sur l’implémentation de référence de Policy Manager, voir *Utilisation des implémentations de référence d’accès Adobe*.
