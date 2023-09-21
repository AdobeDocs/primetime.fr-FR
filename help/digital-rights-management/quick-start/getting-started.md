---
title: Prise en main
description: Prise en main
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Prise en main {#getting-started}

Ce document décrit les étapes de la configuration et du déploiement rapides d’un écosystème DRM Adobe Primetime qui utilise le téléchargement progressif pour distribuer le contenu, ainsi que le serveur DRM Primetime pour la diffusion en continu protégée pour la distribution de licences. Des informations supplémentaires sur chaque étape sont fournies dans les guides suivants :

* *Utilisation du serveur DRM Primetime pour protéger le contenu*
* *Utilisation du serveur DRM Primetime pour la diffusion en continu protégée*

Le serveur DRM Primetime pour la diffusion protégée est un serveur à fonctionnalités minimales qui n’inclut pas de code source. Pour un serveur modifiable avec une source Java complète, voir *Utilisation des implémentations de référence DRM Primetime* guide. Si vous configurez un serveur de licence de référence, qui remplace le *Configuration et déploiement du serveur DRM Primetime pour la diffusion en continu protégée (serveur de licences)* étape .

## Conditions préalables {#prerequisites}

Avant de commencer, effectuez les tâches suivantes :

* Procurez-vous deux ordinateurs Windows ou Linux :

   * Un ordinateur sera le serveur de licences.
   * Un ordinateur sera le serveur de contenu.

* Installez les applications suivantes sur les deux ordinateurs :

   * Tomcat 6.0.18
   * Java 1.6

## Obtention de certificats {#obtain-certificates}

Une fois le logiciel SDK livré, l’administrateur de certificat de la société désigné recevra une invitation à terminer le processus d’enregistrement du certificat DRM Adobe Primetime. Pour plus d’informations, voir *Guide d’inscription de certificat DRM Primetime*.

1. L’administrateur nomme au moins une personne pour agir en tant que demandeur de certificat.
1. Le demandeur de certificat génère une clé privée et une demande de signature de certificat.
1. Le demandeur envoie une demande de certificat.
1. L’administrateur de la société approuve la demande.
1. L’administrateur de certificat de l’Adobe confirme l’envoi.
1. Le demandeur reçoit le certificat, le lie à la clé privée et déploie le certificat. comme décrit dans .

   Pour plus d’informations sur le déploiement du certificat, voir *Déploiement du serveur DRM Adobe Primetime pour la diffusion en continu protégée* guide.
1. Les étapes 3 à 6 doivent être effectuées pour chaque type de certificat.

   Pour la version de production DRM Primetime, le demandeur doit effectuer des demandes distinctes pour les certificats du serveur de licences, de package et de transport, qui sont valides pendant deux ans.

   Les clients qui utilisent les versions d’évaluation ou d’évaluation de DRM Primetime n’ont besoin que d’un certificat valide pendant 1 an ou 90 jours, respectivement.
