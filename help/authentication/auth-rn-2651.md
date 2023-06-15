---
title: Notes de mise à jour d’Adobe Pass Authentication 2.65.1
description: Notes de mise à jour d’Adobe Pass Authentication 2.65.1
source-git-commit: c8259e3268556c20630fff92aa90b0f7f9c12617
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Notes de mise à jour d’Adobe Pass Authentication 2.65.1 {#authn-2651-rn}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

Cette page décrit les nouvelles fonctionnalités, les modifications et les problèmes connus de cette version :

## Clients côté serveur et Web {#server-side-web-clients-2651}

* [Numéro de build](#build-number-2651)
* [Présentation des versions](#release-overview-2651)

### Numéro de build {#build-number-2651}

Authentification Adobe Pass : adobe-pass-**2.65.1**
Date de publication : **06/20/2023 - 06/22/2023**

### Présentation des versions {#release-overview-2651}

Cette version ajoute les éléments suivants :

À compter de cette version, nous allons introduire une assistance technique pour l’ajout de règles de limitation de débit à toutes nos API, afin de protéger l’écosystème global d’une utilisation incorrecte.

L’objectif initial est de surveiller le comportement des applications afin d’établir les valeurs limites appropriées et aucune limite ne sera appliquée dans le cadre de cette version. Dans les cas où le trafic généré par une application spécifique dépasse certaines limites, nous collaborerons avec chaque client pour valider l’implémentation.

Les règles de limitation de débit seront appliquées plus tard cette année, une fois le trafic généré à partir de toutes les applications du client validées.
