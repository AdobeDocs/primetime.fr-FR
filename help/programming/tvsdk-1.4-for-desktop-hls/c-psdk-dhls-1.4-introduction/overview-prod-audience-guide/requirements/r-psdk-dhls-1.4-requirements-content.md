---
description: Vérifiez les restrictions et les exigences relatives aux flux et aux listes de lecture (manifestes), y compris les clés de chiffrement DRM.
title: Exigences en matière de contenu et de manifeste
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---


# Exigences en matière de contenu et de manifeste {#content-and-manifest-requirements}

Vérifiez les restrictions et les exigences relatives aux flux et aux listes de lecture (manifestes), y compris les clés de chiffrement DRM.

| Incluez et définissez la propriété `RESOLUTION` pour chaque flux ABR dans le fichier manifeste. Vous devez utiliser le Flash Player 14 ou une version ultérieure. |
|---|
| Si le flux protégé par DRM est à débit multiple (MBR), la clé de chiffrement DRM utilisée pour le MBR doit être identique à la clé utilisée dans tous les flux de débit binaire. |
| Doit avoir les mêmes rendus de débit que les rendus du contenu principal. |