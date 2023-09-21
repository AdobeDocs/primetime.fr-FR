---
title: Présentation
description: Présentation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Présentation {#overview}

*Modules* fait référence au processus de chiffrement et d’application d’une stratégie aux fichiers FLV ou F4V. Utilisez les API de package multimédia pour compresser les fichiers. Le SDK Java Adobe Access peut uniquement regrouper le contenu AIR et le Flash de téléchargement progressif, comme FLV, F4V et MP4. Pour regrouper du contenu à l’aide d’Adobe Access DRM pour d’autres formats de contenu, tels que Adobe HTTP Dynamic Streaming (HDS) ou Apple HTTP Live Streaming (HLS), vous devez utiliser d’autres outils, tels que Adobe Media Server ( [https://www.adobe.com/products/adobe-media-server-family.html](https://www.adobe.com/products/adobe-media-server-family.html)) ou un encodeur qui implémente le SDK de diffusion par Adobe ( [https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf](https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf)). Les clients peuvent également choisir d’utiliser l’ensemble d’outils Java Primetime Packager d’Adobe, qui peut compresser le contenu pour divers formats cibles, tels que HDS, HLS et DASH.

Le package est découplé à partir du serveur de licences. Il n’est pas nécessaire que le gestionnaire de paquets se connecte au serveur de licences pour échanger des informations sur le contenu. Tout ce que le serveur de licences doit savoir pour émettre la licence est inclus dans les métadonnées du contenu.

Lorsqu’un fichier est chiffré, son contenu ne peut pas être analysé sans la licence appropriée. Adobe Access vous permet de sélectionner les parties du fichier à chiffrer. Comme Adobe® Access™ peut analyser le format de fichier du contenu FLV et F4V, il peut chiffrer intelligemment certaines parties du fichier au lieu de l’ensemble du fichier. Les données telles que les métadonnées et les repères peuvent rester non chiffrées afin que les moteurs de recherche puissent toujours rechercher le fichier.

Il est possible qu’un élément de contenu donné ait plusieurs stratégies. Cela peut s’avérer utile, par exemple, si vous souhaitez obtenir une licence pour du contenu sous différents modèles d’entreprise sans avoir à compresser le contenu plusieurs fois. Par exemple, vous pouvez autoriser l’accès anonyme pendant une courte période et, par la suite, permettre au client d’acheter le contenu et d’avoir un accès illimité. Si le contenu est compilé à l’aide de plusieurs stratégies, le serveur de licences doit implémenter une logique pour sélectionner la stratégie à utiliser pour émettre une licence.

>[!NOTE]
>
>L’architecture permet de spécifier des stratégies d’utilisation et de les lier au contenu lorsque le contenu est compressé. Pour qu’un client puisse lire du contenu, il doit acquérir une licence pour cet ordinateur. La licence spécifie les règles d’utilisation qui sont appliquées et fournit la clé utilisée pour déchiffrer le contenu. La stratégie est un modèle pour générer la licence, mais le serveur de licences peut choisir de remplacer les règles d’utilisation lors de l’émission de la licence. Notez que la licence peut être rendue non valide par des contraintes telles que les délais d’expiration ou les fenêtres de lecture.

De nombreuses options sont disponibles lors de l’emballage du contenu. Elles sont spécifiées dans la variable `DRMParameters` et les classes implémentant cette interface, qui sont les `F4VDRMParameters` et `FLVDRMParameters`. Avec ces classes, vous pouvez définir des paramètres de signature et de clé et indiquer s’il faut chiffrer le contenu audio, le contenu vidéo ou les données de script. Pour découvrir comment ces fonctionnalités sont implémentées dans l’implémentation de référence, consultez les descriptions des options de ligne de commande Media Packager décrites dans la section *Utilisation des implémentations de référence d’accès Adobe*. Ces options sont basées sur l’API Java et sont donc disponibles pour une utilisation par programmation.

Les options de conditionnement incluent :

* Options de chiffrement (audio, vidéo, chiffrement partiel).
* URL du serveur de licences (le client l’utilise comme URL de base pour toutes les demandes envoyées au serveur de licences)
* Certificat de transport du serveur de licences
* Certificat du serveur de licences, utilisé pour chiffrer le CEK.
* Informations d’identification de Packager pour la signature de métadonnées

Adobe Access fournit une API pour transmettre le CEK. Si aucun CEK n’est spécifié, le SDK le génère de manière aléatoire. En règle générale, vous avez besoin d’un autre CEK pour chaque élément de contenu. Cependant, dans la diffusion en flux continu dynamique, il est probable que vous utilisiez le même CEK pour tous les fichiers de ce contenu. Par conséquent, l’utilisateur n’a besoin que d’une seule licence et peut facilement passer d’un débit binaire à un autre. Pour utiliser la même clé et la même licence pour plusieurs éléments de contenu, transmettez la même `DRMParameters` vers `MediaEncrypter.encryptContent()`, ou transmettez le CEK à l’aide de `V2KeyParameters.setContentEncryptionKey()`. Pour utiliser une clé et une licence différentes pour chaque élément de contenu, créez une nouvelle `DRMParameters` pour chaque fichier.

Lors du conditionnement du contenu à l’aide de la rotation des clés, vous pouvez contrôler les clés de rotation utilisées et la fréquence à laquelle les clés changent. `F4VDRMParameters` et `FLVDRMParameters` mettre en oeuvre le `KeyRotationParameters` . Grâce à cette interface, vous pouvez activer la rotation des clés. Vous devez également spécifier une `RotatingContentEncryptionKeyProvider`. Pour chaque exemple chiffré, cette classe détermine la clé de rotation à utiliser. Vous pouvez mettre en oeuvre votre propre fournisseur ou utiliser la variable `TimeBasedKeyProvider` inclus avec le SDK. Cette implémentation génère de manière aléatoire une nouvelle clé après un nombre spécifié de secondes.

Dans certains cas, vous devrez peut-être stocker les métadonnées de contenu sous la forme d’un fichier distinct et les rendre disponibles au client séparément du contenu. Pour ce faire, appelez `MediaEncrypter.encryptContent()`, qui renvoie une `MediaEncrypterResult` . Appeler `MediaEncrypterResult.getKeyInfo()` et convertissez le résultat en `V2KeyStatus`. Récupérez ensuite les métadonnées de contenu et stockez-les dans un fichier.

Toutes ces tâches peuvent être effectuées à l’aide de l’API Java. Pour plus d’informations sur l’API Java discutée dans ce chapitre, voir *Référence de l’API Adobe Access*.

Pour plus d’informations sur l’implémentation de référence de Media Packager, voir *Utilisation des implémentations de référence d’accès Adobe*.
