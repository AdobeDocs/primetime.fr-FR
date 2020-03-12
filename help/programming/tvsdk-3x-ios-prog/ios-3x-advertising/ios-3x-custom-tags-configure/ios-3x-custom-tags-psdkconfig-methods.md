---
description: Vous pouvez configurer les noms de balises personnalisées dans TVSDK globalement avec la classe PTSDKConfig.
seo-description: Vous pouvez configurer les noms de balises personnalisées dans TVSDK globalement avec la classe PTSDKConfig.
seo-title: Méthodes de classe Config pour les balises
title: Méthodes de classe Config pour les balises
uuid: 27f1df0a-bbd3-4d80-820e-b659f2f33069
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# Méthodes de classe Config pour les balises {#config-class-methods-for-tags}

Vous pouvez configurer les noms de balises personnalisées dans TVSDK globalement avec la classe PTSDKConfig.

TVSDK applique automatiquement la configuration globale à tout flux média qui ne spécifie aucune configuration spécifique au flux.

`PTSDKConfig` expose les méthodes suivantes pour gérer les balises personnalisées :

| **S’abonner à des balises personnalisées spécifiques** |  |
|---|---|
| `subscribedTags` | Récupère le  actuel des balises abonnées. |
| `setSubscribedTags` | Définit le  des balises abonnées qui seront exposées à l’application. |
| **Personnaliser les balises publicitaires utilisées par le détecteur d&#39;opportunités par défaut** |
| `adTags` | Récupère le  actuel des balises publicitaires. |
| `setAdTags` | Définit le  des balises publicitaires qui seront utilisées par le générateur d’opportunités par défaut. |


Tenez compte des points suivants :

* Les méthodes setter ne permettent pas au paramètre de balise de contenir des valeurs null.
* Le nom de la balise personnalisée doit contenir le préfixe #.

   Par exemple, #EXT-X-ASSET est un nom de balise personnalisé correct, mais EXT-X-ASSET est incorrect.
* Vous ne pouvez pas modifier la configuration une fois le flux média chargé.