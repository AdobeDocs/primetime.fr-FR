---
title: Présentation
description: Présentation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# Présentation{#overview}

La mise en oeuvre de référence comprend une option de mode de démonstration qui explique comment mettre en oeuvre différents modèles d’utilisation pour un segment de contenu empaqueté. Le mode de démonstration présente la logique métier pour ces modèles d’utilisation :

* **Téléchargement à soi (DTO)** - Les utilisateurs peuvent télécharger le contenu en ligne ou hors ligne et se voient attribuer une licence permanente pour le contenu.
* **Location/Video-On-Demand (VOD)** - Le contenu disponible est fourni avec des restrictions temporelles. Par exemple, les utilisateurs peuvent lire du contenu pendant une période de 30 jours. Une fois la lecture commencée, l’utilisateur a jusqu’à 48 heures pour terminer la lecture du contenu. Le contenu doit être affiché dans 30 jours.
* **Abonnement (à volonté)** - Certains services proposent des abonnements payants qui donnent aux utilisateurs un accès illimité à une grande bibliothèque de contenu tant qu&#39;ils continuent à payer des frais mensuels. Le serveur de licences émet une licence unique pour chaque segment de contenu et émet également une licence racine qui expire à la fin de la période d’abonnement. Chaque mois, lorsque les utilisateurs renouvellent leur abonnement, la licence root doit également être renouvelée.

  >[!NOTE]
  >
  >Pour les modèles d’utilisation précédents, après l’acquisition d’une licence, les utilisateurs doivent saisir leurs informations d’identification afin que le serveur puisse vérifier que les utilisateurs disposent d’un compte de location.

* **Publicité financée** - Le contenu est monétisé en incluant la publicité dans l’expérience. Avec ce modèle, le contenu peut être distribué et ne nécessite pas d’authentification de l’utilisateur.

En mode de démonstration du modèle d’utilisation, la logique commerciale sur le serveur contrôle les attributs des licences générées. Au moment du conditionnement, votre stratégie DRM doit uniquement indiquer si l’authentification est requise ou non.

Pour activer les quatre modèles d’utilisation, vous devez uniquement inclure deux stratégies DRM :

* Une stratégie DRM permettant un accès anonyme au modèle financé par l’annonce
* Une stratégie DRM nécessitant une authentification du nom d’utilisateur/mot de passe pour les trois autres modèles d’utilisation.

Lorsqu’un utilisateur demande une licence, une application cliente peut déterminer s’il faut demander à l’utilisateur l’authentification en fonction des informations d’authentification figurant dans les stratégies DRM.
