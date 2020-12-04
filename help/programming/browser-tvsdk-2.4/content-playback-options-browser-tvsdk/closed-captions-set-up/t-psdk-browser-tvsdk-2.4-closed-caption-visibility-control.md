---
description: Vous pouvez contrôler la visibilité des sous-titres fermés. Lorsque la visibilité est activée, la piste sélectionnée s’affiche.
seo-description: Vous pouvez contrôler la visibilité des sous-titres fermés. Lorsque la visibilité est activée, la piste sélectionnée s’affiche.
seo-title: Contrôler la visibilité des sous-titres
title: Contrôler la visibilité des sous-titres
uuid: b161a729-73f3-4019-a95e-013b42779842
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 0%

---


# Contrôler la visibilité de la légende fermée{#control-closed-caption-visibility}

Vous pouvez contrôler la visibilité des sous-titres fermés. Lorsque la visibilité est activée, la piste sélectionnée s’affiche.

>[!TIP]
>
>Si vous modifiez la piste actuelle, le paramètre de visibilité reste le même.

Si le texte de sous-titrage s’affiche lorsque le lecteur passe en mode de recherche, le texte ne s’affiche plus une fois la recherche terminée. Au lieu de cela, après quelques secondes, le navigateur TVSDK affiche le texte de sous-titrage suivant dans la vidéo après la position de fin de la recherche.

>[!TIP]
>
>Les valeurs de visibilité des sous-titres fermés sont contrôlées avec `MediaPlayer.VISIBLE` et `MediaPlayer.INVISIBLE`.

1. Utilisez la propriété `MediaPlayer.ccVisibility` pour accéder au paramètre de visibilité actuel des sous-titres fermés.

