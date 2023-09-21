---
description: Vérifiez les restrictions et les exigences pour les flux et les listes de lecture (manifestes), y compris les clés de chiffrement DRM.
title: Exigences en matière de contenu et de manifeste
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---

# Exigences en matière de contenu et de manifeste {#content-and-manifest-requirements}

Vérifiez les restrictions et les exigences pour les flux et les listes de lecture (manifestes), y compris les clés de chiffrement DRM.

| Inclure et définir la variable `RESOLUTION` pour chaque flux ABR dans le fichier de manifeste. Vous devez utiliser le Flash Player 14 ou une version ultérieure. |
|---|
| Si le flux protégé par DRM est à débit multiple (MBR), la clé de chiffrement DRM utilisée pour le MBR doit être la même que celle utilisée dans tous les flux de débit. |
| Doit comporter les mêmes rendus de débit que les rendus du contenu principal. |
