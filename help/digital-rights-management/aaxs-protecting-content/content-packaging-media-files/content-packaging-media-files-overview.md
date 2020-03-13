---
seo-title: Présentation
title: Présentation
uuid: 11cf1f1f-a4b2-4ac2-aae7-e925d96729d2
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Présentation {#overview}

*L’emballage* désigne le processus de chiffrement et d’application d’une stratégie aux fichiers FLV ou F4V. Utilisez les API de création de package multimédia pour créer des packages de fichiers. Le SDK Java d’Adobe Access peut uniquement inclure dans un package du contenu Flash et AIR à téléchargement progressif, tel que FLV, F4V et MP4. Pour compresser du contenu à l’aide d’Adobe Access DRM pour d’autres formats de contenu, tels qu’Adobe HTTP Dynamic Streaming (HDS) ou Apple HTTP Live Streaming (HLS), vous devez utiliser d’autres outils, tels qu’Adobe Media Server ( [https://www.adobe.com/products/adobe-media-server-family.html](https://www.adobe.com/products/adobe-media-server-family.html)) ou un encodeur qui implémente le SDK Adobe Broadcast ( [https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf](https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf)). Les clients peuvent également choisir d’utiliser le jeu d’outils Java Primetime Packager d’Adobe, qui permet d’assembler du contenu pour divers formats de , tels que HDS, HLS et DASH.

L’assemblage est dissocié du serveur de licences. Il n’est pas nécessaire que le gestionnaire de package se connecte au serveur de licences pour échanger des informations sur le contenu. Tout ce que le serveur de licences doit savoir pour émettre la licence est inclus dans les métadonnées de contenu.

Lorsqu’un fichier est chiffré, son contenu ne peut pas être analysé sans la licence appropriée. Adobe Access vous permet de sélectionner les parties du fichier à chiffrer. Adobe® Access™ pouvant analyser le format de fichier du contenu FLV et F4V, il peut chiffrer intelligemment certaines parties du fichier au lieu de l’ensemble du fichier. Les données, telles que les métadonnées et les points de repère, peuvent rester non chiffrées afin que les moteurs de recherche puissent toujours rechercher le fichier.

Il est possible qu’un élément de contenu donné ait plusieurs stratégies. Cela peut s’avérer utile, par exemple, si vous souhaitez activer la licence d’un contenu selon différents modèles d’entreprise sans avoir à compresser le contenu plusieurs fois. Par exemple, vous pouvez autoriser l’accès anonyme pendant une courte période, puis permettre au client d’acheter le contenu et d’avoir un accès illimité. Si le contenu est compressé à l’aide de plusieurs stratégies, le serveur de licences doit implémenter la logique permettant de sélectionner la stratégie à utiliser pour émettre une licence.

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>L’architecture permet de spécifier des stratégies d’utilisation et de les lier au contenu lorsque le contenu est compressé. Pour qu’un client puisse lire le contenu, il doit acquérir une licence pour cet ordinateur. La licence spécifie les règles d’utilisation qui sont appliquées et fournit la clé utilisée pour déchiffrer le contenu. La stratégie est un modèle pour générer la licence, mais le serveur de licences peut choisir de remplacer les règles d’utilisation lors de l’émission de la licence. Notez que la licence peut être rendue non valide par des contraintes telles que les délais d’expiration ou les fenêtres de lecture.

De nombreuses options sont disponibles lors de l’assemblage du contenu. Elles sont spécifiées dans l’ `DRMParameters` interface et les classes qui implémentent cette interface, qui sont les `F4VDRMParameters` et `FLVDRMParameters`. Ces classes vous permettent de définir des paramètres de signature et de clé, ainsi que d’indiquer si vous devez chiffrer du contenu audio, du contenu vidéo ou des données de script. Pour voir comment ces éléments sont implémentés dans l’implémentation des références, voir les descriptions des options de ligne de commande de Media Packager décrites dans *Utilisation des implémentations* de référence d’Adobe Access. Ces options sont basées sur l’API Java et sont donc disponibles pour la programmation.

Les options d’emballage incluent :

* Options de chiffrement (audio, vidéo, chiffrement partiel).
* URL du serveur de licences (le client l’utilise comme URL de base pour toutes les requêtes envoyées au serveur de licences)
* Certificat de transport du serveur de licences
* Certificat du serveur de licences, utilisé pour chiffrer le CEK.
* Informations d’identification de Packager pour la signature des métadonnées

Adobe Access fournit une API pour transmettre le CEK. Si aucun CEK n’est spécifié, le SDK le génère de manière aléatoire. En règle générale, vous avez besoin d’un autre CEK pour chaque élément de contenu. Cependant, dans la diffusion en flux continu dynamique, vous utiliserez probablement le même CEK pour tous les fichiers de ce contenu. L’utilisateur n’a donc besoin que d’une seule licence et peut facilement  d’un débit binaire à un autre. Pour utiliser la même clé et la même licence pour plusieurs éléments de contenu, transmettez le même `DRMParameters` objet à `MediaEncrypter.encryptContent()`, ou transmettez le CEK à l’aide de `V2KeyParameters.setContentEncryptionKey()`. Pour utiliser une clé et une licence différentes pour chaque élément de contenu, créez une `DRMParameters` instance pour chaque fichier.

Lors de l’assemblage du contenu à l’aide de la rotation des clés, vous pouvez contrôler les clés de rotation utilisées et la fréquence de modification des clés. `F4VDRMParameters` et `FLVDRMParameters` implémenter l’ `KeyRotationParameters` interface. Grâce à cette interface, vous pouvez activer la rotation des clés. Vous devez également spécifier un `RotatingContentEncryptionKeyProvider`. Pour chaque exemple chiffré, cette classe détermine la clé de rotation à utiliser. Vous pouvez mettre en oeuvre votre propre fournisseur ou utiliser les `TimeBasedKeyProvider` composants inclus dans le SDK. Cette implémentation génère de manière aléatoire une nouvelle clé après un nombre spécifié de secondes.

Dans certains cas, vous devrez peut-être stocker les métadonnées de contenu dans un fichier distinct et les rendre accessibles au client séparément du contenu. Pour ce faire, appelez `MediaEncrypter.encryptContent()`, ce qui renvoie un `MediaEncrypterResult` objet. Appelez `MediaEncrypterResult.getKeyInfo()` et définissez le résultat sur `V2KeyStatus`. Récupérez ensuite les métadonnées de contenu et stockez-les dans un fichier.

Tous ces  de peuvent être effectués à l’aide de l’API Java. Pour plus d’informations sur l’API Java abordée dans ce chapitre, voir Référence *sur l’API d’accès* Adobe.

Pour plus d’informations sur l’implémentation de référence de Media Packager, voir *Utilisation des implémentations* de référence d’Adobe Access.
