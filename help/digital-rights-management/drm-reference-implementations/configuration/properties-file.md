---
description: 'null'
seo-description: 'null'
seo-title: Fichier de propriétés du serveur de licences
title: Fichier de propriétés du serveur de licences
uuid: 5e94ed1f-1dbf-4506-a097-183fcd5d25ef
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Fichier de propriétés du serveur de licences{#license-server-properties-file}

Le serveur de licences référence les propriétés définies dans le fichier [!DNL flashaccess-refimpl.properties]. Vous pouvez vous reporter directement à ce fichier pour obtenir des informations détaillées sur des valeurs spécifiques et pour obtenir des informations sur l’utilisation de chaque propriété. Un exemple fonctionnel complet est fourni dans le répertoire [!DNL resources] de l&#39;implémentation de référence ( `([DRM SDK DVD]\Reference Implementation\Server\Reference Implementation Server\resources/).`).

**Informations d&#39;identification**  : le fichier de propriétés contient des paramètres pour l&#39;emplacement des informations d&#39;identification que l&#39;Adobe vous envoie. Vous pouvez spécifier ces informations d’identification dans un fichier [!DNL .pfx] avec un mot de passe ou fournir un alias et un mot de passe pour les informations d’identification stockées sur un HSM. Vous devez au moins configurer les propriétés liées aux informations d&#39;identification de transport et aux informations d&#39;identification du serveur de licences. Spécifiez l’emplacement de vos fichiers d’informations d’identification par rapport au répertoire que vous spécifiez dans la propriété `config.resourcesDirectory`.

**Flash Media Rights Management Server**  - Le  `flashaccess-refimpl.properties` fichier comprend également plusieurs propriétés liées au contenu d’assemblage. Ces propriétés sont utilisées uniquement pour la conversion des métadonnées de Flash Media Rights Management Server 1.x. Après avoir modifié les valeurs de ce fichier de propriétés, pour que les modifications prennent effet, redémarrez le serveur de licences.
