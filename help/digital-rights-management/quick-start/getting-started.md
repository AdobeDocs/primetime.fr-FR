---
seo-title: Prise en main
title: Prise en main
uuid: 2002cf94-c8a7-4820-a560-6d9f7f33ee97
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# Prise en main {#getting-started}

Ce document décrit les étapes nécessaires à la configuration et au déploiement rapides d’un écosystème DRM Adobe Primetime qui utilise le téléchargement progressif pour distribuer le contenu et le serveur DRM Primetime pour la diffusion en flux continu protégé pour la distribution des licences. Des informations supplémentaires sur chaque étape sont fournies dans les guides suivants :

* *Utilisation du serveur DRM Primetime pour la protection du contenu*
* *Utilisation du serveur DRM Primetime pour la diffusion en continu protégée*

Le serveur DRM Primetime pour la diffusion en flux continu protégée est un serveur à fonctionnalités minimales qui n’inclut pas de code source. Pour un serveur modifiable avec une source Java complète, voir le guide *Utilisation des implémentations de référence DRM de Primetime*. Si vous configurez un serveur de licences de référence, qui remplace l’étape *Configuration et déploiement de Primetime DRM Server pour la diffusion en flux continu protégée (serveur de licences)*.

## Conditions préalables {#prerequisites}

Avant de commencer, effectuez les tâches suivantes :

* Procurez-vous deux ordinateurs Windows ou Linux :

   * Un ordinateur sera le serveur de licences.
   * Un ordinateur sera Content Server.

* Installez les applications suivantes sur les deux ordinateurs :

   * Tomcat 6.0.18
   * Java 1.6

## Obtention de certificats {#obtain-certificates}

Une fois le logiciel SDK livré, l’administrateur de certificats de Société désigné recevra une invitation à terminer le processus d’inscription des certificats DRM de Adobe Primetime. Pour plus d&#39;informations, consultez le *Guide d&#39;inscription des certificats DRM Primetime*.

1. L’administrateur nomme au moins une personne pour agir en tant que demandeur de certificat.
1. Le demandeur de certificat génère une clé privée et une CSR.
1. Le demandeur envoie une demande de certificat.
1. L’administrateur de la Société approuve la demande.
1. L&#39;administrateur de certificat d&#39;Adobe confirme l&#39;envoi.
1. Le demandeur reçoit le certificat, le lie à la clé privée et déploie le certificat. comme décrit dans .

   Pour plus d’informations sur le déploiement du certificat, voir le guide *Déploiement du serveur DRM Adobe Primetime pour la diffusion en flux continu protégée*.
1. Les étapes 3 à 6 doivent être effectuées pour chaque type de certificat.

   Pour la version de production DRM de Primetime, le demandeur doit effectuer des demandes distinctes pour les certificats de serveur de licences, de package et de transport, qui sont valides pendant deux ans.

   Les clients qui utilisent les versions d’évaluation ou d’évaluation de DRM de Primetime n’ont besoin que d’un seul certificat valide pour 1 an / 90 jours, respectivement.