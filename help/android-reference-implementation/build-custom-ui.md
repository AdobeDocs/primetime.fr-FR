---
description: Vous pouvez facilement créer une interface utilisateur personnalisée basée sur la structure d’implémentation de référence.
title: Création d’une interface utilisateur personnalisée
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Créer une interface utilisateur personnalisée {#build-a-custom-user-interface}

Vous pouvez créer une interface utilisateur personnalisée basée sur la structure d’implémentation de référence.

Les composants de l’interface utilisateur des fonctionnalités suivantes sont déjà intégrés :

* Publicités cliquables
* Incrustations publicitaires
* Audio à liaison tardive
* Sous-titres
* Écouteurs pour tous les composants ci-dessus

1. Modifiez le fichier [!DNL PlayerFragment.java] pour initialiser les composants de l&#39;interface utilisateur que vous souhaitez utiliser dans votre lecteur.

1. Modifiez le fichier [!DNL res/player/player_fragment.xml] pour personnaliser l’interface utilisateur.
1. Créez le projet.

>[!NOTE]
>
>Pour modifier l&#39;interface utilisateur de la barre de recherche, vous pouvez modifier la classe MarkableSeekBar. La classe [MarkableSeekBar](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/MarkableSeekBar.html) gère le curseur, le pouce du curseur, le marqueur publicitaire, les marqueurs de repère, la plage de tampons et les arrière-plans de la plage de recherche.