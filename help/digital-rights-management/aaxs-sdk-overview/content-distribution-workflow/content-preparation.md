---
description: Toute utilisation de l'accès aux Adobes consiste en deux étapes clés à différents points du processus. La préparation du contenu doit être effectuée une fois par ressource, ce qui entraîne la création de contenu protégé. L'acquisition de contenu se fait à plusieurs reprises, une fois pour chaque consommateur qui souhaite surveiller cette ressource protégée.
seo-description: Toute utilisation de l'accès aux Adobes consiste en deux étapes clés à différents points du processus. La préparation du contenu doit être effectuée une fois par ressource, ce qui entraîne la création de contenu protégé. L'acquisition de contenu se fait à plusieurs reprises, une fois pour chaque consommateur qui souhaite surveiller cette ressource protégée.
seo-title: Préparation du contenu
title: Préparation du contenu
uuid: 7a3562c6-6033-4e28-8f0a-18e3cb8987b9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# Préparation du contenu {#content-preparation}

Toute utilisation de l&#39;accès aux Adobes consiste en deux étapes clés à différents points du processus. La préparation du contenu doit être effectuée une fois par ressource, ce qui entraîne la création de contenu protégé. L&#39;acquisition de contenu se fait à plusieurs reprises, une fois pour chaque consommateur qui souhaite surveiller cette ressource protégée.

Avant de rendre le contenu disponible pour la distribution, vous devez tout d’abord coder le contenu au format vidéo FLV ou F4V, créer une ou plusieurs stratégies spécifiant les règles d’utilisation du contenu et assembler le contenu à l’aide du SDK d’accès à l’Adobe.

Les étapes pour coder, assembler et distribuer du contenu sont les suivantes :

1. Encodez le contenu au format FLV ou F4V à l’aide d’outils de codage disponibles à l’Adobe ou à des tiers.
1. Créez des stratégies spécifiant les règles d’utilisation sous lesquelles les consommateurs peuvent vue le contenu.

   Une stratégie est le conteneur des règles et restrictions qui déterminent comment, quand et où le contenu protégé peut être affiché par les consommateurs.

   L’outil de création de package requiert au moins une stratégie avec au moins une règle d’utilisation. Vous pouvez remplacer la règle d’utilisation et ajouter d’autres règles d’utilisation lorsque le serveur de licences génère la licence.

1. Compressez le contenu et spécifiez les stratégies à appliquer.

   Adobe Access SDK chiffre le contenu à l’aide d’une clé de chiffrement de contenu (CEK) et lie une ou plusieurs stratégies au contenu. Le résultat est un fichier *de contenu protégé *qui ne peut être lu que par un consommateur qui a obtenu une licence auprès du serveur de licences correspondant.

   Lors de l’assemblage, le contenu est chiffré à l’aide du CEK. Le CEK est chiffré à l’aide de la clé publique du serveur de licences et inclus dans les métadonnées DRM avec les stratégies. Les métadonnées DRM sont signées à l’aide de la clé privée Packager et elles sont incluses dans le contenu protégé.

1. Rendre le contenu protégé disponible pour distribution aux consommateurs.

   Le contenu protégé est généralement distribué à l’aide d’un réseau de distribution de contenu (CDN). Le CDN peut utiliser tout mécanisme pris en charge par l’exécution du client, tel que le Flash Media Server, le HTTP Dynamic Streaming d’Adobe pour la diffusion en flux continu à débit multiple ou un serveur Web HTTP pour le téléchargement progressif.

