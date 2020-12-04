---
description: 'null'
seo-description: 'null'
seo-title: Présentation
title: Présentation
uuid: 5f82f603-6e2d-4c9d-a49f-7b07f30a29e4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# Présentation{#overview}

L’implémentation des références comprend une option de mode de démonstration qui montre comment implémenter différents modèles d’utilisation pour un segment de contenu assemblé. Le mode de démonstration présente la logique métier pour ces modèles d’utilisation :

* **Téléchargement individuel (DTO)**  : les utilisateurs peuvent télécharger le contenu en ligne ou hors ligne et se voient attribuer une licence permanente pour le contenu.
* **Location/Vidéo-On-Demand (VOD)**  - Le contenu disponible est assorti de restrictions temporelles. Par exemple, les utilisateurs peuvent lire du contenu pendant une période de 30 jours. Une fois la lecture commencée, l’utilisateur dispose de 48 heures au maximum pour finir de regarder le contenu. Le contenu doit être affiché dans 30 jours.
* **Abonnement (à volonté)**  - Certains services offre des abonnements payés qui donnent aux utilisateurs un accès illimité à une grande bibliothèque de contenu tant qu&#39;ils continuent à payer des frais mensuels. Le serveur de licences délivre une licence unique pour chaque segment de contenu et émet également une licence racine qui expire à la fin de la période d’abonnement. Chaque mois, lorsque les utilisateurs renouvellent leur abonnement, la licence racine doit également être renouvelée.

   >[!NOTE]
   >
   >Pour les modèles d’utilisation précédents, après l’acquisition d’une licence, les utilisateurs doivent entrer leurs informations d’identification afin que le serveur puisse vérifier que les utilisateurs disposent d’un compte de location.

* **Publicité financée**  - Le contenu est monétisé en incluant la publicité dans l’expérience. Avec ce modèle, le contenu peut être distribué et ne nécessite pas d’authentification de l’utilisateur.

En mode de démonstration du modèle d’utilisation, la logique métier sur le serveur contrôle les attributs des licences générées. Au moment de l&#39;emballage, votre stratégie DRM doit seulement indiquer si l&#39;authentification est requise ou non.

Pour activer les quatre modèles d’utilisation, il vous suffit d’inclure deux stratégies DRM :

* Une stratégie DRM permettant un accès anonyme au modèle financé par la publicité
* Une stratégie DRM qui requiert l&#39;authentification du nom d&#39;utilisateur/mot de passe pour les trois autres modèles d&#39;utilisation.

Lorsqu’un utilisateur demande une licence, une application cliente peut déterminer si l’utilisateur doit demander une authentification en fonction des informations d’authentification contenues dans les stratégies DRM.
