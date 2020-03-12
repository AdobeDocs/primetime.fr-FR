---
seo-title: Extensions d’autorisation personnalisées
title: Extensions d’autorisation personnalisées
description: La logique d’autorisation personnalisée peut être invoquée lors de l’acquisition d’une licence afin de déterminer si une licence doit être délivrée au client demandeur.
seo-description: La logique d’autorisation personnalisée peut être invoquée lors de l’acquisition d’une licence afin de déterminer si une licence doit être délivrée au client demandeur.
uuid: fb40db6f-30aa-46e3-9eeb-faff3cfedab1
translation-type: tm+mt
source-git-commit: fe9493d610bc6fb97d30351c707b73cda92c67a0

---


# Extensions d’autorisation personnalisées {#custom-authorization-extensions}

La logique d’autorisation personnalisée peut être invoquée lors de l’acquisition d’une licence afin de déterminer si une licence doit être délivrée au client demandeur.

Pour mettre en oeuvre votre propre extension d’autorisation client, examinez d’abord l’exemple de code situé dans le répertoire samples (la version compilée de cet exemple se trouve dans flashaccess-license-server-ext-sample.jar). [!DNL SampleAuthorizer.java]

Pour créer votre propre extension, implémentez l’ `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` interface et assurez-vous que `flashaccess-license-server-exts.jar` et `commons-logging.jar` que le chemin de génération doit également se trouver sur le chemin de génération si vous utilisez certains champs dans `adobe-flashaccess-sdk.jar` `IMessageFacade`). Pour déployer votre extension, copiez vos fichiers JAR ou de classe dans *LicenseServer.ConfigRoot*`/flashaccessserver/libs`. Si vous devez mettre à jour les fichiers JAR ou de classe, le serveur doit être redémarré avant que la version mise à jour ne soit utilisée. Vous devez également ajouter le nom de la classe d’auteur au fichier de configuration du client.
