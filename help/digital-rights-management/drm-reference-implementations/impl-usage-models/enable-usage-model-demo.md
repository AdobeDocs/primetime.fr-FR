---
seo-title: Activer la démonstration du modèle d’utilisation
title: Activer la démonstration du modèle d’utilisation
uuid: 43930ebb-e936-4f48-990d-7ad19992e326
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# Activez le modèle d’utilisation demo{#enable-the-usage-model-demo}

1. Spécifiez la propriété personnalisée `RI_UsageModelDemo=true` au moment du conditionnement.

   Si vous assemblez du contenu à l’aide de l’outil de ligne de commande Media Packager, saisissez :

   ```
   java -jar AdobeMediaPackager.jar [<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true
   ```

>[!NOTE]
>
>Si vous n’activez pas le mode de démonstration facultatif au moment de la création du pack, le serveur de licences délivre une licence basée sur la première stratégie DRM valide qu’il traite.

