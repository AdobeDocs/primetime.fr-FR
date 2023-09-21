---
description: Vous pouvez configurer globalement les noms de balise personnalisés dans TVSDK à l’aide de la classe MediaPlayerItemConfig .
title: Méthodes de classe de configuration pour les balises
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Méthodes de classe de configuration pour les balises {#config-class-methods-for-tags}

Vous pouvez configurer globalement les noms de balise personnalisés dans TVSDK à l’aide de la classe MediaPlayerItemConfig .

TVSDK applique automatiquement la configuration globale à tout flux multimédia qui ne spécifie aucune configuration spécifique au flux.

`MediaPlayerItemConfig` expose ces méthodes pour gérer les balises personnalisées :

**Abonnement à des balises personnalisées spécifiques**

| <b>Méthode</b> | <b>Description</b> |
|--- |--- |
| `public final String[] getSubscribedTags` | Récupère la liste actuelle des balises abonnées. |
| `public final void setSubscribedTags(String[] tags);` | Définit la liste des balises abonnées qui seront exposées à l’application.  Votre application est également automatiquement inscrite à toutes les balises transmises par le biais de `setAdTags`. |

**Personnaliser les balises d’annonce utilisées par le détecteur d’opportunités par défaut**

| <b>Méthode</b> | <b>Description</b> |
|--- |--- |
| `public final String[] getAdTags;` | Récupère la liste actuelle des balises publicitaires. |
| `public final void setAdTags(String[] tags);` | Définit la liste des balises d’annonce qui seront utilisées par le générateur d’opportunités par défaut. |

Gardez à l’esprit les éléments suivants :

* Les méthodes setter ne permettent pas au paramètre tags de contenir des valeurs null.

  En cas de problème, TVSDK renvoie une `IllegalArgumentException`.
* Le nom de la balise personnalisée doit contenir la variable `#` préfixe.

  Par exemple : `#EXT-X-ASSET` est un nom de balise personnalisé correct, mais `EXT-X-ASSET` est incorrect.

* Vous ne pouvez pas modifier la configuration une fois le flux multimédia chargé.
