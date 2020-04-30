---
description: Vous pouvez invoquer la logique d’autorisation personnalisée lors de l’acquisition d’une licence pour décider si une licence doit être délivrée au client requérant.
seo-description: Vous pouvez invoquer la logique d’autorisation personnalisée lors de l’acquisition d’une licence pour décider si une licence doit être délivrée au client requérant.
seo-title: Extensions d’autorisation personnalisées
title: Extensions d’autorisation personnalisées
uuid: 588b05e5-3402-4586-bbd4-58b7e9a58ee4
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Extensions d’autorisation personnalisées{#custom-authorization-extensions}

Vous pouvez invoquer la logique d’autorisation personnalisée lors de l’acquisition d’une licence pour décider si une licence doit être délivrée au client requérant.

Si vous souhaitez mettre en oeuvre votre propre extension d’autorisation client, vous devez d’abord examiner l’ [!DNL SampleAuthorizer.java] exemple de code qui se trouve dans le répertoire samples. La version compilée de cet exemple se trouve dans [!DNL flashaccess-license-server-ext-sample.jar].

Si vous souhaitez créer votre propre extension, vous devez implémenter l&#39; `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` interface et vous assurer que [!DNL flashaccess-license-server-exts.jar] et [!DNL commons-logging.jar] se trouvent dans le chemin de génération (vous devez également le faire si vous utilisez certains champs dans [!DNL adobe-flashaccess-sdk.jar] `IMessageFacade`).

Si vous souhaitez déployer votre extension, vous devez copier les fichiers jar ou class dans *LicenseServer.ConfigRoot*[!DNL /flashaccessserver/libs].

Si vous souhaitez mettre à jour les fichiers jar ou class, vous devez redémarrer le serveur pour que la version mise à jour puisse être utilisée. Vous devez également ajouter le nom de la classe d&#39;ordonnateur au fichier de configuration du client.
