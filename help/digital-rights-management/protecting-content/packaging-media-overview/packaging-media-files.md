---
title: Présentation de la création de fichiers multimédias
description: Présentation de la création de fichiers multimédias
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 0%

---

# Présentation {#packaging-media-files-overview}

L’assemblage fait référence au processus de chiffrement et d’application d’une stratégie DRM au contenu vidéo. Vous pouvez utiliser les API de package multimédia pour compresser les fichiers. Le SDK Java DRM Primetime peut uniquement compresser le contenu téléchargé de manière progressive, tel que MP4.

>[!NOTE]
>
>Veillez à contacter votre représentant DRM Primetime pour savoir comment sélectionner l’option de conditionnement la plus appropriée à votre format multimédia et à vos cas d’utilisation.

Le package est découplé à partir du serveur de licences. Il n’est pas nécessaire que le gestionnaire de paquets se connecte au serveur de licences pour échanger des informations sur le contenu. Tout ce que le serveur de licences doit savoir pour émettre une licence est inclus dans les métadonnées du contenu.

Lorsqu’un fichier est chiffré, son contenu ne peut pas être analysé sans la licence appropriée. Vous pouvez utiliser Primetime DRM pour sélectionner les parties du fichier que vous souhaitez chiffrer. Étant donné que Primetime DRM peut analyser le format de fichier du contenu vidéo, il peut chiffrer intelligemment certaines parties d’un fichier au lieu d’un fichier entier. Les données, telles que les métadonnées et les points de repère, peuvent rester non chiffrées afin que les moteurs de recherche puissent toujours rechercher le fichier.

Un élément de contenu spécifié peut avoir plusieurs stratégies DRM. Par exemple, vous pouvez acquérir sous licence du contenu sous différents modèles d’entreprise sans avoir à le compresser plusieurs fois. De plus, vous pouvez autoriser l’accès anonyme pendant une courte période, puis permettre au client d’acheter le contenu pour avoir un accès illimité. Si le contenu est compilé à l’aide de plusieurs stratégies DRM, le serveur de licences doit implémenter une logique pour sélectionner la stratégie DRM à utiliser pour émettre une licence.

>[!NOTE]
>
>L’architecture permet de spécifier des stratégies DRM d’utilisation et de les lier au contenu lorsque le contenu est compressé. Pour qu’un client puisse lire du contenu, il doit acquérir une licence pour un ordinateur spécifié. La licence spécifie les règles d’utilisation qui sont appliquées et fournit la clé qui doit être utilisée pour déchiffrer le contenu. La stratégie DRM représente un modèle pour générer une licence. Cependant, le serveur de licences peut remplacer les règles d’utilisation lorsqu’il émet une licence. La licence peut être rendue non valide par ces contraintes, telles que les délais d’expiration ou les fenêtres de lecture.

Primetime DRM fournit une API pour transmettre le CEK. Si aucun CEK n’est spécifié, le SDK le génère de manière aléatoire. En règle générale, vous avez besoin d’un autre CEK pour chaque section de contenu. Cependant, dans la diffusion en flux continu dynamique, il est probable que vous utilisiez le même CEK pour tous les fichiers qui composent ce contenu. Par conséquent, un utilisateur n’a besoin que d’une seule licence pour passer facilement d’un débit binaire à un autre. Si vous souhaitez utiliser la même clé et la même licence pour plusieurs éléments de contenu, vous devez transmettre la même `DRMParameters` vers `MediaEncrypter.encryptContent()`, ou transmettez le CEK à l’aide de `V2KeyParameters.setContentEncryptionKey()`. Si vous souhaitez utiliser une clé et une licence différentes pour chaque section de contenu, vous devez créer une nouvelle `DRMParameters` pour chaque fichier.

Lorsque vous compressez le contenu à l’aide de la rotation des clés, vous pouvez contrôler les clés de rotation utilisées et la fréquence à laquelle elles changent. `F4VDRMParameters` et `FLVDRMParameters` mettre en oeuvre le `KeyRotationParameters` . Grâce à cette interface, vous pouvez activer la rotation des clés. Vous devez également spécifier une `RotatingContentEncryptionKeyProvider`. Pour chaque exemple chiffré, cette classe détermine la clé de rotation à utiliser. Vous pouvez mettre en oeuvre votre propre fournisseur ou utiliser la variable `TimeBasedKeyProvider` inclus avec le SDK. Cette implémentation génère de manière aléatoire une nouvelle clé après un nombre spécifié de secondes.

Dans certains cas, vous devrez peut-être stocker les métadonnées de contenu sous la forme d’un fichier distinct et les rendre disponibles au client séparément du contenu. Dans ce cas, vous devez appeler `MediaEncrypter.encryptContent()`, qui renvoie une `MediaEncrypterResult` . Appeler `MediaEncrypterResult.getKeyInfo()` et convertissez le résultat en `V2KeyStatus`. Récupérez ensuite les métadonnées de contenu et stockez-les dans un fichier.

Toutes ces tâches peuvent être effectuées avec l’API Java.

Voir *Référence de l’API DRM Adobe Primetime* pour plus d’informations sur l’API Java.

Voir *Utilisation des implémentations de référence DRM Adobe Primetime* pour plus d’informations sur l’implémentation de référence de Media Packager.
