---
description: Vous pouvez contrôler la visibilité des sous-titres non intégrés. Lorsque la visibilité a été activée, le suivi actuellement sélectionné s’affiche. Si vous modifiez le suivi actuel, le paramètre de visibilité reste le même.
title: Contrôler la visibilité des sous-titres
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Présentation {#control-closed-caption-visibility-overview}

Vous pouvez contrôler la visibilité des sous-titres non intégrés. Lorsque la visibilité a été activée, le suivi actuellement sélectionné s’affiche. Si vous modifiez le suivi actuel, le paramètre de visibilité reste le même.

>[!TIP]
>
>Si le texte des sous-titres est affiché lorsque le lecteur passe en mode de recherche, le texte ne s’affiche plus une fois la recherche terminée. Au lieu de cela, au bout de quelques secondes, TVSDK affiche le texte de sous-titrage suivant dans la vidéo après la position de fin de la recherche.
>
>Les valeurs de visibilité des sous-titres sont définies dans `MediaPlayer.Visibility`.
>
>```java
>enum Visibility {  
>       VISIBLE,  
>       INVISIBLE 
>}
>```
>

1. Attendez que la variable `MediaPlayer` pour être au moins en état PRÉPARÉ .

   Pour plus d’informations, voir ui-state-ready-wait-for .
1. Pour obtenir le paramètre de visibilité actuel pour les sous-titres fermés, utilisez la méthode getter dans `MediaPlayer`, qui renvoie une valeur de visibilité.

   ```java
   MediaPlayer.Visibility getCCVisibility() throws MediaPlayerException;
   ```

1. Pour modifier la visibilité des sous-titres, utilisez la méthode setter , en transmettant une valeur de visibilité de `MediaPlayer.Visibility`.

   Par exemple :

   ```java
   mediaPlayer.setCCVisibility(MediaPlayer.Visibility visibility);
   ```
