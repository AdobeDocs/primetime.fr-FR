---
seo-title: Présentation de la création de packages de fichiers multimédias
title: Présentation de la création de packages de fichiers multimédias
uuid: 9509bcdc-ee4d-4025-9bb6-9b8ac439b926
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# Présentation {#packaging-media-files-overview}

L’emballage fait référence au processus de chiffrement et d’application d’une stratégie DRM au contenu vidéo. Vous pouvez utiliser les API d’assemblage de supports pour assembler des fichiers. Le SDK Java DRM de Primetime peut uniquement inclure du contenu à téléchargement progressif, tel que MP4.

>[!NOTE]
>
>N&#39;oubliez pas de contacter votre représentant DRM Primetime pour savoir comment choisir l&#39;option d&#39;emballage la plus appropriée pour votre format multimédia et vos cas d&#39;utilisation.

Le groupement est dissocié du serveur de licences. Il n’est pas nécessaire que le gestionnaire de package se connecte au serveur de licences pour échanger des informations sur le contenu. Tout ce dont le serveur de licences a besoin pour délivrer une licence est inclus dans les métadonnées de contenu.

Lorsqu’un fichier est chiffré, son contenu ne peut pas être analysé sans la licence appropriée. Vous pouvez utiliser le DRM Primetime pour sélectionner les parties du fichier à chiffrer. Puisque Primetime DRM peut analyser le format de fichier du contenu vidéo, il peut chiffrer intelligemment certaines parties d’un fichier au lieu d’un fichier entier. Les données, telles que les métadonnées et les indices, peuvent rester non chiffrées afin que les moteurs de recherche puissent continuer à rechercher le fichier.

Un élément de contenu spécifié peut avoir plusieurs stratégies DRM. Par exemple, vous pouvez attribuer des licences au contenu sous différents modèles d’entreprise sans avoir à regrouper le contenu plusieurs fois. De plus, vous pouvez autoriser l’accès anonyme pendant une courte période, puis permettre au client d’acheter le contenu pour un accès illimité. Si le contenu est compressé en utilisant plusieurs stratégies DRM, le serveur de licences doit implémenter une logique pour sélectionner la stratégie DRM à utiliser pour émettre une licence.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>L&#39;architecture permet de spécifier des stratégies DRM d&#39;utilisation et de les lier au contenu lorsque le contenu est compressé. Pour qu’un client puisse lire du contenu, il doit acquérir une licence pour un ordinateur spécifié. La licence spécifie les règles d’utilisation qui sont appliquées et fournit la clé qui doit être utilisée pour déchiffrer le contenu. La stratégie DRM représente un modèle pour générer une licence. Cependant, le serveur de licences peut remplacer les règles d’utilisation lorsqu’il délivre une licence. La licence peut être rendue invalide par de telles contraintes, telles que les délais d’expiration ou les fenêtres de lecture.

Primetime DRM fournit une API pour transmettre le CEK. Si aucun CEK n’est spécifié, le SDK le génère de manière aléatoire. En règle générale, vous avez besoin d’un autre CEK pour chaque section de contenu. Cependant, dans la diffusion en flux continu dynamique, il est probable que vous utilisiez le même CEK pour tous les fichiers qui composent ce contenu. Par conséquent, un utilisateur n&#39;a besoin que d&#39;une seule licence pour pouvoir transition en toute transparence d&#39;un débit à l&#39;autre. Si vous souhaitez utiliser la même clé et la même licence pour plusieurs éléments de contenu, vous devez transmettre le même `DRMParameters` objet à `MediaEncrypter.encryptContent()`, ou transmettre le CEK à l’aide `V2KeyParameters.setContentEncryptionKey()`. Si vous souhaitez utiliser une clé et une licence différentes pour chaque section de contenu, vous devez créer une nouvelle `DRMParameters` instance pour chaque fichier.

Lorsque vous assemblez du contenu à l’aide de la rotation des clés, vous pouvez contrôler les clés de rotation utilisées et la fréquence de modification des clés. `F4VDRMParameters` et `FLVDRMParameters` implémenter l’ `KeyRotationParameters` interface. Grâce à cette interface, vous pouvez activer la rotation des clés. Vous devez également spécifier un `RotatingContentEncryptionKeyProvider`paramètre. Pour chaque exemple chiffré, cette classe détermine la clé de rotation à utiliser. Vous pouvez mettre en oeuvre votre propre fournisseur ou utiliser les `TimeBasedKeyProvider` composants inclus dans le SDK. Cette implémentation génère de manière aléatoire une nouvelle clé après un nombre spécifié de secondes.

Dans certains cas, vous devrez peut-être stocker les métadonnées du contenu dans un fichier distinct et les rendre disponibles au client séparément du contenu. Dans ce cas, vous devez appeler `MediaEncrypter.encryptContent()`, ce qui renvoie un `MediaEncrypterResult` objet. Appelez `MediaEncrypterResult.getKeyInfo()` et envoyez le résultat à `V2KeyStatus`. Ensuite, récupérez les métadonnées de contenu et stockez-les dans un fichier.

Toutes ces tâches peuvent être accomplies avec l’API Java.

Pour plus d’informations sur l’API Java, voir *Adobe Primetime DRM API Reference* .

Voir *Utilisation des implémentations* de référence DRM d’Adobe Primetime pour en savoir plus sur l’implémentation de référence de Media Packager.
