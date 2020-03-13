---
description: 'Pour utiliser le SDK Browser TVSDK, vous devez créer et configurer un lecteur de base. Pour lire du contenu vidéo, vous pouvez créer un lecteur de base de l’une ou l’autre des deux façons suivantes : le SDK du navigateur ou le framework d’interface utilisateur.'
seo-description: 'Pour utiliser le SDK Browser TVSDK, vous devez créer et configurer un lecteur de base. Pour lire du contenu vidéo, vous pouvez créer un lecteur de base de l’une ou l’autre des deux façons suivantes : le SDK du navigateur ou le framework d’interface utilisateur.'
seo-title: Lecteur de base
title: Lecteur de base
uuid: 44a27458-be12-452f-92b9-3cef79439257
translation-type: tm+mt
source-git-commit: 592245f5a7186d18dabbb5a98a468cbed7354aed

---


# Présentation {#basic-player-overview}

Pour utiliser le SDK Browser TVSDK, vous devez créer et configurer un lecteur de base. Pour lire du contenu vidéo, vous pouvez créer un lecteur de base de l’une des deux façons suivantes : à l’aide du navigateur TVSDK ou de l’interface utilisateur Framework.

## Utilisation du navigateur TVSDK {#section_4D1C6D4B3A3447DFA2AA0229E140E2D9}

Utilisez les API fournies avec le SDK du navigateur directement pour coder votre lecteur vidéo. Le SDK fournit des infrastructures et des utilitaires, ainsi qu’un lecteur de référence à partir duquel travailler.

>[!TIP]
>
>Pour voir cela fonctionner dans un lecteur de référence, ne spécifiez aucun attribut avec `videoDiv`.

## Utilisation de la structure de l’interface utilisateur {#section_AE02384CFEF64A448C108232AB62A9FF}

Ce module est utilisé pour créer des instances du lecteur, où chaque instance est liée à un élément DOM (modèle d’objet de) fourni par l’appelant. En plus d’avoir une instance du SDK du navigateur, chaque instance du lecteur héberge un certain nombre de commandes qui constituent l’interface utilisateur du lecteur.

La mise en oeuvre de chaque contrôle comporte deux aspects:

* Une `HTMLElement`, qui est la représentation visuelle du composant à l’écran
* A `Behavior`, qui gère `HTMLElement` et fournit une API pour les interactions

Les détails de ces contrôles sont fournis à la `VideoPlayer` société à l’aide d’un objet config, qui est transmis au lecteur lors de son instanciation. Par défaut, chaque composant forme une hiérarchie d’objets, l’élément étant fourni à l’instance du lecteur à la racine de l’arborescence. Chaque composant étant créé, il est ajouté au DOM à l’emplacement approprié.

Chaque composant porte un nom, qui est sa clé dans l’objet de configuration lorsque l’objet est enregistré. La classe CSS de l’élément DOM sous-jacent est formée en tant que `vp-` préfixe ajouté au nom du composant.

Les composants peuvent être étendus ou remplacés, leur configuration peut être modifiée et les propriétés initiales définies. Cela vous permet de mieux contrôler les propriétés de l’API, le nom de la classe CSS et, éventuellement, les aspects de l’implémentation du composant. Ces options peuvent être utilisées pour personnaliser la fonctionnalité et autoriser plusieurs instances d’un composant qui peuvent être définies ou configurées individuellement.

Toutes les instances de composant sont accessibles avec la `.behaviors` propriété. Les instances peuvent être activées et désactivées et affichées ou masquées. Mais une fois les instances créées, elles ne peuvent plus être supprimées.
