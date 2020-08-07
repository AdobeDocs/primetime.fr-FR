---
seo-title: Présentation
title: Présentation
uuid: 11cf1f1f-a4b2-4ac2-aae7-e925d96729d2
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---


# Présentation {#overview}

*L’emballage* fait référence au processus de chiffrement et d’application d’une stratégie aux fichiers FLV ou F4V. Utilisez les API de création de package des médias pour assembler des fichiers. Le SDK Java d’Adobe Access ne peut inclure que le Flash de téléchargement progressif et le contenu AIR, tel que FLV, F4V et MP4. Pour compresser du contenu à l’aide de la gestion des droits numériques d’accès aux Adobes pour d’autres formats de contenu, tels que Adobe HTTP Dynamic Streaming (HDS) ou Apple HTTP Live Streaming (HLS), vous devez utiliser d’autres outils, tels que Adobe Media Server ( [https://www.adobe.com/products/adobe-media-server-family.html](https://www.adobe.com/products/adobe-media-server-family.html)) ou un encodeur qui implémente le kit SDK de diffusion d’Adobe ( [https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf](https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf)). Les clients peuvent également choisir d’utiliser le jeu d’outils Java Primetime Packager d’Adobe, qui permet d’assembler du contenu pour divers formats de cible, tels que HDS, HLS et DASH.

Le groupement est dissocié du serveur de licences. Il n’est pas nécessaire que le gestionnaire de package se connecte au serveur de licences pour échanger des informations sur le contenu. Tout ce dont le serveur de licences a besoin pour délivrer la licence est inclus dans les métadonnées de contenu.

Lorsqu’un fichier est chiffré, son contenu ne peut pas être analysé sans la licence appropriée. Accès aux Adobes vous permet de sélectionner les parties du fichier à chiffrer. Adobe® Access™ pouvant analyser le format de fichier du contenu FLV et F4V, il peut crypter intelligemment certaines parties du fichier au lieu de l&#39;ensemble du fichier. Les données telles que les métadonnées et les indices peuvent rester non chiffrées afin que les moteurs de recherche puissent continuer à rechercher le fichier.

Il est possible qu’un élément de contenu donné ait plusieurs stratégies. Cela peut s’avérer utile, par exemple, si vous souhaitez activer la licence d’un contenu selon différents modèles d’entreprise sans avoir à compresser le contenu plusieurs fois. Par exemple, vous pouvez autoriser l’accès anonyme pendant une courte période et, par la suite, permettre au client d’acheter le contenu et d’avoir un accès illimité. Si le contenu est compressé à l’aide de plusieurs stratégies, le serveur de licences doit implémenter une logique pour sélectionner la stratégie à utiliser pour émettre une licence.

>[!NOTE]
>
>L’architecture permet de spécifier des stratégies d’utilisation et de les lier au contenu lorsque le contenu est compressé. Pour qu’un client puisse lire du contenu, il doit acquérir une licence pour cet ordinateur. La licence spécifie les règles d’utilisation qui sont appliquées et fournit la clé utilisée pour déchiffrer le contenu. La stratégie est un modèle pour générer la licence, mais le serveur de licences peut choisir de remplacer les règles d’utilisation lors de l’émission de la licence. Notez que la licence peut être rendue invalide par des contraintes telles que les délais d’expiration ou les fenêtres de lecture.

De nombreuses options sont disponibles lors de l’emballage du contenu. Elles sont spécifiées dans l&#39; `DRMParameters` interface et les classes implémentant cette interface, qui sont les `F4VDRMParameters` et `FLVDRMParameters`. Ces classes permettent de définir des paramètres de signature et de clé, ainsi que d’indiquer s’il faut chiffrer du contenu audio, du contenu vidéo ou des données de script. Pour voir comment ces solutions sont mises en oeuvre dans l’implémentation des références, voir les descriptions des options de ligne de commande de Media Packager décrites dans *Utilisation des implémentations* de référence d’accès à l’Adobe. Ces options sont basées sur l’API Java et sont donc disponibles pour la programmation.

Les options d’emballage incluent :

* Options de chiffrement (audio, vidéo, chiffrement partiel).
* URL du serveur de licences (le client l’utilise comme URL de base pour toutes les requêtes envoyées au serveur de licences)
* Certificat de transport du serveur de licences
* Certificat du serveur de licences, utilisé pour chiffrer le CEK.
* Informations d’identification de Packager pour la signature des métadonnées

adobe Access fournit une API pour transmettre le CEK. Si aucun CEK n’est spécifié, le SDK le génère de manière aléatoire. En règle générale, vous avez besoin d’un autre CEK pour chaque élément de contenu. Cependant, dans la diffusion en flux continu dynamique, vous utiliseriez probablement le même CEK pour tous les fichiers de ce contenu. L’utilisateur n’a donc besoin que d’une seule licence et peut facilement transition d’un débit binaire à l’autre. Pour utiliser la même clé et la même licence pour plusieurs éléments de contenu, transmettez le même `DRMParameters` objet à `MediaEncrypter.encryptContent()`ou transmettez le CEK à l’aide de `V2KeyParameters.setContentEncryptionKey()`. Pour utiliser une clé et une licence différentes pour chaque élément de contenu, créez une nouvelle `DRMParameters` instance pour chaque fichier.

Lorsque vous incluez du contenu à l’aide d’une rotation de clé, vous pouvez contrôler les clés de rotation utilisées et la fréquence de modification des clés. `F4VDRMParameters` et `FLVDRMParameters` implémenter l’ `KeyRotationParameters` interface. Grâce à cette interface, vous pouvez activer la rotation des clés. Vous devez également spécifier un `RotatingContentEncryptionKeyProvider`paramètre. Pour chaque exemple chiffré, cette classe détermine la clé de rotation à utiliser. Vous pouvez mettre en oeuvre votre propre fournisseur ou utiliser les `TimeBasedKeyProvider` composants inclus dans le SDK. Cette implémentation génère de manière aléatoire une nouvelle clé après un nombre spécifié de secondes.

Dans certains cas, vous devrez peut-être stocker les métadonnées du contenu dans un fichier distinct et les rendre disponibles au client séparément du contenu. Pour ce faire, appelez `MediaEncrypter.encryptContent()`, qui renvoie un `MediaEncrypterResult` objet. Appelez `MediaEncrypterResult.getKeyInfo()` et envoyez le résultat à `V2KeyStatus`. Ensuite, récupérez les métadonnées de contenu et stockez-les dans un fichier.

Toutes ces tâches peuvent être effectuées à l’aide de l’API Java. Pour plus d&#39;informations sur l&#39;API Java abordée dans ce chapitre, consultez le Guide de référence *de l&#39;API d&#39;accès aux* Adobes.

Pour plus d’informations sur l’implémentation de référence de Media Packager, voir *Utilisation des implémentations* de référence d’accès à l’Adobe.
