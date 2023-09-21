---
description: Pour utiliser Browser TVSDK, vous devez créer et configurer un lecteur de base. Pour lire du contenu vidéo, vous pouvez créer un lecteur de base de deux manières différentes à l’aide du navigateur TVSDK ou de l’interface utilisateur.
title: Lecteur de base
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# Présentation {#basic-player-overview}

Pour utiliser Browser TVSDK, vous devez créer et configurer un lecteur de base. Pour lire du contenu vidéo, vous pouvez créer un lecteur de base de deux manières : à l’aide du Browser TVSDK ou de l’interface utilisateur Framework.

## Utilisation du navigateur TVSDK {#section_4D1C6D4B3A3447DFA2AA0229E140E2D9}

Utilisez les API fournies avec le navigateur TVSDK directement pour coder votre lecteur vidéo. Le SDK vous fournit des structures et des utilitaires, ainsi qu’un lecteur de référence à partir duquel vous pouvez travailler.

>[!TIP]
>
>Pour que cela fonctionne dans un lecteur de référence, ne spécifiez aucun attribut avec `videoDiv`.

## Utilisation de la structure de l’interface utilisateur {#section_AE02384CFEF64A448C108232AB62A9FF}

Ce module est utilisé pour créer des instances du lecteur, où chaque instance est liée à un élément de modèle d’objet de document (DOM) fourni par l’appelant. Outre une instance du navigateur TVSDK, chaque instance de lecteur héberge un certain nombre de contrôles qui constituent l’interface utilisateur du lecteur.

La mise en oeuvre de chaque contrôle se compose de deux aspects :

* Un `HTMLElement`, qui est la représentation visuelle du composant à l’écran.
* A `Behavior`, qui gère la variable `HTMLElement` et fournit une API pour les interactions.

Les détails de ces contrôles sont fournis au `VideoPlayer` en utilisant un objet config, qui est transmis au lecteur lors de son instanciation. Par défaut, chaque composant forme une hiérarchie d’objets, l’élément étant fourni à l’instance du lecteur à la racine de l’arborescence. À mesure que chaque composant est créé, il est ajouté au DOM à l’emplacement approprié.

Chaque composant porte un nom, qui est sa clé dans l’objet de configuration lorsque l’objet est enregistré. La classe CSS de l’élément DOM sous-jacent est formée en tant que `vp-` préfixe ajouté au nom du composant.

Les composants peuvent être étendus ou remplacés, leur configuration peut être modifiée et les propriétés initiales définies. Cela vous permet de mieux contrôler les propriétés de l’API, le nom de classe CSS et, éventuellement, les aspects de l’implémentation du composant. Ces options peuvent être utilisées pour personnaliser la fonctionnalité et autoriser plusieurs instances d’un composant qui peuvent être stylisées ou configurées individuellement.

Toutes les instances de composant sont accessibles à l’aide de la fonction `.behaviors` . Les instances peuvent être activées et désactivées, affichées ou masquées. Mais une fois les instances créées, ces instances ne peuvent pas être supprimées.
