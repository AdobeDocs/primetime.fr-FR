---
title: Extensions d’autorisation personnalisées
description: La logique d’autorisation personnalisée peut être invoquée lors de l’acquisition d’une licence afin de déterminer si une licence doit être délivrée au client requérant.
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---


# Extensions d&#39;autorisation personnalisée {#custom-authorization-extensions}

La logique d’autorisation personnalisée peut être invoquée lors de l’acquisition d’une licence afin de déterminer si une licence doit être délivrée au client requérant.

Pour mettre en oeuvre votre propre extension d’autorisation client, consultez d’abord l’exemple de code [!DNL SampleAuthorizer.java] situé dans le répertoire samples (la version compilée de cet exemple se trouve dans flashaccess-license-server-ext-sample.jar).

Pour créer votre propre extension, implémentez l&#39;interface `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` et assurez-vous que `flashaccess-license-server-exts.jar` et `commons-logging.jar` se trouvent sur le chemin de génération `adobe-flashaccess-sdk.jar` si vous utilisez certains champs dans `IMessageFacade`). Pour déployer votre extension, copiez vos fichiers jar ou de classe dans *LicenseServer.ConfigRoot* `/flashaccessserver/libs`. Si vous devez mettre à jour les fichiers jar ou class, le serveur doit être redémarré avant que la version mise à jour ne soit utilisée. Vous devez également ajouter le nom de la classe d&#39;ordonnateur au fichier de configuration du client.
