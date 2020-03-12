---
description: Vérifiez les restrictions et les exigences pour les flux et les listes de lecture (manifestes), y compris les clés de chiffrement DRM.
seo-description: Vérifiez les restrictions et les exigences pour les flux et les listes de lecture (manifestes), y compris les clés de chiffrement DRM.
seo-title: Exigences en matière de contenu et de manifeste
title: Exigences en matière de contenu et de manifeste
uuid: 53cc570a-be33-4488-95e8-43f91b559b13
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d

---


# Exigences en matière de contenu et de manifeste {#content-and-manifest-requirements}

Vérifiez les restrictions et les exigences pour les flux et les listes de lecture (manifestes), y compris les clés de chiffrement DRM.

| Incluez et définissez la `RESOLUTION` propriété de chaque flux ABR dans le fichier manifeste. Vous devez utiliser Flash Player 14 ou version ultérieure. |
|---|
| Si le flux protégé par DRM est à débit multiple (MBR), la clé de chiffrement DRM utilisée pour le MBR doit être la même que la clé utilisée dans tous les flux de débit binaire. |
| Doit avoir les mêmes rendus de débit binaire que les rendus du contenu principal. |