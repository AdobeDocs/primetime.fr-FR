---
seo-title: Terminologie et concepts fondamentaux
title: Terminologie et concepts fondamentaux
uuid: dc269873-7b63-4c18-bada-5338f4da0edd
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Terminologie et concepts fondamentaux{#terminology-and-core-concepts}

Les termes et concepts suivants sont utilisés dans ce :

**Consommateur**

Le *consommateur* est l’utilisateur final qui télécharge ou diffuse du contenu.

**Contenu**

*Le contenu* se compose de fichiers audio ou vidéo numériques.

**Clé de chiffrement du contenu**

La clé *de chiffrement de* contenu (CEK) est une clé cryptographique utilisée pour chiffrer le contenu.

**Propriétaires de contenu**

*Les propriétaires* de contenu sont les entités commerciales qui détiennent le droit d’auteur sur le contenu. Il peut s&#39;agir de studios d&#39;images grand format ou de producteurs indépendants de films ou d&#39;autres contenus audiovisuels plus petits.

**Packager de contenu**

*Les gestionnaires de package* de contenu sont des organisations qui assemblent du contenu pour l’utiliser avec Adobe Primetime DRM. Les propriétaires de contenu ou les distributeurs peuvent choisir d’assembler leur propre contenu, ou s’ils peuvent s’adresser aux services d’un tiers pour assembler leur contenu et le distribuer électroniquement par Internet.

**Certificat numérique**

*Les certificats* numériques (également appelés *certificats*) lient une entité, telle qu’un individu, une organisation ou un système, à une paire de clés publique et privée spécifique. Les certificats numériques peuvent être considérés comme des informations d’identification électroniques qui vérifient l’identité d’une personne, d’un système ou d’une organisation.

**Signature numérique**

Une signature ** numérique lie l’identité de l’éditeur au contenu qu’il a publié et fournit un mécanisme de détection des falsifications. Les algorithmes de signature numérique utilisent des fonctions de hachage cryptographique et des algorithmes de chiffrement asymétrique (ou paire de clés publique/privée). Certaines signatures numériques tirent également parti des certificats numériques et de l’infrastructure à clé publique (PKI) pour lier les clés publiques à l’identité des propriétaires ou des distributeurs de contenu.

**Distributeur**

*Les distributeurs* (également appelés distributeurs *de* contenu ou* détaillants*) sont des entités commerciales qui garantissent aux propriétaires de contenu le droit de publier et de diffuser du contenu auprès des consommateurs. Dans certains cas, la même entité est à la fois propriétaire du contenu et distributeur de contenu.

**Métadonnées DRM**

Informations que le client (c’est-à-dire Adobe® Flash® Player, Adobe® AIR® runtime et Primetime client) envoie pour identifier le contenu demandé.

**Licence**

Une *licence *est une structure de données qui contient une clé chiffrée utilisée pour déchiffrer le contenu associé à une stratégie. La licence est générée par Primetime DRM lorsque le client demande du contenu et est liée à l’ordinateur du client. En utilisant une stratégie comme référence, la licence définit les droits disponibles pour le consommateur qui télécharge du contenu. Pour pouvoir  du contenu, le consommateur doit obtenir une licence.

**Acquisition de licence**

*L’acquisition* de licence est le processus d’acquisition d’une licence permettant au consommateur de déchiffrer et de du contenu protégé selon un ensemble de règles d’utilisation. L’acquisition de licence se produit lorsqu’un client envoie au serveur de licences des informations identifiant le contenu demandé (les métadonnées ** DRM) et le certificat de l’ordinateur (identifiant l’ordinateur du client) (voir ci-dessous).

**Serveur de licences**

Le serveur de licences* peut *être intégré dans les systèmes de facturation et d&#39;authentification du distributeur ou du, et peut contenir une logique métier pour vérifier que le consommateur qui demande du contenu protégé est autorisé à  le contenu. Si l’utilisateur est autorisé à accéder au contenu, le serveur de licences délivre une licence permettant au client d’exécution de déchiffrer et de lire le contenu en fonction de la stratégie et des droits associés au compte du client.

Vous devez créer et déployer un serveur de licences à l’aide du SDK DRM Primetime.

**Politique**

Une *stratégie* est un  pour les règles d’utilisation qui déterminent comment les consommateurs peuvent utiliser le contenu protégé. Les stratégies sont définies indépendamment du contenu protégé. Une stratégie ne fait pas respecter les droits tant qu’elle n’est pas liée au contenu par le biais de la licence. Un de stratégie  l’ensemble des règles d’utilisation, c’est-à-dire les autorisations ou &quot;droits&quot; que les consommateurs ont sur le contenu qu’ils acquièrent. Par exemple, les propriétaires de contenu peuvent créer une stratégie qui garantit que le contenu protégé n’est accessible aux consommateurs que pendant une période donnée. Cette stratégie est ensuite appliquée à tout le contenu pour lequel le propriétaire du contenu souhaite imposer cette restriction.

Les stratégies sont créées à l’aide du SDK DRM Primetime.

**Contenu protégé**

*Le contenu* protégé (également appelé contenu ** compressé) fait référence au contenu vidéo chiffré à l’aide du SDK DRM Primetime ou d’autres outils pris en charge.

**Détaillants**

Voir l&#39;entrée pour les *distributeurs* plus tôt dans cette section.
