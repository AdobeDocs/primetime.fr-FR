---
seo-title: A propos des certificats
title: A propos des certificats
uuid: 0b7818b4-bd6a-4f2e-94c2-565e0d735bf8
translation-type: tm+mt
source-git-commit: b4b50471ab0ba98329862322a61bf73aa9e471d5

---


# A propos des certificats {#about-certificates}

Le SDK DRM d’Adobe Primetime est disponible dans les configurations suivantes :

* SDK de production DRM Primetime
* SDK d’évaluation DRM Primetime
* SDK d’évaluation DRM Primetime

Pour utiliser le SDK DRM Primetime pour créer un serveur de licences, vous devez obtenir des certificats numériques auprès d’Adobe. Les certificats numériques (également appelés certificats) lient une entité, telle qu’une personne, une organisation ou un système, à une paire de clés publique et privée spécifique. Les certificats numériques peuvent être considérés comme des informations d’identification électroniques permettant de vérifier l’identité d’une personne, d’un système ou d’une organisation.

Pour bénéficier d’une flexibilité maximale et d’une sécurité renforcée dans vos options de déploiement, le SDK DRM Primetime requiert quatre certificats :

* Certificat du serveur de licences

   Le SDK utilise ce certificat pour signer les licences de contenu délivrées aux clients.
* Certificat Packager

   Le SDK utilise ce certificat pour générer des métadonnées DRM lors du conditionnement (chiffrement) de contenu.
* Certificat de transport

   Le SDK utilise ce certificat pour sécuriser la communication entre les clients et le serveur de licences.
* Certificat d’autorité de domaine

   Les clients qui souhaitent mettre en oeuvre un serveur de domaine ont besoin du certificat d’autorité de certification de domaine. Contrairement aux autres certificats, le certificat d’autorité de certification de domaine n’est pas émis par Adobe.

>[!NOTE]
>
>Pour le SDK d’évaluation et le SDK d’évaluation, les certificats License Server, Packager et Transport sont combinés en un seul certificat.

