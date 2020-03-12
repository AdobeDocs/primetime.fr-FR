---
seo-title: Prise en main
title: Prise en main
uuid: 2002cf94-c8a7-4820-a560-6d9f7f33ee97
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Prise en main {#getting-started}

Ce décrit les étapes nécessaires à la configuration et au déploiement rapides d’un écosystème DRM Adobe Primetime qui utilise le téléchargement progressif pour distribuer le contenu, ainsi que le serveur DRM Primetime pour la diffusion en flux continu protégé pour la distribution des licences. Des informations supplémentaires sur chaque étape sont fournies dans les guides suivants :

* *Utilisation du serveur DRM Primetime pour la protection du contenu*
* *Utilisation du serveur DRM Primetime pour la diffusion en continu protégée*

Le serveur DRM Primetime pour la diffusion en flux continu protégée est un serveur à fonctionnalités minimales qui n’inclut pas de code source. Pour un serveur modifiable avec une source Java complète, voir le guide *Utilisation des implémentations* de référence DRM Primetime. Si vous configurez un serveur de licence de référence, qui remplace l’étape *Configuration et déploiement de Primetime DRM Server pour la diffusion en flux continu protégée (serveur de licences)* .

## Conditions préalables {#prerequisites}

Avant de commencer, complétez le  suivant :

* Obtenez deux ordinateurs Windows ou Linux :

   * Un ordinateur sera le serveur de licences.
   * Un ordinateur sera Content Server.

* Installez les applications suivantes sur les deux ordinateurs :

   * Tomcat 6.0.18
   * Java 1.6

## Obtention de certificats {#obtain-certificates}

Une fois le logiciel SDK fourni, l’administrateur de certificats  désigné recevra une invitation à terminer le processus d’enregistrement des certificats DRM d’Adobe Primetime. Pour plus d&#39;informations, consultez le Guide *d&#39;inscription des certificats DRM* Primetime.

1. L’administrateur désigne au moins une personne pour agir en tant que demandeur de certificat.
1. Le demandeur de certificat génère une clé privée et une CSR.
1. Le demandeur envoie une demande de certificat.
1. L’administrateur de  approuve la demande.
1. L’administrateur de certificats Adobe confirme l’envoi.
1. Le demandeur reçoit le certificat, le lie à la clé privée et déploie le certificat. comme décrit dans .

   Pour plus d’informations sur le déploiement du certificat, voir le guide *Déploiement d’Adobe Primetime DRM Server for Protected Streaming* .
1. Les étapes 3 à 6 doivent être effectuées pour chaque type de certificat.

   Pour la version de production DRM Primetime, le demandeur doit effectuer des demandes distinctes pour les certificats de serveur de licence, de conditionnement et de transport, qui sont valides pendant deux ans.

   Les clients qui utilisent les versions d’évaluation DRM ou d’évaluation de Primetime n’ont besoin que d’un seul certificat valide pendant 1 an ou 90 jours, respectivement.