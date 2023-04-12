---
title: Présentation de Roku SSO
description: À propos de Roku SSO
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 0%

---


# Présentation de Roku SSO {#overview}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

## Introduction {#roku-sso-intro}

Ce document décrit les informations nécessaires pour tirer parti de la fonctionnalité de connexion unique sur les appareils Roku. Adobe Primetime Authentication collabore avec Roku pour améliorer l’expérience utilisateur de connexion et pour faciliter l’authentification unique sur les applications TV Everywhere pour les abonnés TV.

La solution est basée sur l’API REST sans client de l’authentification Adobe Primetime. La plupart des programmeurs n’auront donc pas besoin de mettre à jour leurs applications pour bénéficier de l’authentification unique.

## Activation de Roku SSO {#enable-roku-sso}

La fonction SSO Roku est activée par défaut, sauf si la demande de programmeur ou MVPD pour la fonction SSO est désactivée.

Chaque programmeur peut activer/désactiver l’authentification unique sur la plateforme Roku pour des intégrations spécifiques.

### Que doit faire un programmeur pour que Roku SSO fonctionne ? {#make-roku-sso-work}

Pour les applications des programmeurs implémentant l’API REST sur les appareils clients, la connexion unique Roku fonctionnera sans changement. Roku OS ajoute deux en-têtes HTTP à toute requête aux points de terminaison de l’authentification Adobe Primetime.

Pour les applications des programmeurs mettant en oeuvre une solution Serveur à Serveur pour l’api REST , le programmeur doit contacter l’équipe Roku et demander une configuration où ces deux en-têtes seront envoyés à leur domaine sur tous les flux d’api.

Identifiant d’abonné fourni par Roku à utiliser au lieu de l’identifiant d’appareil transmis par l’application pour garantir une connexion unique entre applications (et entre appareils).

Pour plus d’informations sur le format des en-têtes nécessaires, contactez votre représentant Adobe.

### Problèmes possibles {#possible-issues}

Les programmeurs doivent vérifier que leurs mises en oeuvre actuelles basées sur l’API REST sans client d’Adobe n’entravent pas l’authentification unique de la plateforme de Roku. Voir ci-dessous une liste des problèmes possibles et comment les résoudre.

| Problème | Cause possible | Solutions possibles | |-|-|-| |Aucun en-tête SSO Roku envoyé à l’Adobe|En utilisant HTTP au lieu de HTTPS pour les appels aux domaines d’authentification Adobe Primetime|Utiliser HTTPS| |Le logo MVPD ne s’affiche pas/n’est pas mis à jour pour les jetons SSO|L’interface utilisateur repose sur le stockage local|Les applications doivent mettre à jour l’interface utilisateur (et le stockage local, si nécessaire) après avoir vérifié l’authentification| |Déconnexion déclenchée sans AuthZ|La conception de l’application|L’application doit être mise à jour pour ne jamais se déconnecter en arrière-plan|

## FAQ {#faq}

* **Comment fonctionnera l’authentification unique ?**

   SSO fonctionnera dans toutes les applications de programmeur optimisées par l’authentification Adobe Primetime sur tous les appareils Roku associés au même utilisateur Roku.
Tous les MVPD ne permettront pas l’authentification unique Roku.

* **Y aura-t-il une modification des TTL d’authentification ?**

   Le premier jeton d’authentification valide sera utilisé pour effectuer une authentification unique. Dans ce cas, toutes les autres applications qui seront authentifiées via SSO utiliseront le même TTL jusqu’à son expiration. Ainsi, lorsque vous naviguez d’une application à l’autre, la deuxième application partage la durée de vie de la première application qui s’authentifie.

* **Les autres fonctionnalités d’Adobe fonctionneront-elles comme auparavant ?**

   Toutes les fonctionnalités d’authentification Primetime fonctionneront comme auparavant.

* **Existe-t-il un processus d’opt-in/opt-out du programmeur bénéficiant d’SSO sur la plateforme Roku ?**

   Il s’agit d’un changement de configuration dans le tableau de bord TVE d’Adobe. Chaque programmeur peut activer/désactiver l’authentification unique sur la plateforme Roku pour des intégrations spécifiques.
