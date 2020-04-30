---
description: Vous pouvez contrôler la visibilité des sous-titres fermés. Lorsque la visibilité est activée, la piste sélectionnée s’affiche. Si vous modifiez la piste actuelle, le paramètre de visibilité reste le même.
seo-description: Vous pouvez contrôler la visibilité des sous-titres fermés. Lorsque la visibilité est activée, la piste sélectionnée s’affiche. Si vous modifiez la piste actuelle, le paramètre de visibilité reste le même.
seo-title: Contrôler la visibilité des sous-titres
title: Contrôler la visibilité des sous-titres
uuid: b9d48d70-2554-4948-8654-fa45093c3782
translation-type: tm+mt
source-git-commit: ''

---


# Présentation {#control-closed-caption-visibility-overview}

Vous pouvez contrôler la visibilité des sous-titres fermés. Lorsque la visibilité est activée, la piste sélectionnée s’affiche. Si vous modifiez la piste actuelle, le paramètre de visibilité reste le même.

>[!TIP]
>
>Si le texte de sous-titrage s’affiche lorsque le lecteur passe en mode de recherche, le texte ne s’affiche plus une fois la recherche terminée. Au lieu de cela, après quelques secondes, TVSDK affiche le texte de sous-titrage suivant dans la vidéo après la position de fin de la recherche.
>
>Les valeurs de visibilité des sous-titres fermés sont définies dans `MediaPlayer.Visibility`. >
>
```java>
>enum Visibility {  
>       VISIBLE,  
>       INVISIBLE 
>}
>```>



1. Attendez que le `MediaPlayer` soit au moins dans l’état PRÉPARÉ.

   Pour plus d’informations, voir ui-state-ready-wait-for.
1. Pour obtenir le paramètre de visibilité actuel pour les légendes fermées, utilisez la méthode getter dans `MediaPlayer`, qui renvoie une valeur de visibilité.

   ```java
   MediaPlayer.Visibility getCCVisibility() throws MediaPlayerException;
   ```

1. Pour modifier la visibilité des légendes fermées, utilisez la méthode setter, en transmettant une valeur de visibilité de `MediaPlayer.Visibility`.

   Par exemple :

   ```java
   mediaPlayer.setCCVisibility(MediaPlayer.Visibility visibility);
   ```

