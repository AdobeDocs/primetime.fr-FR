---
seo-title: La critique des politiques
title: La critique des politiques
uuid: 076f386e-ba58-4507-92a3-a190126c881e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# La critique des politiques{#policy-criticality}

Si de nouvelles règles d’utilisation sont utilisées dans les stratégies et que ces stratégies sont utilisées dans le contenu compressé pour les anciens serveurs de licences (qui ne comprennent pas les nouvelles règles d’utilisation), vous pouvez spécifier le comportement des anciens serveurs de licences. Par défaut, l’aspect critique de la stratégie est &quot;true&quot;, ce qui signifie que le serveur de licences doit comprendre toutes les parties de la stratégie pour générer une licence à l’aide de la stratégie. Si la valeur &quot;false&quot; est affectée à la criticité de la stratégie, un ancien serveur de licences peut ignorer certaines parties de la stratégie qu’il ne comprend pas et les licences générées par le serveur ne contiendront pas les nouvelles règles d’utilisation.

Les serveurs Adobe Access utilisant la version 2.0.2 du kit SDK et les versions ultérieures respecteront le paramètre de valeur de la stratégie.
