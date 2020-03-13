---
seo-title: Options d’assemblage
title: Options d’assemblage
uuid: 04244428-cb42-438a-8f16-91532c70ea60
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Options d’assemblage{#packaging-options}

Vous disposez de nombreuses options pour l’emballage du contenu. Vous pouvez spécifier les options de l’ `DRMParameters` interface et mettre en oeuvre les classes qui peuvent l’interface. Ces classes vous permettent de définir des paramètres de signature et de clé, ainsi que d’indiquer si vous devez chiffrer du contenu audio, du contenu vidéo ou des données de script. Pour voir comment ces éléments sont implémentés dans l’implémentation des références, reportez-vous aux descriptions des options de ligne de commande de Media Packager décrites dans *Utilisation des implémentations* de référence DRM d’Adobe Primetime. Ces options sont basées sur l’API Java et sont donc disponibles pour une utilisation par programmation.

Les options d’emballage incluent :

* Options de chiffrement (audio, vidéo, chiffrement partiel).
* URL du serveur de licences utilisée par le client comme URL de base pour toutes les requêtes envoyées au serveur de licences
* Certificat de transport du serveur de licences
* Certificat du serveur de licences, utilisé pour chiffrer le CEK
* Informations d’identification de Packager pour la signature des métadonnées

