---
title: Activer la démonstration du modèle d’utilisation
description: Activer la démonstration du modèle d’utilisation
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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

