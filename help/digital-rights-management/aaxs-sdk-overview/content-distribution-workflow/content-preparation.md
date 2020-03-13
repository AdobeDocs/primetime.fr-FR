---
description: Toute utilisation d’Adobe Access se compose de deux étapes clés à différents points du flux de travaux. La préparation du contenu doit être effectuée une fois par ressource, ce qui entraîne la création de contenu protégé. L’acquisition de contenu est effectuée plusieurs fois, une fois pour chaque consommateur qui souhaite surveiller cette ressource protégée.
seo-description: Toute utilisation d’Adobe Access se compose de deux étapes clés à différents points du flux de travaux. La préparation du contenu doit être effectuée une fois par ressource, ce qui entraîne la création de contenu protégé. L’acquisition de contenu est effectuée plusieurs fois, une fois pour chaque consommateur qui souhaite surveiller cette ressource protégée.
seo-title: Préparation du contenu
title: Préparation du contenu
uuid: 7a3562c6-6033-4e28-8f0a-18e3cb8987b9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Préparation du contenu {#content-preparation}

Toute utilisation d’Adobe Access se compose de deux étapes clés à différents points du flux de travaux. La préparation du contenu doit être effectuée une fois par ressource, ce qui entraîne la création de contenu protégé. L’acquisition de contenu est effectuée plusieurs fois, une fois pour chaque consommateur qui souhaite surveiller cette ressource protégée.

Avant de rendre le contenu disponible pour distribution, vous devez d’abord coder le contenu au format vidéo FLV ou F4V, créer une ou plusieurs stratégies spécifiant les règles d’utilisation du contenu, puis assembler le contenu à l’aide du SDK Adobe Access.

Les étapes pour coder, assembler et distribuer du contenu sont les suivantes :

1. Codez le contenu au format FLV ou F4V à l’aide des outils de codage disponibles auprès d’Adobe ou de tiers.
1. Créez des stratégies spécifiant les règles d’utilisation sous lesquelles les consommateurs peuvent le contenu.

   Une stratégie est le  des règles et des restrictions qui déterminent comment, quand et où le contenu protégé peut être affiché par les consommateurs.

   Le gestionnaire de package requiert au moins une stratégie avec au moins une règle d’utilisation. Vous pouvez remplacer la règle d’utilisation et ajouter d’autres règles d’utilisation lorsque le serveur de licences génère la licence.

1. Mettez en package le contenu et spécifiez les stratégies à appliquer.

   Le SDK Adobe Access chiffre le contenu à l’aide d’une clé de chiffrement de contenu (CEK) et lie une ou plusieurs stratégies au contenu. Le résultat est un fichier *de contenu protégé *qui ne peut être lu que par un consommateur qui a obtenu une licence auprès du serveur de licences correspondant.

   Lors de l’assemblage, le contenu est chiffré à l’aide du CEK. Le CEK est chiffré à l’aide de la clé publique du serveur de licences et inclus dans les métadonnées DRM avec les stratégies. Les métadonnées DRM sont signées à l’aide de la clé privée Packager et sont incluses dans le contenu protégé.

1. Rendre le contenu protégé disponible pour distribution aux consommateurs.

   Le contenu protégé est généralement distribué à l’aide d’un réseau de distribution de contenu (CDN). Le CDN peut utiliser tout mécanisme pris en charge par le runtime client, tel que Flash Media Server, Adobe HTTP Dynamic Streaming pour la diffusion en flux continu à débit multiple ou un serveur Web HTTP pour le téléchargement progressif.

