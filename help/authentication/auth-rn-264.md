---
title: Notes de mise à jour de l’authentification Adobe Primetime 2.64
description: Notes de mise à jour de l’authentification Adobe Primetime 2.64
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 0%

---

# Notes de mise à jour de l’authentification Adobe Primetime 2.64 {#authn-264-rn}

>[!NOTE]
>
>Le contenu de cette page est fourni à titre d’information uniquement. L’utilisation de cette API nécessite une licence actuelle de Adobe. Aucune utilisation non autorisée n’est autorisée.

Cette page décrit les nouvelles fonctionnalités, les modifications et les problèmes connus de cette version :

## Clients côté serveur et Web {#ss-web-clients}

* [Numéro de build](#build-no-264)
* [Nouvelles fonctionnalités](#new-featres-264)
* [Correctifs](#bug-fixes-264)


### Numéro de build {#build-no-264}

Authentification Adobe Primetime : adobe-pass-**2,64**

Date de publication : **11/08/2022 - 11/10/2022**

### Nouvelles fonctionnalités {#new-featres-264}

* Mises à jour de l’infrastructure, visant à réduire les temps de réponse du serveur, à améliorer les performances globales du système.
* Améliorations du nouveau mécanisme d&#39;identification de plateforme.
* Possibilité de bloquer les réponses d’authentification non sollicitées des MVPD où le paramètre &quot;in_response_to&quot; est absent de l’assertion SAML.

### Correctifs {#bug-fixes-264}

* Correction d’une mise en forme incorrecte de certains jetons TempPass hérités.
* Correction de problèmes mineurs sur le deuxième flux d’authentification de l’écran.
