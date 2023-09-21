---
title: À propos des certificats
description: À propos des certificats
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# À propos des certificats {#about-certificates}

Le SDK DRM Adobe Primetime est disponible dans les configurations suivantes :

* SDK de production DRM Primetime
* SDK d’évaluation DRM Primetime
* SDK d’évaluation DRM Primetime

Pour utiliser le SDK DRM Primetime afin de créer un serveur de licences, vous devez obtenir des certificats numériques auprès d’Adobe. Les certificats numériques (également appelés certificats) lient une entité, telle qu’un individu, une organisation ou un système, à une paire de clés publique et privée spécifique. Les certificats numériques peuvent être considérés comme des informations d’identification électroniques qui vérifient l’identité d’un individu, d’un système ou d’une organisation.

Pour offrir une flexibilité maximale et une sécurité renforcée à vos options de déploiement, le SDK DRM Primetime requiert quatre certificats :

* Certificat du serveur de licences

  Le SDK utilise ce certificat pour signer les licences de contenu délivrées aux clients.
* Certificat du package

  Le SDK utilise ce certificat pour générer des métadonnées DRM lors du conditionnement (chiffrement) du contenu.
* Certificat de transport

  Le SDK utilise ce certificat pour sécuriser la communication entre les clients et le serveur de licences.
* Certificat d’autorité de certification de domaine

  Les clients qui souhaitent mettre en oeuvre un serveur de domaine ont besoin du certificat d’autorité de certification du domaine. Contrairement aux autres certificats, le certificat de l’autorité de certification du domaine n’est pas émis par Adobe.

>[!NOTE]
>
>Pour le SDK d’évaluation et le SDK d’évaluation, les certificats du serveur de licences, de Packager et de transport sont combinés en un seul certificat.
