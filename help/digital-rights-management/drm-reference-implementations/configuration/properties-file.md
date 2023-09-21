---
title: Fichier de propriétés du serveur de licences
description: Fichier de propriétés du serveur de licences
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# Fichier de propriétés du serveur de licences{#license-server-properties-file}

Le serveur de licences référence les propriétés définies dans la variable [!DNL flashaccess-refimpl.properties] fichier . Vous pouvez vous référer directement à ce fichier pour plus d’informations sur des valeurs spécifiques et pour plus d’informations sur l’utilisation de chaque propriété. Un exemple fonctionnel complet est fourni dans la section [!DNL resources] répertoire de l’implémentation de référence ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources/).`).

**Informations d’identification** - Le fichier de propriétés comprend des paramètres pour l’emplacement des informations d’identification qui vous Adobe des problèmes. Vous pouvez spécifier ces informations d’identification dans une [!DNL .pfx] avec un mot de passe ou fournissez un alias et un mot de passe pour les informations d’identification stockées sur un HSM. Vous devez au moins configurer les propriétés liées aux informations d’identification de transport et aux informations d’identification du serveur de licences. Spécifiez l’emplacement de vos fichiers d’informations d’identification par rapport au répertoire que vous spécifiez dans la variable `config.resourcesDirectory` .

**Flash Media Rights Management Server** - La variable `flashaccess-refimpl.properties` comprend également plusieurs propriétés liées au contenu de package. Ces propriétés sont utilisées uniquement pour la conversion des métadonnées du serveur de Rights Management de médias Flash 1.x. Après avoir modifié les valeurs de ce fichier de propriétés, pour que les modifications prennent effet, redémarrez le serveur de licences.
