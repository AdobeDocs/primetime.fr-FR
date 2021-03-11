---
description: Pour utiliser le SDK Browser TVSDK, vous devez créer et configurer un lecteur de base. Pour lire du contenu vidéo, vous pouvez créer un lecteur de base de deux manières à l’aide du SDK du navigateur ou de la structure de l’interface utilisateur.
title: Lecteur de base
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---


# Aperçu {#basic-player-overview}

Pour utiliser le SDK Browser TVSDK, vous devez créer et configurer un lecteur de base. Pour lire du contenu vidéo, vous pouvez créer un lecteur de base de deux manières : à l’aide du navigateur TVSDK ou de l’interface utilisateur Framework.

## Utilisation du navigateur TVSDK {#section_4D1C6D4B3A3447DFA2AA0229E140E2D9}

Utilisez les API fournies avec le SDK du navigateur directement pour coder votre lecteur vidéo. Le SDK fournit des infrastructures et des utilitaires, ainsi qu’un lecteur de référence à partir duquel travailler.

>[!TIP]
>
>Pour voir cela fonctionner dans un lecteur de référence, ne spécifiez aucun attribut avec `videoDiv`.

## Utilisation de la structure de l’interface utilisateur {#section_AE02384CFEF64A448C108232AB62A9FF}

Ce module est utilisé pour créer des instances du lecteur, où chaque instance est liée à un élément DOM (document object model) fourni par l’appelant. En plus d’avoir une instance du navigateur TVSDK, chaque instance du lecteur héberge un certain nombre de contrôles qui constituent l’interface utilisateur du lecteur.

La mise en oeuvre de chaque contrôle comporte deux aspects :

* Un `HTMLElement`, qui est la représentation visuelle du composant à l’écran.
* Un `Behavior`, qui gère le `HTMLElement` et fournit une API pour les interactions.

Les détails relatifs à ces contrôles sont fournis à `VideoPlayer` en utilisant un objet de configuration, qui est transmis au lecteur lors de son instanciation. Par défaut, chaque composant forme une hiérarchie d’objets, l’élément étant fourni à l’instance du lecteur à la racine de l’arborescence. Au fur et à mesure de sa création, chaque composant est ajouté au DOM à l’emplacement approprié.

Chaque composant a un nom, qui est sa clé dans l&#39;objet de configuration lorsque l&#39;objet est enregistré. La classe CSS de l’élément DOM sous-jacent est constituée en tant que préfixe `vp-` ajouté au nom du composant.

Les composants peuvent être étendus ou remplacés, leur configuration peut être modifiée et les propriétés initiales définies. Cela vous permet de mieux contrôler les propriétés de l’API, le nom de classe CSS et, éventuellement, certains aspects de l’implémentation du composant. Ces options peuvent être utilisées pour personnaliser les fonctionnalités et autoriser plusieurs instances d’un composant qui peuvent être définies ou configurées individuellement.

Toutes les instances de composant sont accessibles avec la propriété `.behaviors`. Les instances peuvent être activées et désactivées et affichées ou masquées. Mais une fois les instances créées, elles ne peuvent plus être supprimées.
