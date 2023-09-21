---
title: Fichiers de propriétés du serveur
description: Fichiers de propriétés du serveur
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# Fichiers de propriétés du serveur {#server-properties-files}

Le serveur nécessite deux fichiers de configuration, un pour le serveur de licences et un autre pour le service de package. Les deux fichiers doivent être placés sur le chemin d’accès aux classes. Les fichiers de propriétés contiennent l’emplacement des informations d’identification émises par Adobe. Ces informations d’identification peuvent être spécifiées sous la forme d’un fichier .pfx et d’un mot de passe ou en fournissant un alias et un mot de passe pour les informations d’identification stockées sur un HSM.

Reportez-vous aux fichiers de propriétés pour plus d’informations sur les valeurs spécifiques et l’utilisation de chaque paramètre. Vous trouverez des exemples de fichiers de propriétés dans le répertoire &quot;resources&quot; de l’implémentation de référence (Reference Implementation\Server\resources).

Pour garantir la sécurité du mot de passe de vos informations d’identification, un outil est fourni (ScrambleUtil.class) pour chiffrer le mot de passe avant qu’il ne soit entré dans le fichier flashaccess-refimpl.properties ou flashaccess-refimpl-packager.properties .

Pour préparer correctement le mot de passe de vos informations d’identification :

1. Accédez à [!DNL Reference Implementation\Server\refimpl\scrambler].
1. A partir de l&#39;invite de commande, saisissez la commande :

   ```
   java -classpath  
   <i class="+ topic ph hi-d="" i "="">
   path_to_adobe-flashaccess-sdk.jar.; 
        com.adobe.flashaccess.refimpl.util.ScrambleUtil " 
   <i class="+ topic ph hi-d="" i "="">
   your_pfx_password" 
   </i class="+ topic> 
   </i class="+ topic>
   ```

>[!NOTE]
>
>L’exemple précédent utilise un point-virgule (;) comme délimiteur. Pour les plateformes autres que Microsoft Windows, utilisez un deux-points (:) comme délimiteur.

L’utilitaire génère le mot de passe chiffré que vous devez copier dans la variable [!DNL .properties] fichier .
