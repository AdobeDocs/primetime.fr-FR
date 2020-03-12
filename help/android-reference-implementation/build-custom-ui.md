---
description: Vous pouvez facilement créer une interface utilisateur personnalisée basée sur la structure d’implémentation de référence.
seo-description: Vous pouvez facilement créer une interface utilisateur personnalisée basée sur la structure d’implémentation de référence.
seo-title: Création d’une interface utilisateur personnalisée
title: Création d’une interface utilisateur personnalisée
uuid: b785f6a4-3ef8-4f7a-a087-0d6551da9750
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Création d’une interface utilisateur personnalisée {#build-a-custom-user-interface}

Vous pouvez créer une interface utilisateur personnalisée basée sur la structure d’implémentation de référence.

Les composants de l’interface utilisateur des fonctionnalités suivantes sont déjà intégrés :

* Publicités cliquables
* Incrustations publicitaires
* Audio à liaison tardive
* Sous-titres
* Écouteurs pour tous les composants ci-dessus

1. Modifiez le [!DNL PlayerFragment.java] fichier pour initialiser les composants de l’interface utilisateur que vous souhaitez utiliser dans votre lecteur.

1. Modifiez le [!DNL res/player/player_fragment.xml] fichier pour personnaliser l’interface utilisateur.
1. Créez le projet.

>[!NOTE]
>
>Pour modifier l’interface utilisateur de la barre de recherche, vous pouvez modifier la classe MarkableSeekBar. La classe [MarkableSeekBar](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/ui/player/MarkableSeekBar.html) gère le curseur, le pouce du curseur, le marqueur d’annonce, les marqueurs de repère, la plage de tampons et les arrière-plans de la plage de recherche.