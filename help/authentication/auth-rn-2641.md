---
title: Notes de mise à jour d’Adobe Primetime authentication 2.64.1
description: Notes de mise à jour d’Adobe Primetime authentication 2.64.1
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 0%

---


# Notes de mise à jour d’Adobe Primetime authentication 2.64.1 {#authn-264-rn}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

Cette page décrit les nouvelles fonctionnalités, les modifications et les problèmes connus de cette version :

## Clients côté serveur et Web {#server-side-web-clients-2641}

* [Numéro de build](#build-number-2641)
* [Présentation des versions](#release-overview-2641)

### Numéro de build {#build-number-2641}

Authentification Adobe Primetime : adobe-pass-**2.64.1**
Date de publication : **01/31/2023 - 02/02/2023**

### Présentation des versions {#release-overview-2641}

Cette version ajoute les éléments suivants :

* La possibilité de bloquer les réponses d’authentification non sollicitées des MVPD où le paramètre &quot;in_response_to&quot; est absent de l’assertion SAML.
* Amélioration de la validation du paramètre redirect_url afin de se conformer aux exigences de sécurité.
* Amélioration de la journalisation des informations sur l’appareil pour les demandes d’authentification du deuxième écran, à l’aide des informations fournies par l’appareil initial.
