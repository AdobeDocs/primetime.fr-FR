---
title: Activation de la démonstration du modèle d’utilisation
description: Activation de la démonstration du modèle d’utilisation
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# Activation de la démonstration du modèle d’utilisation{#enable-the-usage-model-demo}

1. Spécification de la propriété personnalisée `RI_UsageModelDemo=true` au moment de l’emballage.

   Si vous mettez en package du contenu à l’aide de l’outil de ligne de commande Media Packager, saisissez :

   ```
   java -jar AdobeMediaPackager.jar [<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true
   ```

>[!NOTE]
>
>Si vous n’activez pas le mode de démonstration facultatif au moment du conditionnement, le serveur de licences émet une licence basée sur la première stratégie DRM valide qu’il traite.
