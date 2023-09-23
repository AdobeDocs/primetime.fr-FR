---
description: Toute utilisation d’Adobe Primetime DRM consiste en deux étapes clés à différents points du workflow. La préparation du contenu doit être effectuée une fois par ressource et entraîne la création de contenu protégé. L’acquisition de contenu est effectuée à plusieurs reprises, une fois pour chaque consommateur qui souhaite regarder cette ressource protégée.
title: Préparation du contenu
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Préparation du contenu{#content-preparation}

Toute utilisation d’Adobe Primetime DRM consiste en deux étapes clés à différents points du workflow. La préparation du contenu doit être effectuée une fois par ressource et entraîne la création de contenu protégé. L’acquisition de contenu est effectuée à plusieurs reprises, une fois pour chaque consommateur qui souhaite regarder cette ressource protégée.

Avant de rendre le contenu disponible pour distribution, vous devez d’abord coder le contenu dans votre format vidéo, créer une ou plusieurs stratégies spécifiant les règles d’utilisation du contenu et regrouper le contenu à l’aide du SDK Adobe Primetime DRM.

Les étapes de codage, de package et de distribution de contenu sont les suivantes :

1. Codez le contenu dans le format vidéo souhaité à l’aide des outils de codage disponibles à partir d’Adobe ou de tiers.
1. Créez des stratégies spécifiant les règles d’utilisation sous lesquelles les consommateurs peuvent afficher le contenu.

   Une stratégie est le conteneur des règles et restrictions qui déterminent comment, quand et où le contenu protégé peut être consulté par les consommateurs.

   Le service de package requiert au moins une stratégie avec au moins une règle d’utilisation. Vous pouvez remplacer la règle d’utilisation et ajouter d’autres règles d’utilisation lorsque le serveur de licences génère la licence.

1. Regroupez le contenu et spécifiez les stratégies à appliquer.

   Le SDK DRM Primetime chiffre le contenu à l’aide d’une clé de chiffrement de contenu (CEK) et lie une ou plusieurs stratégies au contenu. Le résultat est un *fichier de contenu protégé* qui ne peut être lu que par un consommateur qui a obtenu une licence du serveur de licences correspondant.

   Lors de l’emballage, le contenu est chiffré à l’aide du CEK. Le CEK est chiffré à l’aide de la clé publique du serveur de licences et inclus dans les métadonnées DRM Primetime avec les stratégies. Les métadonnées DRM Primetime sont signées à l’aide de la clé privée Packager et les métadonnées sont incluses dans le contenu protégé.

1. Rendre le contenu protégé disponible pour distribution aux consommateurs.

   Le contenu protégé est généralement distribué à l’aide d’un réseau de distribution de contenu (CDN). Le réseau de diffusion de contenu peut utiliser n’importe quel mécanisme pris en charge par le composant d’exécution du client, comme Flash Media Server, HTTP Dynamic Streaming d’Adobe pour la diffusion en continu à débit multiple ou serveur web HTTP pour le téléchargement progressif.
