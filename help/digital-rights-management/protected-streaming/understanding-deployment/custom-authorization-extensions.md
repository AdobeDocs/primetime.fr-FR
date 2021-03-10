---
description: Vous pouvez invoquer la logique d’autorisation personnalisée lors de l’acquisition d’une licence pour décider si une licence doit être délivrée au client requérant.
title: Extensions d’autorisation personnalisées
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# Extensions d’autorisation personnalisées{#custom-authorization-extensions}

Vous pouvez invoquer la logique d’autorisation personnalisée lors de l’acquisition d’une licence pour décider si une licence doit être délivrée au client requérant.

Si vous souhaitez mettre en oeuvre votre propre extension d’autorisation client, vous devez d’abord consulter l’exemple de code [!DNL SampleAuthorizer.java] situé dans le répertoire samples. La version compilée de cet exemple se trouve dans [!DNL flashaccess-license-server-ext-sample.jar].

Si vous souhaitez créer votre propre extension, vous devez implémenter l&#39;interface `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` et vous assurer que [!DNL flashaccess-license-server-exts.jar] et [!DNL commons-logging.jar] se trouvent dans le chemin de génération ( [!DNL adobe-flashaccess-sdk.jar] doit également se trouver dans le chemin de génération si vous utilisez certains champs dans `IMessageFacade`).

Si vous souhaitez déployer votre extension, vous devez copier les fichiers jar ou de classe dans *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/libs].

Si vous souhaitez mettre à jour les fichiers jar ou class, vous devez redémarrer le serveur pour que la version mise à jour puisse être utilisée. Vous devez également ajouter le nom de la classe d&#39;ordonnateur au fichier de configuration du client.
