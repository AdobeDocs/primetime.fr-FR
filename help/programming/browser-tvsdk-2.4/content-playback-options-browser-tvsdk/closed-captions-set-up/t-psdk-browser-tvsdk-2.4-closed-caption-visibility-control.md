---
description: Vous pouvez contrôler la visibilité des sous-titres non intégrés. Lorsque la visibilité est activée, le suivi actuellement sélectionné s’affiche.
title: Contrôler la visibilité des sous-titres
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---

# Contrôler la visibilité des sous-titres{#control-closed-caption-visibility}

Vous pouvez contrôler la visibilité des sous-titres non intégrés. Lorsque la visibilité est activée, le suivi actuellement sélectionné s’affiche.

>[!TIP]
>
>Si vous modifiez le suivi actuel, le paramètre de visibilité reste le même.

Si le texte des sous-titres est affiché lorsque le lecteur passe en mode de recherche, le texte ne s’affiche plus une fois la recherche terminée. Au lieu de cela, au bout de quelques secondes, le TVSDK du navigateur affiche le texte de sous-titrage suivant dans la vidéo après la position de fin de la recherche.

>[!TIP]
>
>Les valeurs de visibilité des sous-titres sont contrôlées avec `MediaPlayer.VISIBLE` et `MediaPlayer.INVISIBLE`.

1. Utilisez la variable `MediaPlayer.ccVisibility` pour accéder au paramètre de visibilité actuel pour les sous-titres fermés.
