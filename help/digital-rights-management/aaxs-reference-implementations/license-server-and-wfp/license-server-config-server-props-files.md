---
seo-title: Fichiers de propriétés du serveur
title: Fichiers de propriétés du serveur
uuid: 3d3a0ee3-009f-4d62-9587-7e487ecdcafd
translation-type: tm+mt
source-git-commit: 4102780d0c7d0b96d120c1c2b3d14c47bc1b0e6f

---


# Fichiers de propriétés du serveur {#server-properties-files}

Le serveur requiert deux fichiers de configuration, un pour le serveur de licences et un pour le gestionnaire de package. Les deux fichiers doivent être placés sur le chemin de classe. Les fichiers de propriétés contiennent l’emplacement des informations d’identification émises par Adobe. Ces informations d’identification peuvent être spécifiées sous la forme d’un fichier .pfx et d’un mot de passe ou en fournissant un alias et un mot de passe pour les informations d’identification stockées sur un HSM.

Consultez les fichiers de propriétés pour plus d&#39;informations sur les valeurs spécifiques et l&#39;utilisation de chaque paramètre. Vous trouverez des exemples de fichiers de propriétés dans le répertoire &quot;resources&quot; de l’implémentation de référence (Référence Implementation\Server\resources).

Pour garantir la sécurité du mot de passe de vos informations d’identification, un outil est fourni (ScrambleUtil.class) pour chiffrer le mot de passe avant qu’il ne soit entré dans le fichier flashaccess-refimpl.properties ou flashaccess-refimpl-packager.properties.

Pour préparer correctement le mot de passe de vos informations d’identification :

1. Allez-y [!DNL Reference Implementation\Server\refimpl\scrambler].
1. Dans l’invite de commande, saisissez la commande suivante :

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

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>L’exemple précédent utilise un point-virgule (;) comme séparateur. Pour les plateformes autres que Microsoft Windows, utilisez un deux-points (:) comme délimiteur.

L’utilitaire génère le mot de passe chiffré que vous devez copier dans le [!DNL .properties] fichier.
