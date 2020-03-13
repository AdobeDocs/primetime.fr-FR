---
seo-title: Activer la démonstration du modèle d’utilisation
title: Activer la démonstration du modèle d’utilisation
uuid: 43930ebb-e936-4f48-990d-7ad19992e326
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Activer la démonstration du modèle d’utilisation{#enable-the-usage-model-demo}

1. Spécifiez la propriété personnalisée `RI_UsageModelDemo=true` au moment de l’assemblage.

   Si vous assemblez du contenu à l’aide de l’outil de ligne de commande Media Packager, saisissez :

   ```
   java -jar AdobeMediaPackager.jar [
   
<i>source_file</i>] [dest_file<i></i>] -k RI_UsageModelDemo=true

```
>[!NOTE] {class="- topic/note "}
>
>If you do not activate the optional demo mode at packaging time, the license server issues a license based on the first valid DRM policy it processes.

