---
description: Vous pouvez appeler la logique d’autorisation personnalisée lors de l’acquisition de la licence pour décider si une licence doit être délivrée au client demandeur.
seo-description: Vous pouvez appeler la logique d’autorisation personnalisée lors de l’acquisition de la licence pour décider si une licence doit être délivrée au client demandeur.
seo-title: Extensions d’autorisation personnalisées
title: Extensions d’autorisation personnalisées
uuid: 588b05e5-3402-4586-bbd4-58b7e9a58ee4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Extensions d’autorisation personnalisées{#custom-authorization-extensions}

Vous pouvez appeler la logique d’autorisation personnalisée lors de l’acquisition de la licence pour décider si une licence doit être délivrée au client demandeur.

Si vous souhaitez mettre en oeuvre votre propre extension d’autorisation client, vous devez d’abord consulter l’ [!DNL SampleAuthorizer.java] exemple de code qui se trouve dans le répertoire samples. La version compilée de cet exemple se trouve dans [!DNL flashaccess-license-server-ext-sample.jar].

Si vous souhaitez créer votre propre extension, vous devez mettre en oeuvre l’ `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` interface et vous assurer que [!DNL flashaccess-license-server-exts.jar] et [!DNL commons-logging.jar] se trouvent dans le chemin de génération ( [!DNL adobe-flashaccess-sdk.jar] doit également se trouver dans le chemin de génération si vous utilisez certains champs dans `IMessageFacade`).

Si vous souhaitez déployer votre extension, vous devez copier les fichiers jar ou de classe dans *LicenseServer.ConfigRoot*[!DNL /flashaccessserver/libs].

Si vous souhaitez mettre à jour les fichiers JAR ou de classe, vous devez redémarrer le serveur avant d’utiliser la version mise à jour. Vous devez également ajouter le nom de la classe d’auteur au fichier de configuration du client.
