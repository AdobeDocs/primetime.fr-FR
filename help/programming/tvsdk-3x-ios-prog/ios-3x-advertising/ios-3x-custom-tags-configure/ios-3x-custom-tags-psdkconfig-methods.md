---
description: Vous pouvez configurer globalement les noms de balises personnalisés dans TVSDK avec la classe PTSDKConfig .
title: Méthodes de classe de configuration pour les balises
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Méthodes de classe de configuration pour les balises {#config-class-methods-for-tags}

Vous pouvez configurer globalement les noms de balises personnalisés dans TVSDK avec la classe PTSDKConfig .

TVSDK applique automatiquement la configuration globale à tout flux multimédia qui ne spécifie aucune configuration spécifique au flux.

`PTSDKConfig` expose ces méthodes pour gérer les balises personnalisées :

| **Abonnement à des balises personnalisées spécifiques** |  |
|---|---|
| `subscribedTags` | Récupère la liste actuelle des balises abonnées. |
| `setSubscribedTags` | Définit la liste des balises abonnées qui seront exposées à l’application. |
| **Personnaliser les balises d’annonce utilisées par le détecteur d’opportunités par défaut** |
| `adTags` | Récupère la liste actuelle des balises publicitaires. |
| `setAdTags` | Définit la liste des balises d’annonce qui seront utilisées par le générateur d’opportunités par défaut. |


Gardez à l’esprit les éléments suivants :

* Les méthodes setter ne permettent pas au paramètre tags de contenir des valeurs null.
* Le nom de la balise personnalisée doit contenir le préfixe # .

  Par exemple, #EXT-X-ASSET est un nom de balise personnalisé correct, mais EXT-X-ASSET est incorrect.
* Vous ne pouvez pas modifier la configuration une fois le flux multimédia chargé.
