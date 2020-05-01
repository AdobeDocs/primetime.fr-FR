---
description: Vous pouvez configurer les noms de balises personnalisées dans TVSDK globalement avec la classe PTSDKConfig.
seo-description: Vous pouvez configurer les noms de balises personnalisées dans TVSDK globalement avec la classe PTSDKConfig.
seo-title: Config des méthodes de classe pour les balises
title: Config des méthodes de classe pour les balises
uuid: 27f1df0a-bbd3-4d80-820e-b659f2f33069
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Config des méthodes de classe pour les balises {#config-class-methods-for-tags}

Vous pouvez configurer les noms de balises personnalisées dans TVSDK globalement avec la classe PTSDKConfig.

TVSDK applique automatiquement la configuration globale à tout flux média qui ne spécifie pas de configuration spécifique au flux.

`PTSDKConfig` expose les méthodes suivantes pour gérer les balises personnalisées :

| **S’abonner à des balises personnalisées spécifiques** |  |
|---|---|
| `subscribedTags` | Récupère la liste actuelle des balises abonnées. |
| `setSubscribedTags` | Définit la liste des balises abonnées qui seront exposées à l’application. |
| **Personnaliser les balises publicitaires utilisées par le détecteur d&#39;opportunités par défaut** |
| `adTags` | Récupère la liste actuelle des balises publicitaires. |
| `setAdTags` | Définit la liste des balises publicitaires qui seront utilisées par le générateur d’opportunités par défaut. |


Souvenez-vous des points suivants :

* Les méthodes setter n’autorisent pas le paramètre de balises à contenir des valeurs nulles.
* Le nom de la balise personnalisée doit contenir le préfixe #.

   Par exemple, #EXT-X-ASSET est un nom de balise personnalisé correct, mais EXT-X-ASSET est incorrect.
* Vous ne pouvez pas modifier la configuration après le chargement du flux média.