---
seo-title: Présentation de la création de packages de fichiers multimédia
title: Présentation de la création de packages de fichiers multimédia
uuid: 9509bcdc-ee4d-4025-9bb6-9b8ac439b926
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Présentation {#packaging-media-files-overview}

L’assemblage fait référence au processus de chiffrement et d’application d’une stratégie DRM au contenu vidéo. Vous pouvez utiliser les API de création de package multimédia pour créer des packages de fichiers. Le SDK Java DRM de Primetime peut uniquement inclure dans un package du contenu à téléchargement progressif, tel que MP4.

>[!NOTE]
>
>N&#39;oubliez pas de contacter votre représentant DRM Primetime pour savoir comment choisir l&#39;option d&#39;emballage la plus appropriée pour votre format multimédia et vos cas d&#39;utilisation.

L’assemblage est dissocié du serveur de licences. Il n’est pas nécessaire que le gestionnaire de package se connecte au serveur de licences pour échanger des informations sur le contenu. Tout ce que le serveur de licences doit savoir pour émettre une licence est inclus dans les métadonnées de contenu.

Lorsqu’un fichier est chiffré, son contenu ne peut pas être analysé sans la licence appropriée. Vous pouvez utiliser le DRM Primetime pour sélectionner les parties du fichier à chiffrer. Etant donné que le DRM Primetime peut analyser le format de fichier du contenu vidéo, il peut chiffrer intelligemment certaines parties d’un fichier au lieu d’un fichier entier. Les données, telles que les métadonnées et les points de repère, peuvent rester non chiffrées afin que les moteurs de recherche puissent toujours rechercher le fichier.

Un élément de contenu spécifié peut avoir plusieurs stratégies DRM. Par exemple, vous pouvez attribuer des licences au contenu sous différents modèles d’entreprise sans avoir à compresser le contenu plusieurs fois. De plus, vous pouvez autoriser l’accès anonyme pendant une courte période et ensuite permettre au client d’acheter le contenu pour un accès illimité. Si le contenu est compressé à l’aide de plusieurs stratégies DRM, le serveur de licences doit implémenter la logique permettant de sélectionner la stratégie DRM à utiliser pour émettre une licence.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>L’architecture permet de spécifier les stratégies DRM d’utilisation et de les lier au contenu lorsque le contenu est compressé. Pour qu’un client puisse lire du contenu, il doit acquérir une licence pour un ordinateur donné. La licence spécifie les règles d’utilisation qui sont appliquées et fournit la clé qui doit être utilisée pour déchiffrer le contenu. La stratégie DRM représente un modèle pour la génération d’une licence. Cependant, le serveur de licences peut remplacer les règles d’utilisation lorsqu’il délivre une licence. La licence peut être rendue non valide par de telles contraintes, telles que les délais d’expiration ou les fenêtres de lecture.

Primetime DRM fournit une API pour transmettre le CEK. Si aucun CEK n’est spécifié, le SDK le génère de manière aléatoire. En règle générale, vous avez besoin d’un autre CEK pour chaque section de contenu. Cependant, dans la diffusion en flux continu dynamique, il est probable que vous utilisiez le même CEK pour tous les fichiers qui composent ce contenu. Par conséquent, un utilisateur n’a besoin que d’une seule licence pour  en toute transparence d’un débit à un autre. Si vous souhaitez utiliser la même clé et la même licence pour plusieurs éléments de contenu, vous devez transmettre le même `DRMParameters` objet à `MediaEncrypter.encryptContent()`, ou transmettre le CEK à l’aide `V2KeyParameters.setContentEncryptionKey()`. Si vous souhaitez utiliser une clé et une licence différentes pour chaque section de contenu, vous devez créer une nouvelle `DRMParameters` instance pour chaque fichier.

Lorsque vous assemblez du contenu à l’aide de la rotation des clés, vous pouvez contrôler les clés de rotation utilisées et la fréquence de modification des clés. `F4VDRMParameters` et `FLVDRMParameters` implémenter l’ `KeyRotationParameters` interface. Grâce à cette interface, vous pouvez activer la rotation des clés. Vous devez également spécifier un `RotatingContentEncryptionKeyProvider`. Pour chaque exemple chiffré, cette classe détermine la clé de rotation à utiliser. Vous pouvez mettre en oeuvre votre propre fournisseur ou utiliser les `TimeBasedKeyProvider` composants inclus dans le SDK. Cette implémentation génère de manière aléatoire une nouvelle clé après un nombre spécifié de secondes.

Dans certains cas, vous devrez peut-être stocker les métadonnées de contenu dans un fichier distinct et les rendre accessibles au client séparément du contenu. Dans ce cas, vous devez appeler `MediaEncrypter.encryptContent()`, ce qui renvoie un `MediaEncrypterResult` objet. Appelez `MediaEncrypterResult.getKeyInfo()` et définissez le résultat sur `V2KeyStatus`. Récupérez ensuite les métadonnées de contenu et stockez-les dans un fichier.

Tous ces  de peuvent être réalisés avec l’API Java.

Pour plus d’informations sur l’API Java, consultez le Guide de référence *de l’API DRM* Adobe Primetime.

Voir *Utilisation des implémentations* de référence DRM d’Adobe Primetime pour en savoir plus sur l’implémentation de référence de Media Packager.
