---
title: Options de groupement
description: Options de groupement
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---

# Options de groupement{#packaging-options}

De nombreuses options sont disponibles pour le contenu de l&#39;emballage. Vous pouvez spécifier les options de la variable `DRMParameters` et implémentez les classes qui peuvent s’afficher dans l’interface. Avec ces classes, vous pouvez définir des paramètres de signature et de clé et indiquer s’il faut chiffrer le contenu audio, le contenu vidéo ou les données de script. Pour découvrir comment ces fonctionnalités sont implémentées dans l’implémentation de référence, consultez les descriptions des options de ligne de commande Media Packager décrites dans la section *Utilisation des implémentations de référence DRM Adobe Primetime*. Ces options sont basées sur l’API Java et sont donc disponibles pour une utilisation par programmation.

Les options de conditionnement incluent :

* Options de chiffrement (audio, vidéo, chiffrement partiel).
* URL du serveur de licences utilisée par le client comme URL de base pour toutes les demandes envoyées au serveur de licences
* Certificat de transport du serveur de licences
* Certificat du serveur de licences, utilisé pour chiffrer le CEK
* Informations d’identification de Packager pour la signature de métadonnées
