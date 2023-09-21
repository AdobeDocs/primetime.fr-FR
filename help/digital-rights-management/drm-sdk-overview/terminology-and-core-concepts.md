---
title: Terminologie et concepts de base
description: Terminologie et concepts de base
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Terminologie et concepts de base{#terminology-and-core-concepts}

Les termes et concepts suivants sont utilisés dans ce document :

**Consommation**

La variable *client* est l’utilisateur final qui télécharge ou diffuse du contenu.

**Contenu**

*Contenu* se compose de fichiers audio ou vidéo numériques.

**Clé de chiffrement du contenu**

La variable *Clé de chiffrement du contenu* (CEK) est une clé cryptographique utilisée pour chiffrer le contenu.

**Propriétaires de contenu**

*Propriétaires de contenu* sont les entités commerciales qui détiennent le droit d’auteur sur le contenu. Il peut s&#39;agir de grands studios d&#39;images ou de producteurs indépendants plus petits de films ou d&#39;autres contenus audiovisuels.

**Packages de contenu**

*Packages de contenu* sont des organisations qui compilent du contenu à utiliser avec Adobe Primetime DRM. Les propriétaires de contenu ou les distributeurs peuvent choisir d&#39;assembler leur propre contenu, ou s&#39;ils peuvent faire appel aux services d&#39;un tiers pour regrouper leur contenu et le distribuer électroniquement via Internet.

**Certificat numérique**

*Certificats numériques* (également appelé *certificates*) liez une entité, telle qu’une personne physique, une organisation ou un système, à une paire de clés publique et privée spécifique. Les certificats numériques peuvent être considérés comme des informations d’identification électroniques qui vérifient l’identité d’un individu, d’un système ou d’une organisation.

**Signature numérique**

A *signature numérique* lie l’identité de l’éditeur au contenu qu’il a publié et fournit un mécanisme pour détecter la falsification. Les algorithmes de signature numérique utilisent des fonctions de hachage cryptographique et des algorithmes de chiffrement asymétriques (ou de paire de clés publique/privée). Certaines signatures numériques tirent également parti des certificats numériques et de l’infrastructure à clé publique (PKI) pour lier les clés publiques aux identités des propriétaires ou des distributeurs de contenu.

**Distributeur**

*Distributeurs* (également appelé *distributeurs de contenu* ou* détaillants*) sont des entités commerciales qui garantissent des droits de distribution aux propriétaires de contenu pour publier et diffuser du contenu auprès des consommateurs. Dans certains cas, la même entité est à la fois le propriétaire du contenu et le distributeur de contenu.

**Métadonnées DRM**

Informations que le client (c’est-à-dire Adobe® Flash® Player, Adobe® AIR® runtime et client Primetime) envoie pour identifier le contenu demandé.

**Licence**

Une *licence* est une structure de données qui contient une clé chiffrée utilisée pour déchiffrer le contenu associé à une stratégie. La licence est générée par Primetime DRM lorsque le consommateur demande du contenu et est lié à l’ordinateur du consommateur. En utilisant une stratégie comme référence, la licence définit les droits disponibles pour le consommateur qui télécharge du contenu. Pour visualiser le contenu, le consommateur doit obtenir une licence.

**Acquisition de licences**

*Acquisition de licences* est le processus d’acquisition d’une licence permettant au consommateur de décrypter et d’afficher du contenu protégé selon un ensemble de règles d’utilisation. L’acquisition de licence se produit lorsqu’un client envoie des informations identifiant le contenu demandé (le *Métadonnées DRM*) et le certificat de la machine (identifiant l’ordinateur du consommateur) au serveur de licences (voir ci-dessous).

**Serveur de licences**

Le* serveur de licences *peut être intégré aux systèmes de facturation et d’authentification du distributeur ou du fournisseur de services, et peut contenir une logique commerciale afin de vérifier que le client qui demande du contenu protégé est autorisé à afficher le contenu. Si l’utilisateur est autorisé à accéder au contenu, le serveur de licences émet une licence permettant au client d’exécution de déchiffrer et de lire le contenu en fonction de la stratégie et des droits associés au compte du client.

Vous devez créer et déployer un serveur de licences à l’aide du SDK DRM Primetime.

**Stratégie**

A *policy* est un conteneur pour les règles d’utilisation qui déterminent la manière dont les consommateurs peuvent utiliser du contenu protégé. Les stratégies sont définies indépendamment du contenu protégé. Une stratégie n’impose des droits que lorsqu’elle est liée au contenu par le biais de la licence. Une stratégie répertorie l’ensemble des règles d’utilisation, c’est-à-dire les autorisations ou &quot;droits&quot; que les consommateurs ont sur le contenu qu’ils achètent. Par exemple, les propriétaires de contenu peuvent créer une stratégie qui garantit que le contenu protégé n’est accessible aux consommateurs que pendant une période donnée. Cette stratégie est ensuite appliquée à tout le contenu pour lequel le propriétaire du contenu souhaite appliquer cette restriction.

Les stratégies sont créées à l’aide du SDK DRM Primetime.

**Contenu protégé**

*Contenu protégé* (également appelé *contenu conditionné*) fait référence au contenu vidéo chiffré à l’aide du SDK DRM Primetime ou d’autres outils pris en charge.

**Détaillants**

Voir l’entrée pour *distributeurs* plus haut dans cette section.
