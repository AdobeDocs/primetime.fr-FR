---
description: Vous pouvez contrôler la visibilité des sous-titres fermés. Lorsque la visibilité est activée, la piste sélectionnée s’affiche. Si vous modifiez la piste actuelle, le paramètre de visibilité reste le même.
seo-description: Vous pouvez contrôler la visibilité des sous-titres fermés. Lorsque la visibilité est activée, la piste sélectionnée s’affiche. Si vous modifiez la piste actuelle, le paramètre de visibilité reste le même.
seo-title: Contrôler la visibilité des sous-titres
title: Contrôler la visibilité des sous-titres
uuid: 42913347-8158-474e-aa3c-ba4d38baba12
translation-type: tm+mt
source-git-commit: 5df9a8b98baaf1cd1803581d2b60c7ed4261a0e8
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---


# Présentation {#control-closed-caption-visibility}

Vous pouvez contrôler la visibilité des sous-titres fermés. Lorsque la visibilité est activée, la piste sélectionnée s’affiche. Si vous modifiez la piste actuelle, le paramètre de visibilité reste le même.

>[!TIP]
>
>Si le texte de sous-titrage s’affiche lorsque le lecteur passe en mode de recherche, le texte ne s’affiche plus une fois la recherche terminée. Au lieu de cela, après quelques secondes, TVSDK affiche le texte de sous-titrage suivant dans la vidéo après la position de fin de la recherche.

>[!NOTE]
>
>Les valeurs de visibilité des sous-titres fermés sont définies dans `MediaPlayer.Visibility`.
>
>
```java
>enum Visibility { 
>       VISIBLE,  
>       INVISIBLE 
>}
>```

1. Attendez que MediaPlayer ait au moins l’état PRÉPARÉ (voir [Attendre un état](../../../tvsdk-1.4-for-android/ui-configure/android-1.4-ui-state-prepared-wait-for.md)valide).
1. Pour obtenir le paramètre de visibilité actuel pour les sous-titres fermés, utilisez la méthode getter dans MediaPlayer, qui renvoie une valeur de visibilité.

   ```java
   Visibility getCCVisibility() throws IllegalStateException;
   ```

1. Pour modifier la visibilité des légendes fermées, utilisez la méthode setter, en transmettant une valeur de visibilité de `MediaPlayer.Visibility`.

   Par exemple :

   ```java
   mediaPlayer.setCCVisibility(Visibility.VISIBLE);
   ```

