---
description: Vous pouvez facilement créer une interface utilisateur personnalisée basée sur la structure d’implémentation de référence.
title: Création d’une interface utilisateur personnalisée
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Création d’une interface utilisateur personnalisée {#build-a-custom-user-interface}

Vous pouvez créer une interface utilisateur personnalisée basée sur la structure d’implémentation de référence.

Les composants de l’interface utilisateur des fonctionnalités suivantes sont déjà intégrés :

* Publicités cliquables
* Superpositions publicitaires
* Liaison audio tardive
* Sous-titres codés
* Les écouteurs pour tous les composants ci-dessus

1. Modifiez la variable [!DNL PlayerFragment.java] pour initialiser les composants de l’interface utilisateur que vous souhaitez utiliser dans votre lecteur.

1. Modifiez la variable [!DNL res/player/player_fragment.xml] pour personnaliser l’interface utilisateur.
1. Créez le projet.

>[!NOTE]
>
>Pour apporter des modifications à l’interface utilisateur de la barre de recherche, vous pouvez modifier la classe MarkableSeekBar . La variable [MarkableSeekBar](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/MarkableSeekBar.html) gère le curseur, le pouce du curseur, le marqueur publicitaire, les marqueurs de repère, la plage de mémoire tampon et les arrière-plans de la plage de recherche.
