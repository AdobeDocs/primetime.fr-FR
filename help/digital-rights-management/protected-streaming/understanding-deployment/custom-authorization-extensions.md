---
description: Vous pouvez appeler une logique d’autorisation personnalisée lors de l’acquisition d’une licence pour décider si une licence doit être émise au client qui la demande.
title: Extensions d’autorisation personnalisées
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Extensions d’autorisation personnalisées{#custom-authorization-extensions}

Vous pouvez appeler une logique d’autorisation personnalisée lors de l’acquisition d’une licence pour décider si une licence doit être émise au client qui la demande.

Si vous souhaitez mettre en oeuvre votre propre extension d’autorisation client, vous devez d’abord consulter la section [!DNL SampleAuthorizer.java] exemple de code situé dans le répertoire samples. La version compilée de cet exemple se trouve dans la section [!DNL flashaccess-license-server-ext-sample.jar].

Si vous souhaitez créer votre propre extension, vous devez mettre en oeuvre la variable `com.adobe.flashaccess.server.license.extension.auth.IAuthorizer` et assurez-vous de [!DNL flashaccess-license-server-exts.jar] et [!DNL commons-logging.jar] se trouvent dans le chemin de génération ( [!DNL adobe-flashaccess-sdk.jar] doit également se trouver dans le chemin de création si vous utilisez certains champs dans `IMessageFacade`).

Si vous souhaitez déployer votre extension, vous devez copier les fichiers jar ou de classe dans *LicenseServer.ConfigRoot* [!DNL /flashaccessserver/libs].

Si vous souhaitez mettre à jour les fichiers jar ou de classe, vous devez redémarrer le serveur avant que la version mise à jour puisse être utilisée. Vous devez également ajouter le nom de classe de l’agent d’autorisation au fichier de configuration du client.
