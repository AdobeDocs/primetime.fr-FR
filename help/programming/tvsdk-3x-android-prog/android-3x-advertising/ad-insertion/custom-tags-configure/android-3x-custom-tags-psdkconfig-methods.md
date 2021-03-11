---
description: Vous pouvez configurer globalement les noms de balises personnalisées dans TVSDK avec la classe MediaPlayerItemConfig.
title: Config des méthodes de classe pour les balises
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---


# Configurez les méthodes de classe pour les balises {#config-class-methods-for-tags}

Vous pouvez configurer globalement les noms de balises personnalisées dans TVSDK avec la classe MediaPlayerItemConfig.

TVSDK applique automatiquement la configuration globale à tout flux média qui ne spécifie aucune configuration spécifique au flux.

`MediaPlayerItemConfig` expose les méthodes suivantes pour gérer les balises personnalisées :

**S’abonner à des balises personnalisées spécifiques**

| <b>Méthode</b> | <b>Description</b> |
|--- |--- |
| `public final String[] getSubscribedTags` | Récupère la liste actuelle des balises abonnées. |
| `public final void setSubscribedTags(String[] tags);` | Définit la liste des balises abonnées qui seront exposées à l’application.  Votre application est également automatiquement abonnée à toutes les balises transmises par `setAdTags`. |

**Personnaliser les balises publicitaires utilisées par le détecteur d&#39;opportunités par défaut**

| <b>Méthode</b> | <b>Description</b> |
|--- |--- |
| `public final String[] getAdTags;` | Récupère la liste actuelle des balises publicitaires. |
| `public final void setAdTags(String[] tags);` | Définit la liste des balises publicitaires qui seront utilisées par le générateur d’opportunités par défaut. |

Souvenez-vous des points suivants :

* Les méthodes setter n’autorisent pas le paramètre de balises à contenir des valeurs nulles.

   S’il est rencontré, TVSDK lance un `IllegalArgumentException`.
* Le nom de la balise personnalisée doit contenir le préfixe `#`.

   Par exemple, `#EXT-X-ASSET` est un nom de balise personnalisé correct, mais `EXT-X-ASSET` est incorrect.

* Vous ne pouvez pas modifier la configuration après le chargement du flux média.