---
description: 'null'
seo-description: 'null'
seo-title: Fichier de propriétés du serveur de licences
title: Fichier de propriétés du serveur de licences
uuid: 5e94ed1f-1dbf-4506-a097-183fcd5d25ef
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Fichier de propriétés du serveur de licences{#license-server-properties-file}

Le serveur de licences référence les propriétés définies dans le [!DNL flashaccess-refimpl.properties] fichier. Vous pouvez vous référer directement à ce fichier pour plus d’informations sur des valeurs spécifiques et sur l’utilisation de chaque propriété. Un exemple fonctionnel complet est fourni dans le [!DNL resources] répertoire de l’implémentation de référence ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources/).`).

**Informations d’identification** : le fichier de propriétés comprend des paramètres pour l’emplacement des informations d’identification qu’Adobe vous envoie. Vous pouvez spécifier ces informations d’identification dans un [!DNL .pfx] fichier avec un mot de passe ou fournir un alias et un mot de passe pour les informations d’identification stockées sur un HSM. Vous devez au moins configurer les propriétés liées aux informations d’identification de transport et aux informations d’identification du serveur de licences. Spécifiez l’emplacement de vos fichiers d’informations d’identification par rapport au répertoire que vous spécifiez dans la `config.resourcesDirectory` propriété.

**Flash Media Rights Management Server** - Le `flashaccess-refimpl.properties` fichier comprend également plusieurs propriétés liées à l’assemblage de contenu. Ces propriétés sont utilisées uniquement pour la conversion des métadonnées Flash Media Rights Management Server 1.x. Après avoir modifié les valeurs de ce fichier de propriétés, redémarrez le serveur de licences pour que les modifications prennent effet.
