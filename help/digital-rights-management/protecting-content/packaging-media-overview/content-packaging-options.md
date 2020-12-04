---
seo-title: Options de création de package
title: Options de création de package
uuid: 04244428-cb42-438a-8f16-91532c70ea60
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# Options de création de package{#packaging-options}

Vous disposez de nombreuses options pour le contenu d’emballage. Vous pouvez spécifier les options dans l&#39;interface `DRMParameters` et implémenter les classes qui peuvent l&#39;interface. Ces classes permettent de définir des paramètres de signature et de clé, ainsi que d’indiquer s’il faut chiffrer du contenu audio, du contenu vidéo ou des données de script. Pour voir comment ces solutions sont implémentées dans l’implémentation des références, voir les descriptions des options de ligne de commande Media Packager décrites dans *Utilisation des implémentations de référence DRM d’Adobe Primetime*. Ces options sont basées sur l’API Java et sont donc disponibles pour la programmation.

Les options d’emballage incluent :

* Options de chiffrement (audio, vidéo, chiffrement partiel).
* URL du serveur de licences utilisée par le client comme URL de base pour toutes les requêtes envoyées au serveur de licences
* Certificat de transport du serveur de licences
* Certificat du serveur de licences, utilisé pour chiffrer le CEK
* Informations d’identification de Packager pour la signature des métadonnées

