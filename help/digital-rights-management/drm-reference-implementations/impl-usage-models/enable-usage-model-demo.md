---
seo-title: Activer la démonstration du modèle d’utilisation
title: Activer la démonstration du modèle d’utilisation
uuid: 43930ebb-e936-4f48-990d-7ad19992e326
translation-type: tm+mt
source-git-commit: 6e949c2f88deef88f0d0ac95b18c006da1c89d2f

---


# Activer la démonstration du modèle d’utilisation{#enable-the-usage-model-demo}

1. Spécifiez la propriété personnalisée `RI_UsageModelDemo=true` au moment de l’assemblage.

   Si vous assemblez du contenu à l’aide de l’outil de ligne de commande Media Packager, saisissez :

   ```
   java -jar AdobeMediaPackager.jar [<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true
   ```

>[!NOTE] {class=&quot;- rubrique/note &quot;}
>
>Si vous n’activez pas le mode de démonstration facultatif au moment de la création du pack, le serveur de licences émet une licence basée sur la première stratégie DRM valide qu’il traite.

