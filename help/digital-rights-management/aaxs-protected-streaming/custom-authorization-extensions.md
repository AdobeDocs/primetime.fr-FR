---
title: Extensions d’autorisation personnalisées
description: La logique d’autorisation personnalisée peut être appelée lors de l’acquisition d’une licence pour décider si une licence doit être émise au client qui la demande.
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Extensions d’autorisation personnalisées {#custom-authorization-extensions}

La logique d’autorisation personnalisée peut être appelée lors de l’acquisition d’une licence pour décider si une licence doit être émise au client qui la demande.

Pour mettre en oeuvre votre propre extension d’autorisation client, consultez la section [!DNL SampleAuthorizer.java] exemple de code situé dans le répertoire samples (la version compilée de cet exemple se trouve dans flashaccess-license-server-ext-sample.jar).

Pour créer votre propre extension, implémentez le `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` et assurez-vous de `flashaccess-license-server-exts.jar` et `commons-logging.jar` se trouvent sur le chemin d’accès à la version `adobe-flashaccess-sdk.jar` doit également se trouver sur le chemin de génération si vous utilisez certains champs dans `IMessageFacade`). Pour déployer votre extension, copiez vos fichiers jar ou de classe dans *LicenseServer.ConfigRoot* `/flashaccessserver/libs`. Si vous devez mettre à jour les fichiers jar ou de classe, le serveur doit être redémarré avant l’utilisation de la version mise à jour. Vous devez également ajouter le nom de classe de l’agent d’autorisation au fichier de configuration du client.
